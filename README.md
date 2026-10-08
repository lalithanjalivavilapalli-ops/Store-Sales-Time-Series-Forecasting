# Store Sales – Time Series Forecasting (Version 1)

**Foundations of Data Science Project** · Basic baseline using the Kaggle *Store Sales – Time Series Forecasting* dataset (Corporación Favorita, Ecuador).

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/YOUR-USERNAME/YOUR-REPO-NAME/blob/main/Store_Sales_Forecasting_V1.ipynb)

## Problem Statement
To develop a time series forecasting model for predicting future product sales across individual retail stores using historical sales data. The model aims to identify temporal patterns, trends, and seasonal variations while incorporating factors such as store characteristics, product families, promotions, holidays, events, transactions, and oil prices to improve the accuracy of sales predictions.

> **Version 1** is intentionally simple. It is a working baseline that will be improved in Version 2.

## What this notebook does
1. Understands the dataset (7 CSV files, target variable `sales`)
2. Loads and cleans the data (dates, missing values, duplicates)
3. Exploratory Data Analysis with 7 graphs and explanations
4. Basic feature engineering (`year`, `month`, `day`, `day_of_week`, `store_nbr`, `family_code`, `onpromotion`)
5. Chronological train / validation split
6. Random Forest Regressor
7. Evaluation with RMSLE, MAE and RMSE
8. Actual vs predicted graphs and a forecast over time
9. Findings (dataset, model, business)
10. Limitations and ideas for Version 2

## Results (validation period: 2017-07-31 to 2017-08-15)

| Model | RMSLE | MAE | RMSE |
|---|---|---|---|
| Baseline (always predict average sales) | 3.5534 | 639.77 | 1248.41 |
| **Random Forest (Version 1)** | **0.4396** | **77.92** | **290.81** |

These scores were measured on my own 16-day validation set, not on the Kaggle leaderboard.

## Key observations
- Average daily sales grew from about 386,000 (2013) to about 856,000 (2017).
- December is the strongest month; Saturday and Sunday are the busiest days.
- GROCERY I, BEVERAGES and PRODUCE make up 63.6% of all sales.
- Sales and transactions are strongly correlated (0.84).

## How to run

### Option 1: Google Colab (easiest)
1. Click the **Open In Colab** badge above.
2. Download the dataset from Kaggle (link below) and upload the ZIP file in the Colab **Files** panel.
3. If the ZIP name is different, change `ZIP_PATH` in the 3rd code cell.
4. Click **Runtime → Run all** (training takes about 2–3 minutes).

### Option 2: Run locally
```bash
pip install -r requirements.txt
jupyter notebook Store_Sales_Forecasting_V1.ipynb
```
Place `store-sales-time-series-forecasting.zip` in the same folder as the notebook.

## Dataset
The dataset is **not included** in this repository because it is too large (`train.csv` is about 116 MB).
Download it from Kaggle: https://www.kaggle.com/competitions/store-sales-time-series-forecasting/data

## Limitations of Version 1
Only 7 features, a single untuned Random Forest, no lag features, no rolling averages, limited use of holidays/events/oil/store information, training on 2016 onwards only, and a short 16-day validation window.

## Planned for Version 2
Lag features, rolling averages, holidays and events, store information, oil prices, payday features, training on the full history, multiple validation windows, hyperparameter tuning and comparison with other models.

## Tools
Python, pandas, numpy, matplotlib, seaborn, scikit-learn
