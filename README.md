# cesnet-anomaly-detection
In this notebook, we apply a Seasonal ARIMA (SARIMA) model to a real-world network traffic time series dataset (CESNET-TimeSeries24). Our goal is to forecast future traffic and identify anomalies where actual traffic significantly deviates from the forecast.

# CESNET Anomaly Detection (SARIMA)

This repository contains a Jupyter Notebook implementation of forecasting-based anomaly detection on CESNET-TimeSeries24 data using SARIMA models.

## Contents
- `CESNET_Anomaly_Detection.ipynb`: Main notebook
- `Presentation_Slides.pdf`: Final slide deck
- `anomaly_plots/`: Output plots from SARIMA forecasts and anomaly detection
- `README.md`: Project summary

## Approach
- Forecasted `n_flows` using SARIMA(1,0,0)(0,1,0,168)
- Compared 7-day and 2-day one-shot forecasts
- Detected anomalies using residual thresholding (3-sigma, MAD, Quantile)

## Results
- Lower RMSE and SMAPE in 2-day forecasts
- MAD was more sensitive to moderate anomalies
- 3-sigma detected only major spikes

## Tools
Python, pandas, statsmodels, scikit-learn, matplotlib
