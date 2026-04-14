# Forecasting Canadian Import Volume for Selected Commodity Groups

## Overview
This project forecasts monthly Canadian import volume indexes for three selected commodity groups using Statistics Canada data:

- Agriculture
- Clothing and Footwear
- Furniture and Fixtures

The study compares forecasting performance at two horizons:

- 3-month ahead
- 12-month ahead

It also examines whether adding the import price index improves forecast accuracy.

## Research Questions
1. Which forecasting model produces the lowest forecasting error for each selected commodity group at the 3-month horizon?
2. Which forecasting model produces the lowest forecasting error for each selected commodity group at the 12-month horizon?
3. Does adding the import price index improve forecast accuracy compared with using only past volume-based information?

## Dataset
**Source:** Statistics Canada  
**Dataset:** International merchandise trade, by commodity, price and volume indexes, monthly

### Final filtered dataset
The modeling dataset includes:

- Imports only
- Seasonally adjusted observations only
- Volume index as the target variable
- Price index as an optional predictor
- Three selected commodity groups only

### Selected groups
- Furniture and Fixtures
- Clothing and Footwear
- Agriculture

**Note:** “Agriculture” is a simplified project label for the selected Statistics Canada series *Fresh fruit, nuts and vegetables, and pulse crops*. It does not represent the full agricultural sector.

### Dataset summary
- Date range: January 2017 to November 2025
- Total rows: 321
- Groups: 3
- Observations per group: 107

Validation checks confirmed:
- no missing values in the final cleaned dataset
- no duplicate month-group rows
- no missing months within each group

## Models Compared
- Naïve
- Seasonal Naïve
- Linear Regression
- Random Forest
- SARIMA

For Linear Regression and Random Forest, both **with-price** and **without-price** versions were tested.

## Evaluation Metrics
- RMSE
- MAE

RMSE was used as the main model-selection metric.

## Final Best Models

### 3-month horizon
- Agriculture: **SARIMA**
- Clothing and Footwear: **Naïve**
- Furniture and Fixtures: **Linear Regression with price**

### 12-month horizon
- Agriculture: **Random Forest without price**
- Clothing and Footwear: **SARIMA**
- Furniture and Fixtures: **Naïve**

## Key Findings
- Forecasting performance depended on both the commodity group and the forecast horizon.
- No single model dominated all cases.
- Naïve remained a strong benchmark.
- Price information helped some groups, but not all.
- Longer-horizon forecasting was generally more difficult.

## Repository Structure
```text
Capstone/
├── data/
├── notebooks/
├── README.md

**Project Overview**

This project develops and evaluates time-series forecasting models to predict monthly import volume indexes for selected Canadian commodity groups using Statistics Canada data (2017–2025).

The study focuses on three representative commodity groups:

1. Furniture and Fixtures

2. Clothing and Footwear

3. Agriculture Products

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
