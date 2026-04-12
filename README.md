# Behavioral Drift Detection in Distributed Systems

Detecting gradual behavioral drift in large-scale distributed systems 
using Google Borg cluster traces and PySpark.

## Overview
Traditional monitoring relies on fixed thresholds — effective for sudden 
failures but blind to gradual behavioral shifts. This project detects 
distributional drift in system metrics over time without hardcoded thresholds.

## Dataset
Google Borg Cluster Traces — 349,000+ real production events from Google's 
internal cluster manager, containing CPU usage, memory allocation, scheduling 
events, and failure indicators.

Dataset not included due to size. Available at: 
https://github.com/google/cluster-data

## Tech Stack
Python, PySpark, scipy, pandas, matplotlib, seaborn

## Approach
1. Load and parse raw telemetry using PySpark (nested struct columns, multiline CSV)
2. Extract CPU usage, memory allocation, and scheduling metrics
3. Partition data into time windows using distributed Spark operations
4. Detect drift by comparing distributions across windows using statistical methods
5. Simulate real-time alerting by processing windows sequentially

## Status
🚧 Work in Progress

## Authors
Surya K
