# Lab 1 Point in Time Feature Engineering

**Purpose**  
Build a point in time training set from event and label data to avoid label leakage. Materialize offline features to Delta and prepare an enriched training set suitable for model training and validation.

**Prerequisites**  
- Databricks workspace and cluster (Databricks Runtime for Machine Learning recommended).  
- Repo synced to Databricks Repos.  
- Secret scope `lab-secrets` with `DATABRICKS_HOST` and `DATABRICKS_TOKEN` (optional for REST examples).  
- Notebook `01-Feature-Engineering-and-Point-in-Time.ipynb` available in `notebooks/`.

---

## Overview

1. Generate synthetic events and labels or load your dataset.  
2. Persist events and labels as Delta tables.  
3. Implement a point in time join to assemble training rows without leakage.  
4. Materialize aggregated features to a Delta feature table.  
5. Enrich training rows with materialized features.  
6. Run validation tests to assert no leakage and expected row counts.  
7. Notes on production considerations and next steps.

---

## 1 Generate sample data

**Goal** Create two Delta tables: `demo.events` and `demo.labels`. Use the notebook cell below to generate synthetic data for the lab.

```python
# Notebook cell: create synthetic events and labels
from pyspark.sql import SparkSession
from pyspark.sql import functions as F
from pyspark.sql.types import StructType, StructField, IntegerType, TimestampType, DoubleType
import datetime, random

spark = SparkSession.builder.getOrCreate()

NUM_ENTITIES = 50
DAYS = 30
BASE = datetime.datetime(2023, 1, 1)

# Events: entity_id, feature_ts, f1, f2
events = []
for entity in range(1, NUM_ENTITIES + 1):
    for day in range(DAYS):
        ts = BASE + datetime.timedelta(days=day, hours=random.randint(0, 23))
        events.append((entity, ts, float(random.random() * 10), float(random.random() * 5)))

events_schema = StructType([
    StructField("entity_id", IntegerType(), False),
    StructField("feature_ts", TimestampType(), False),
    StructField("f1", DoubleType(), False),
    StructField("f2", DoubleType(), False)
])
events_df = spark.createDataFrame(events, schema=events_schema)
events_df = events_df.repartition("entity_id")
events_df.write.format("delta").mode("overwrite").saveAsTable("demo.events")

# Labels: entity_id, label_ts, label
labels = []
label_days = [15, 20, 25]
for entity in range(1, NUM_ENTITIES + 1):
    for day in label_days:
        ts = BASE + datetime.timedelta(days=day, hours=12)
        labels.append((entity, ts, float(random.choice([0, 1]))))

labels_schema = StructType([
    StructField("entity_id", IntegerType(), False),
    StructField("label_ts", TimestampType(), False),
    StructField("label", DoubleType(), False)
])
labels_df = spark.createDataFrame(labels, schema=labels_schema)
labels_df.write.format("delta").mode("overwrite").saveAsTable("demo.labels")

print("Wrote demo.events rows:", events_df.count())
print("Wrote demo.labels rows:", labels_df.count())
