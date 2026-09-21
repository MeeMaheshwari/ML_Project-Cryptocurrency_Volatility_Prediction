# ML_Project-Cryptocurrency_Volatility_Prediction
End-to-end Machine Learning project for predicting 7-day cryptocurrency volatility using historical OHLCV and market-cap data, with data preprocessing, EDA, feature engineering, Random Forest Regression, model evaluation, and Streamlit deployment.
---
# 📊 Cryptocurrency Volatility Prediction

**End-to-End Machine Learning Project**
*Predicting 7-day cryptocurrency volatility using historical OHLCV and market data*

![Python](https://img.shields.io/badge/Python-3.x-blue?style=flat-square\&logo=python)
![Scikit-learn](https://img.shields.io/badge/Scikit--learn-Machine%20Learning-orange?style=flat-square\&logo=scikit-learn)
![Streamlit](https://img.shields.io/badge/Streamlit-App-red?style=flat-square\&logo=streamlit)
![Pandas](https://img.shields.io/badge/Pandas-Data%20Processing-yellow?style=flat-square\&logo=pandas)

---

## 👩‍💻 Project Created By

**Maheshwari Shinde**

**Course:** Data Analytics
**Platform:** PW Skills

---

## 📌 Project Overview

Cryptocurrency markets are highly volatile, with rapid price movements that can create significant risks for traders and investors.

This project develops an **end-to-end Machine Learning pipeline** to predict **7-day cryptocurrency volatility** using historical OHLC (Open, High, Low, Close), Volume, and Market Capitalization data.

The project follows a complete Machine Learning workflow, including:

* Data Cleaning and Preprocessing
* Exploratory Data Analysis (EDA)
* Feature Engineering
* Feature Scaling
* Machine Learning Model Training
* Model Evaluation
* Model Saving
* Streamlit Deployment
* Project Documentation

---

## 🎯 Project Objective

The main objective of this project is to build a Machine Learning model that predicts cryptocurrency volatility based on historical market data.

The project aims to understand cryptocurrency price behaviour and create a complete pipeline from raw historical data to volatility prediction.

---

## 📊 Dataset Information

The dataset contains historical daily cryptocurrency market information.

### Dataset Columns

```text
date
symbol
open
high
low
close
volume
market_cap
```

The EDA report contains approximately **18,000 daily records**.

---

## 🧹 Data Preprocessing

The data preprocessing stage performs the following operations:

* Standardizes column names
* Removes unnecessary columns
* Converts the `date` column into datetime format
* Removes records with invalid dates
* Sorts data by cryptocurrency and date
* Handles missing values using forward-fill and backward-fill

The cleaned dataset is then passed to the feature engineering stage.

---

## ⚙️ Feature Engineering

The project creates additional features to capture cryptocurrency market behaviour.

### 1. Daily Return

```text
daily_return = (close - open) / open
```

### 2. 7-Day Rolling Volatility

```text
vol_7d = 7-day rolling standard deviation of daily_return
```

### 3. Liquidity Ratio

```text
liquidity_ratio = volume / market_cap
```

### 4. 7-Day Moving Average

```text
ma7 = 7-day moving average of close price
```

### 5. 30-Day Moving Average

```text
ma30 = 30-day moving average of close price
```

---

## 🔎 Exploratory Data Analysis

The EDA stage analyzes the structure and behaviour of the cryptocurrency dataset.

The analysis includes:

* Dataset overview
* Data quality analysis
* Missing-value analysis
* Price distributions
* Trading volume distributions
* Market capitalization distributions
* Correlation analysis
* Volatility analysis
* Price trends
* Volatility outliers

### Key Observations

* Open, High, Low and Close prices are highly correlated.
* Volume and Market Capitalization show right-skewed distributions.
* Smaller cryptocurrencies show higher volatility in the analysed data.
* Liquidity ratio shows an inverse relationship with volatility.

---

## 🤖 Machine Learning Model

The project uses a:

### Random Forest Regressor

The Random Forest model is used to predict the numerical value of cryptocurrency volatility.

### Model Configuration

```text
Algorithm: RandomForestRegressor
Number of Estimators: 200
Random State: 42
```

### Features Used

```text
open
high
low
close
volume
market_cap
daily_return
liquidity_ratio
ma7
ma30
```

---

## 📏 Model Evaluation

The model is evaluated using standard regression metrics:

* **MAE** — Mean Absolute Error
* **RMSE** — Root Mean Square Error
* **R²** — Coefficient of Determination

### Model Results

| Metric |    Value |
| ------ | -------: |
| MAE    | 0.035549 |
| RMSE   | 0.142268 |
| R²     |  -7.5304 |

The reported results represent the current model evaluation from the project.

The negative R² indicates that the current model and validation approach do not explain the test-set volatility sufficiently well. This provides an opportunity for further feature engineering, validation improvements, and model optimization.

---

## 🏗️ Pipeline Architecture

```text
                    Cryptocurrency Dataset
                             │
                             ▼
                  ┌─────────────────────┐
                  │ Data Preprocessing  │
                  │                     │
                  │ Cleaning            │
                  │ Missing Values      │
                  │ Date Processing     │
                  └──────────┬──────────┘
                             │
                             ▼
                  ┌─────────────────────┐
                  │ Feature Engineering │
                  │                     │
                  │ Daily Return        │
                  │ 7-Day Volatility    │
                  │ Liquidity Ratio     │
                  │ MA7 / MA30          │
                  └──────────┬──────────┘
                             │
                             ▼
                  ┌─────────────────────┐
                  │ Feature Scaling     │
                  │ StandardScaler      │
                  └──────────┬──────────┘
                             │
                             ▼
                  ┌─────────────────────┐
                  │ Random Forest       │
                  │ Regressor           │
                  └──────────┬──────────┘
                             │
                             ▼
                  ┌─────────────────────┐
                  │ Model Evaluation    │
                  │ MAE / RMSE / R²     │
                  └──────────┬──────────┘
                             │
                             ▼
                  ┌─────────────────────┐
                  │ Saved ML Model      │
                  └──────────┬──────────┘
                             │
                             ▼
                  ┌─────────────────────┐
                  │ Streamlit App       │
                  │ Volatility          │
                  │ Prediction          │
                  └─────────────────────┘
```

### Project Flow

```text
data/dataset.csv
      ↓
src/data_preprocessing.py
      ↓
src/feature_engineering.py
      ↓
src/model_training.py
      ↓
models/
      ↓
app/streamlit_app.py
```

---

## 📁 Project Structure

```text
Cryptocurrency-Volatility-Prediction-ML/
│
├── app/
│   └── streamlit_app.py
│
├── data/
│   └── dataset.csv
│
├── models/
│   ├── scaler.pkl
│   └── crypto_volatility_model.pkl
│
├── notebook/
│   └── crypto_volatility_prediction_colab.ipynb
│
├── reports/
│   ├── EDA_Report.md
│   ├── Final_Report.md
│   ├── HLD.md
│   ├── LLD.md
│   └── Pipeline.md
│
├── src/
│   ├── data_preprocessing.py
│   ├── feature_engineering.py
│   └── model_training.py
│
├── README.md
└── .gitignore
```

---

## 🚀 Streamlit Deployment

The project includes a **Streamlit application** for testing cryptocurrency volatility predictions.

The application accepts:

* Open Price
* High Price
* Low Price
* Close Price
* Trading Volume
* Market Capitalization

The application then processes the inputs using the saved scaler and Machine Learning model and generates a predicted **7-day volatility** value.

---

## 🛠️ Technologies Used

* **Python**
* **Pandas**
* **NumPy**
* **Matplotlib**
* **Seaborn**
* **Scikit-learn**
* **Random Forest Regressor**
* **Streamlit**
* **Jupyter Notebook**
* **Google Colab**
* **GitHub**

---

## 📚 Skills Demonstrated

* Data Cleaning
* Data Preprocessing
* Exploratory Data Analysis
* Data Visualization
* Feature Engineering
* Feature Scaling
* Regression
* Random Forest
* Model Evaluation
* Machine Learning Pipeline
* Model Serialization
* Streamlit Deployment
* Technical Documentation
* GitHub Project Organization

---

## 📄 Project Documentation

The repository contains the following project documentation:

### EDA Report

Contains:

* Dataset overview
* Data quality analysis
* Statistical observations
* Visual analysis
* Key findings

### HLD — High Level Design

Describes:

* System overview
* Major project components
* Architecture
* Technologies and libraries used

### LLD — Low Level Design

Describes:

* Module breakdown
* Functions
* Data flow
* Model implementation
* Storage structure

### Pipeline Architecture

Describes the flow of data from preprocessing to prediction.

### Final Report

Contains:

* Project objective
* Methodology
* Model results
* Key findings
* Conclusion
* Future improvements

---

## 🔮 Future Improvements

The project can be further improved by:

* Hyperparameter tuning
* Improved time-based validation
* Additional technical indicators
* XGBoost and other Machine Learning models
* LSTM-based time-series modelling
* Real-time cryptocurrency API integration
* Automated model retraining
* Enhanced Streamlit dashboard
* Improved future-volatility forecasting methodology

---

## 📝 Conclusion

This project demonstrates an end-to-end Machine Learning workflow for cryptocurrency volatility prediction, starting from historical market data and progressing through data preprocessing, exploratory data analysis, feature engineering, model training, evaluation, model saving, and Streamlit deployment.

The current implementation provides a complete Machine Learning project structure while identifying opportunities for further model optimization and improved forecasting performance.

---

## 👩‍💻 Author

### Maheshwari Shinde

**Aspiring Data Analyst | Python | SQL | Excel | Power BI | Tableau | Machine Learning**

---

⭐ **Thank you for visiting my project!**
