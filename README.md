# Behavioral Drift Detection

A machine learning project for detecting changes in resource usage patterns and classifying failures using Google Borg cluster telemetry data.

## Overview

This project uses PySpark to process cluster telemetry, statistical tests to identify behavioral drift, and a Random Forest classifier to identify failure-related patterns.

## Tech Stack

- **Python, PySpark** – Data processing and ETL
- **Pandas, NumPy** – Data manipulation and feature engineering
- **SciPy** – Statistical drift detection
- **Scikit-learn** – Machine learning and evaluation
- **Matplotlib, Seaborn** – Data visualization

## Implementation

### 1. Data Preprocessing

- Processed 405,894 Google Borg cluster-trace records using PySpark.
- Cleaned missing and invalid values, retaining 349,442 records.
- Extracted CPU and memory usage features.

### 2. Behavioral Drift Detection

- Divided the dataset into 10 chronological, approximately equal-count windows.
- Applied the Kolmogorov–Smirnov (KS) test and Population Stability Index (PSI) to detect changes in resource usage distributions.
- Analyzed CPU and memory usage patterns across windows.

### 3. Failure Classification

- Trained a Random Forest classifier using resource usage and engineered features.
- Evaluated classification performance using ROC-AUC, average precision, and other classification metrics.

## Results

| Metric | Result |
|---|---|
| Raw Records | 405,894 |
| Records After Cleaning | 349,442 |
| Drift Analysis Windows | 10 |
| ROC-AUC | 0.873 |
| Average Precision | 0.816 |
| Accuracy | 91% |

*Results are from the final notebook's saved experimental outputs.*

## How to Run

1. Clone the repository.
2. Install the required Python libraries.
3. Download the required Google Borg cluster-trace dataset and configure its path in the notebook.
4. Open and execute `behavioral_drift_detection_final.ipynb`.

## Limitations

- Drift detection identifies distribution changes, not necessarily system failures.
- The classifier identifies failure-related patterns but does not establish advance failure prediction.
- The current experiment has preprocessing and temporal-validation limitations.

## Conclusion

The project demonstrates a workflow combining scalable telemetry preprocessing, statistical drift analysis, and machine learning-based failure classification.
