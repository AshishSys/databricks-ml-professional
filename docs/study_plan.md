# Study Plan

## Purpose
A focused, timeboxed study plan to prepare for the Databricks Certified Machine Learning Professional exam and to complete the hands‑on labs and notebooks in this repository.

## Duration and cadence
- **Total duration:** 6 weeks (adjustable).  
- **Weekly cadence:** 3–5 focused sessions per week; 1–2 hours per session.  
- **Milestones:** end of Week 2 (feature engineering), Week 4 (training and registry), Week 6 (serving and monitoring).

## Weekly breakdown
### Week 1 Setup and Fundamentals
- Read repository README and run environment setup notebook.
- Configure Databricks workspace, create a cluster with ML runtime.
- Create Databricks secret scope and add `DATABRICKS_HOST` and `DATABRICKS_TOKEN`.

### Week 2 Feature Engineering and Point in Time
- Complete `notebooks/01-Feature-Engineering-and-Point-in-Time.ipynb`.
- Run Lab 1 `labs/lab1_point_in_time.md` end-to-end.
- Validate point‑in‑time joins and materialized feature table.

### Week 3 Training and MLflow Tracking
- Complete `notebooks/02-Training-MLflow-Tracking-Model-Registry.ipynb`.
- Run Lab 2 `labs/lab2_mlflow_registry.md`.
- Practice logging experiments, registering models, and adding signatures.

### Week 4 Model Registry and Promotion Workflows
- Implement model versioning and stage transitions.
- Simulate CI promotion and smoke tests.
- Add automated checks for model metadata and metrics.

### Week 5 Serving and Canary Deployments
- Complete `notebooks/03-Serving-and-Monitoring.ipynb`.
- Run Lab 3 `labs/lab3_serving_canary.md`.
- Practice canary traffic simulation and rollback logic.

### Week 6 Monitoring Retraining and Final Review
- Run Lab 4 `labs/lab4_monitoring_retraining.md`.
- Implement drift checks and trigger retraining job.
- Review cheat sheet and practice questions in `notebooks/99-CheatSheet-40-Practice-Questions.ipynb`.
- Do a full mock exam walkthrough and fix gaps.

## Study tips
- **Hands‑on first:** run notebooks on Databricks Repos for two‑way sync.  
- **Log everything:** use MLflow for experiments and store metrics in Delta for reproducibility.  
- **Small iterations:** commit frequently and use branches for experiments.  
- **Simulate production:** test model promotion, serving, and rollback in a controlled environment.  
- **Use secrets:** never hardcode tokens; use Databricks secret scopes and GitHub Actions secrets.

## Deliverables by end of study plan
- Delta feature tables and training set.  
- Registered model with at least one staged version.  
- A serving endpoint or local serving simulation with canary test.  
- Monitoring notebooks and a retraining job trigger.  
- Completed cheat sheet notebook and lab markdowns.

## Resources
- Databricks documentation for Feature Store, MLflow, and Jobs.  
- Official exam guide and blueprint (see exam blueprint file).  
- This repository labs and notebooks for hands‑on practice.
