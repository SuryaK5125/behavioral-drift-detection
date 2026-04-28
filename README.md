# Behavioral Drift Detection in Distributed Systems

## Overview
Detects behavioral drift in Google Borg cluster telemetry using 
statistical methods with thresholds learned dynamically from early 
window behavior and not hardcoded values.

## Key Findings
- Significant memory allocation drift detected at window 10 (PSI=0.2629)
- Task failure rate nearly doubled from ~12% to ~24% in drift windows
- Random Forest achieves 0.98 ROC-AUC predicting task failures from resource metrics
- avg_memory_usage, max_cpu_usage, avg_cpu_usage are top failure predictors

## Pipeline
1. Ingest 313MB Google Borg traces (1.3M rows) via PySpark
2. Parse semi-structured CPU/memory fields using regex extraction
3. Split 349k cleaned records into 10 time-based windows
4. Apply KS test + PSI to detect distributional drift vs baseline window
5. Learn drift thresholds dynamically from warm-up windows 2-3
6. Correlate drift with task failure rates
7. Train Random Forest failure prediction model
8. Simulate real-time streaming alert pipeline

## Tech Stack
Python, PySpark, SciPy, Scikit-learn, Pandas, Matplotlib, Seaborn

## Dataset
[Google Borg Cluster Traces](https://github.com/google/cluster-data)


## Results

### Drift Detection (KS + PSI)
![Drift Detection](drift_detection_results.png)

### Drift vs Failure Rate
![Drift vs Failure](drift_vs_failure.png)

### Streaming Alert Timeline
![Streaming Alerts](streaming_drift_alerts.png)

### Failure Prediction Model
![Failure Prediction](failure_prediction.png)
