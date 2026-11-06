# 🛒 Retail Sales Forecasting

A end-to-end time-series forecasting project that predicts **30 days of future retail sales** using classical statistical models and machine learning.

Compared **ARIMA**, **SARIMA**, and **XGBoost** — XGBoost achieved the best performance with **~20% WAPE**.

---

## 📊 Results

| Model | MAE | RMSE | WAPE |
|---|---|---|---|
| **XGBoost** | **3.49** | **4.61** | **20.4%** |
| SARIMA | 5.86 | 6.86 | 34.2% |
| ARIMA | 6.13 | 7.28 | 35.8% |

> WAPE (Weighted Absolute Percentage Error) is the primary metric — widely used in retail forecasting.

---

## 📁 Dataset

- **Source:** [Kaggle — Store Item Demand Forecasting Challenge](https://www.kaggle.com/competitions/demand-forecasting-kernels-only)
- **Size:** ~913,000 rows
- **Coverage:** 10 stores × 50 products × 5 years (2013–2017) of daily sales

Download `train.csv` from Kaggle and place it inside the `demand-forecasting-kernels-only/` folder.

---

## 🧠 Project Workflow

```
Data Loading → EDA → Time-Series Analysis → Feature Engineering → Modeling → Evaluation
```

### 1. Exploratory Data Analysis
- Daily / monthly sales trends
- Weekly seasonality patterns
- Sales by store and product
- Sales distribution

### 2. Time-Series Analysis
- **Seasonal Decomposition** (trend + seasonal + residual, period=7)
- **ACF & PACF plots** — to identify ARIMA parameters
- **ADF Stationarity Test** — required before fitting ARIMA

### 3. Feature Engineering (for XGBoost)
| Feature Type | Features |
|---|---|
| Lag features | Sales from 1, 7, 14, 28 days ago |
| Rolling statistics | 7/14/28-day rolling mean, 7-day rolling std |
| Calendar features | Day of week, month, day, week of year, is_weekend |

> ✅ Rolling features are computed on `shift(1)` to prevent data leakage.

### 4. Models
- **ARIMA(1,1,1)** — classical time-series baseline
- **SARIMA(1,1,1)(1,1,1,7)** — adds weekly seasonal component
- **XGBoost** — gradient boosting with engineered features, using a **walk-forward prediction loop**

### 5. Evaluation
Metrics: **MAE**, **RMSE**, **WAPE**

---

## 🗂️ Project Structure

```
retail-sales-forecasting/
│
├── demand-forecasting-kernels-only/
│   ├── train.csv               # Main dataset (download from Kaggle)
│   └── test.csv
│
├── retail_sales_forecasting.ipynb  # Main notebook
└── README.md
```

---

## ⚙️ Setup & Run

### 1. Clone the repository
```bash
git clone https://github.com/prashanth2808/retail-sales-forecasting.git
cd retail-sales-forecasting
```

### 2. Install dependencies
```bash
pip install pandas numpy matplotlib seaborn scikit-learn statsmodels xgboost
```

### 3. Download the dataset
Get `train.csv` from [Kaggle](https://www.kaggle.com/competitions/demand-forecasting-kernels-only/data) and place it in `demand-forecasting-kernels-only/`.

### 4. Run the notebook
Open `retail_sales_forecasting.ipynb` in Jupyter or VS Code and run all cells.

---

## 🛠️ Tech Stack

![Python](https://img.shields.io/badge/Python-3.10+-blue)
![XGBoost](https://img.shields.io/badge/XGBoost-gradient_boosting-orange)
![Statsmodels](https://img.shields.io/badge/Statsmodels-ARIMA%2FSARIMA-green)
![Pandas](https://img.shields.io/badge/Pandas-data_processing-lightblue)
![Matplotlib](https://img.shields.io/badge/Matplotlib-visualization-red)

---

## 📌 Key Concepts Demonstrated

- Time-series feature engineering with lag & rolling features
- Data leakage prevention in sequential data
- Walk-forward forecasting loop for ML models
- Statistical tests: ADF, ACF, PACF
- Model comparison with retail-specific metrics

---

## 👤 Author

**Prashanth** — [GitHub](https://github.com/prashanth2808)
