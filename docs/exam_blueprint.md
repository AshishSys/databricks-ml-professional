# Exam Blueprint

## Purpose
Concise mapping of exam domains to repository content and suggested practice tasks.

## Exam domains and weightings
- **Feature Engineering and Data Preparation** 25%  
- **Model Training and MLflow Tracking** 25%  
- **Model Registry and Deployment** 20%  
- **Serving and Monitoring** 20%  
- **Operationalization and Governance** 10%

## Mapping to repository
- **Feature Engineering and Data Preparation**
  - Primary: `notebooks/01-Feature-Engineering-and-Point-in-Time.ipynb`, `labs/lab1_point_in_time.md`
  - Practice: implement point‑in‑time joins, materialize Delta feature tables, validate no leakage.

- **Model Training and MLflow Tracking**
  - Primary: `notebooks/02-Training-MLflow-Tracking-Model-Registry.ipynb`, `labs/lab2_mlflow_registry.md`
  - Practice: log params/metrics/artifacts, reproduce runs, infer model signature.

- **Model Registry and Deployment**
  - Primary: `labs/lab2_mlflow_registry.md`, `labs/lab3_serving_canary.md`
  - Practice: register models, stage transitions, simulate CI promotion, create rollback plan.

- **Serving and Monitoring**
  - Primary: `notebooks/03-Serving-and-Monitoring.ipynb`, `labs/lab3_serving_canary.md`, `labs/lab4_monitoring_retraining.md`
  - Practice: deploy model endpoints, run canary tests, implement drift detection and alerts.

- **Operationalization and Governance**
  - Primary: `docs/study_plan.md`, `labs/lab4_monitoring_retraining.md`
  - Practice: secrets management, job scheduling, reproducibility, access controls.

## Practical tasks to master each domain
- Build a reproducible training pipeline that logs to MLflow.  
- Register a model and write a script to transition stages via API.  
- Create a Delta feature table and demonstrate point‑in‑time joins.  
- Deploy a model endpoint and run a canary traffic test with rollback.  
- Implement a drift detection notebook and trigger a retrain job.

## Exam day checklist
- Confirm Databricks cluster runtime and libraries.  
- Ensure MLflow tracking server and Model Registry are accessible.  
- Have sample datasets and notebooks ready to run.  
- Know how to access secrets and tokens securely.  
- Timebox tasks and focus on reproducible, auditable steps.

## Notes
- Use this blueprint to prioritize study time according to domain weightings.  
- Keep the repository updated with any additional practice scripts or notes.
