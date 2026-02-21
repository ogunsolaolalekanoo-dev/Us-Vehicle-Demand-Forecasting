US Vehicle Demand Forecasting & Structural Shift Analysis (1990–2016)
Overview

This project develops a multi-segment forecasting system for U.S. vehicle demand using BEA seasonally adjusted monthly sales data (1990–2016).

The system compares classical econometric models (SARIMA) with feature-engineered machine learning models to evaluate:

Forecast accuracy

Structural demand shifts

Economic shock sensitivity

Segment stability across time

The objective is not only prediction accuracy, but understanding demand dynamics and model robustness under regime change.

Business Questions

Did the 2008 financial crisis permanently alter U.S. vehicle demand structure?

Are light trucks structurally replacing traditional autos?

Which demand segments are most forecastable?

Do classical time-series models perform competitively against engineered ML models?

Data

Source: U.S. Bureau of Economic Analysis (BEA)
Frequency: Monthly
Period: 1990–2016
Series Modeled:

Domestic Autos

Foreign Autos

Domestic Light Trucks

Foreign Light Trucks

All modeling used seasonally adjusted values.

Methodology
1. Econometric Baseline — SARIMA

Each segment was modeled using SARIMA (1,1,1)(1,1,1,12) to capture:

Autoregressive behavior

Differencing for non-stationarity

Annual seasonality

Stationarity was tested using ADF tests prior to modeling.

2. Feature-Engineered Machine Learning

A structured time-series feature framework was built including:

Lag features (1, 3, 6, 12 months)

Rolling means (3, 6, 12 months)

Year-over-year growth

Month-of-year seasonality

Trend index

Models evaluated:

Linear Regression

Random Forest

XGBoost

Target leakage from aggregate totals and shares was identified and removed before final training.

3. Evaluation Framework

Two evaluation strategies were used:

Hold-out test (final 24 months)

Rolling TimeSeries cross-validation

Metrics:

MAE

RMSE

MAPE
