**US Vehicle Demand Forecasting & Structural Shift Analysis (1990–2016)**
Overview

This project develops a multi-segment forecasting system for U.S. vehicle demand using BEA seasonally adjusted monthly sales data (1990–2016).

The system compares classical econometric models (SARIMA) with feature-engineered machine learning models to evaluate:

Forecast accuracy

Structural demand shifts

Economic shock sensitivity

Segment stability across time

The objective is not only prediction accuracy, but understanding demand dynamics and model robustness under regime change.

**Business Questions**

Did the 2008 financial crisis permanently alter U.S. vehicle demand structure?

Are light trucks structurally replacing traditional autos?

Which demand segments are most forecastable?

Do classical time-series models perform competitively against engineered ML models?

**Data**

Source: U.S. Bureau of Economic Analysis (BEA)
Frequency: Monthly
Period: 1990–2016
**Series Modeled:**

Domestic Autos

Foreign Autos

Domestic Light Trucks

Foreign Light Trucks

All modeling used seasonally adjusted values.

**Methodology**
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
**Results**
| Segment        | SARIMA | Linear Regression |
| -------------- | ------ | ----------------- |
| Auto Domestic  | 24.70  | **10.15**         |
| Auto Foreign   | 24.64  | **5.27**          |
| Truck Domestic | 45.96  | **11.16**         |
| Truck Foreign  | 35.02  | **5.61**          |
Feature-engineered linear regression reduced forecast error by 59–84% relative to SARIMA.
**Cross-Validation Stability**
| Segment        | CV_RMSE |
| -------------- | ------- |
| Auto Domestic  | 26.98   |
| Auto Foreign   | 8.66    |
| Truck Domestic | 31.27   |
| Truck Foreign  | 4.99    |


Foreign truck demand is highly stable across time.

Domestic segments show regime instability, particularly around economic shocks.

Post-2012 demand exhibits stronger linear stability.

**Structural Insights**

Light trucks structurally overtook autos following the 2008 financial crisis.

Domestic vehicle demand shows greater regime sensitivity than foreign segments.

Demand dynamics are largely linear autoregressive with strong annual seasonality.

Nonlinear tree-based models did not outperform linear regression once leakage was removed.

**Key Takeaways**

Feature engineering can outperform classical SARIMA by a significant margin.

Model simplicity should not be underestimated — linear regression dominated ensemble models.

Cross-validation revealed structural instability masked by single hold-out splits.

Forecasting systems must be evaluated under multiple temporal regimes.

**Repository Structure**
us-vehicle-demand-forecasting/
│
├── notebooks/
├── data/
├── reports/
└── README.md

**Strategic Recommendations**

Treat Light Trucks as the Structural Growth Segment

Finding:

Light trucks overtook autos after 2008.

Post-2008 averages show trucks remain elevated relative to autos.

Foreign truck demand is highly stable (low CV_RMSE).

Recommendation:

OEMs and policy analysts should treat light trucks as a structurally dominant demand category rather than a cyclical anomaly. Forecasting, capacity planning, and capital allocation models should prioritize truck demand dynamics over legacy auto assumptions.

**Domestic Segments Require Regime-Aware Forecasting**

Finding:

Domestic auto and truck segments show high cross-validation instability.

RMSE varies significantly across time windows.

Indicates sensitivity to macro shocks.

Recommendation:

Domestic vehicle demand models should incorporate macroeconomic indicators (e.g., unemployment, fuel prices, interest rates) and structural break detection mechanisms to improve robustness under economic stress.

**Use Feature-Engineered ML Over Classical SARIMA**

Finding:

Linear regression reduced RMSE by 59–84% vs SARIMA.

Tree models did not outperform linear models.

Demand dynamics are largely linear autoregressive.

Recommendation:

Production forecasting systems for mature demand series should begin with structured feature engineering and linear autoregressive ML models before deploying complex ensemble methods.

**Monitor Segment-Specific Stability for Risk Management**

Finding:

Foreign truck demand is highly stable.

Domestic segments are shock-sensitive.

Recommendation:

Risk-adjusted planning scenarios should weight domestic demand forecasts with wider confidence intervals, while foreign truck forecasts can be treated as lower-variance projections.

Business interpretation of macro demand dynamics

It is designed to reflect real-world forecasting system development rather than isolated modeling exercises.
