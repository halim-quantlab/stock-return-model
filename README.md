# 📊 Simple Stock Price Model — Learning-Focused Quant Project

A learning-focused mini project that applies linear regression to stock return prediction, with emphasis on feature engineering, preprocessing, and model interpretation rather than maximizing predictive accuracy.

## 🚀 Project Overview

This project was built to develop a practical understanding of the full machine learning pipeline on financial time series data.  
Instead of aiming for the best-performing predictive model, the goal is to explore how data preprocessing, feature engineering, and regression modeling behave in a realistic low signal-to-noise financial setting.

The workflow covers:

- Financial data extraction using `yfinance`
- Return-based feature construction
- Data cleaning and outlier handling
- Feature scaling and normalization
- Linear regression training using gradient descent
- Model evaluation using R² and visual diagnostics
- Comparison between baseline and feature-engineered models

---

## 🎯 Objective

The objective of this project is to answer a simple but important question:

**Can feature engineering improve a basic linear regression model for predicting next-day stock returns?**

To investigate this, I compared:

1. A **baseline model** using only a small set of raw features
2. A **feature-engineered model** using lagged returns, rolling statistics, interaction terms, and nonlinear features

---

## 🧠 Features Used

### Baseline Features
- Momentum
- Volatility
- Volume Change

### Engineered Features
- Return_lag1
- Return_lag5
- Momentum_5
- Momentum_10
- Volatility_5
- Volatility_10
- Mom_x_Vol
- Mom_x_VolChange
- Momentum_sq
- Volatility_sq

These engineered variables were designed to capture:

- temporal dependencies
- smoothing effects
- nonlinear relationships
- feature interactions

---

## 📈 Results

|      Model    |                    Features Used                          |      R²    |
|---------------|-----------------------------------------------------------|------------|
| Baseline      | Momentum, Volatility, Volume Change                       | **0.0066** |
| Engineered    | Full feature set (lag, rolling, interaction, nonlinear)   | **0.0659** |

### Key Observation
The feature-engineered model improved R² by roughly **10×** relative to the baseline model.

Although the absolute R² remains small, this is expected in financial return prediction, where markets are noisy and true predictive signals are often weak.

---

## 🔍 Key Insights

- The **baseline model underfits strongly**, often producing near-constant predictions.
- **Feature engineering improves explanatory power**, even in a weak-signal financial environment.
- Proper preprocessing such as:
  - handling missing values
  - removing outliers
  - scaling features  
  is essential for stable optimization.
- A low or modest R² in finance does **not automatically mean the project failed** — it often reflects the true difficulty of predicting returns.

---

## 🛠️ Tech Stack

- **Python**
- **NumPy** — numerical computation
- **Pandas** — data manipulation
- **yfinance** — stock data extraction
- **Matplotlib / Seaborn** — visualization
- **scikit-learn** — scaling and evaluation

---

## 📂 Project Structure

```text
simple-stock-price-model/
│
├── notebook/
│   └── simple_stock_price_model.ipynb
│
├── README.md
└── requirements.txt