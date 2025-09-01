# Electricity Load Forecasting (Mock Project)

## Overview
This project demonstrates an **electricity load forecasting pipeline** using a **public Kaggle dataset**.  
The original production project relies on **proprietary PJM regional utility data and internal database** and cannot be shared.  
Here, a public dataset is used to reproduce the methodology, including exploratory data analysis, feature engineering, and model comparison.

⚠️ **Important Notes on Real-World Projects**
- Real pipelines involve **more complex time series handling**:
  - Irregular timestamps
  - Daylight saving adjustments
  - Multi-zone synchronization  
- **Missing value detection and repair** is more challenging in production, e.g. partial-day gaps and misaligned reports.  
- The Kaggle dataset uses **real weather data** as a proxy for forecasts.  
  In production, however, **weather forecasts differ from actual weather**, introducing additional noise and reducing accuracy.

---

## Features
- 📊 **Exploratory Data Analysis (EDA)**
  - Missing values, duplicates, timestamp completeness
  - Demand distribution histograms
  - Seasonality plots (daily and weekly patterns)

- ⚙️ **Feature Engineering**
  - Time-based features: hour-of-day, day-of-week, holidays
  - Lagged variables and rolling statistics
  - Standardization for neural networks

- 🤖 **Models**
  - Random Forest Regressor (baseline)
  - XGBoost (limited hyperparameter tuning)
  - LSTM (PyTorch) for sequence modeling

- 📈 **Evaluation**
  - Walk-forward validation with `TimeSeriesSplit`
  - RMSE as the primary error metric
  - Learning curves for model capacity
  - Predicted vs. actual demand visualization


---

## Quickstart

### 1. Install dependencies

### 2. Download dataset
- Kaggle dataset: *[Electricity Load + Weather Data]([https://www.kaggle.com/](https://www.kaggle.com/datasets/saurabhshahane/electricity-load-forecasting/data))*  
- Place CSV file under `data/` folder.

### 3. Run notebooks
- `01_eda.ipynb` → exploratory analysis  
- `02_random_forest.ipynb` → baseline model  
- `03_xgboost.ipynb` → gradient boosting model  
- `04_lstm_pytorch.ipynb` → deep learning model  

---

## Results
| Model           | MSE  | Notes                                |
|-----------------|----------------|--------------------------------------|
| Random Forest         | 1023.20           | Using Weather Data as Weather Forecast         |
| LSTM (PyTorch)  | 24117.29          | Captures sequential dependencies     |

*(Replace with your actual results if available.)*

---

## Notes
- This project demonstrates methodology on **public data**.  (https://www.kaggle.com/datasets/saurabhshahane/electricity-load-forecasting/data)
- Real-world projects must handle **more complex ETL, feature integration (e.g. weather forecasts), and operational monitoring**.  
- Forecast error from weather predictions is a key source of accuracy reduction in production.
