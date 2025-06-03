# CESNET Anomaly Detection (SARIMA-Based)

This project applies forecasting-based anomaly detection on network traffic using the CESNET-TimeSeries24 dataset. A SARIMA model is used to predict normal flow behavior and detect deviations as potential anomalies.

## Objective

Detect anomalies such as DDoS attacks and outages by forecasting normal traffic and identifying significant residual errors.

## Reference Paper
- **Title**: CESNET-TimeSeries24: A Time Series Dataset for Network Anomaly Detection
- **Authors**: Josef Koumpe, Václav Bartoš, et al.
- **DOI**: 10.1038/s41597-025-04603-x
- **PDF**: [View Paper on Nature Scientific Data
](https://www.nature.com/articles/s41597-025-04603-x)
## Dataset Overview

- **Source**: [CESNET-TimeSeries24](https://zenodo.org/records/13382427)
- **Subset Used**: IP address `103.csv`
- **Metric**: `n_flows` (number of flows per hour)
- **Time Range**: Oct 2023 – July 2024
- **Granularity**: 1-hour aggregated

## Tools Used

- `Python`, `pandas`, `numpy`, `matplotlib`
- `statsmodels` (SARIMA modeling)
- `scikit-learn` (evaluation metrics)

## Forecasting Setup

- **Model**: `SARIMA(1,0,0)(0,1,0,168)`
- **Forecast Types**:
  - One-shot 7-day forecast
  - One-shot 2-day forecast
  - Rolling 2-day forecast
- **Evaluation Metrics**: RMSE, MAE, SMAPE, R²


## Anomaly Detection

- Based on residuals (actual – forecast)
- Methods:
  - 3-Sigma
  - MAD (Median Absolute Deviation)
  - Quantile (1st and 99th percentiles)
- **Evaluation Metrics**: Precision, Recall, F1-Score


## Notable Analysis

- Known anomaly (probe outage): May 21 – June 4, 2024
- Best detection performance achieved using MAD method (F1 = 0.27)

  
## How to Run
- **Clone the Repository**:
- git clone https://github.com/tanjilaahmed2/cesnet-anomaly-detection.git
- cd cesnet-anomaly-detection
- jupyter notebook
- Run CESNET_Anomaly_Detection.ipynb
  
The notebook will:

- Load CESNET flow data for a specific IP (103)
- Train SARIMA model on 31-day windows
- Perform 7-day and 2-day forecasts
- Detect anomalies using residual-based methods (3-Sigma, MAD, Quantile)
- Generate and save plots 
