📦 Forecasting Monthly Import Volume for Selected Canadian Commodity Groups

**Project Overview**

This project develops and evaluates time-series forecasting models to predict monthly import volume indexes for selected Canadian commodity groups using Statistics Canada data (2017–2025).

The study focuses on three representative commodity groups:

Furniture and Fixtures

Clothing and Footwear

Canola (including rapeseed)

The objective is to generate accurate 3-month and 12-month ahead forecasts to support:

Short-term inventory planning

Medium-term procurement decisions

Trade policy timing and risk management

📊 **Dataset**

Source:
Statistics Canada – International merchandise trade, by commodity, price and volume indexes, monthly

Time Coverage:
January 2017 – November 2025

Frequency:
Monthly

Base Year:
2017 = 100

Unit of Analysis:
One model per commodity group

Target Variable:
Import Volume Index (Laspeyres fixed weighted)

Optional Explanatory Variable:
Import Price Index

**Research Questions**

Can forecasting models predict 12-month ahead import volume indexes with lower RMSE than naïve and seasonal-naïve baselines?

Which model (SARIMA, Linear Regression with lag features, Random Forest) achieves the best accuracy for 3-month and 12-month horizons?

Does including the import price index improve forecast accuracy compared to univariate models?

**Methodology**

1️⃣ **Data Preparation**

Filtered:

Trade = Import

Index = Volume index

Seasonally adjusted series

Converted dates to time-series format

Created lag features (1, 3, 6, 12 months)

Checked structural breaks (COVID period)

2️⃣ **Baseline Models**

Naïve forecast: last observed value

Seasonal naïve forecast: value from same month previous year

All candidate models must outperform these baselines.

3️⃣ **Candidate Models**
📌 SARIMA

Captures trend and seasonality.

📌 Linear Regression with Lag Features

Uses historical lag values and optional price index.

📌 Random Forest Regressor

Captures nonlinear patterns in time series.

4️⃣ **Validation Strategy**

Time-series split (rolling validation):

Training: 2017–2023

Testing: 2024–2025

Evaluation Metrics:

RMSE

MAE

Best model selected based on lowest RMSE.

⚠ **Structural Break Handling**

The COVID-19 period (2020–2021) represents a potential structural shock.

Approaches:

Include dummy variable

Compare pre/post COVID performance

Robustness checks excluding extreme months

📈 **Exploratory Data Analysis (EDA)**

The notebook includes:

Time plots for each commodity group

Seasonal decomposition

Autocorrelation (ACF/PACF) plots

Correlation analysis between price and volume indexes


📌 **Key Limitations**

Index-based measures (not actual import quantities)

Limited time coverage (2017–2025)

Structural shock during COVID

Possible future data revisions

Aggregated commodity groups

📊 **Expected Outcomes**

Comparative model accuracy results

3-month and 12-month forecasts per commodity

Evaluation of whether price index improves forecasting performance
