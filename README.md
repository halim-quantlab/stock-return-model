# 📊 Stock Return Model Machine Learning Quant Project

This project builds a practical, end-to-end machine learning pipeline for financial time series data, with emphasis on intuition, robustness, and realistic evaluation rather than purely maximizing predictive accuracy.

---

# 🎯 Objective

The goal of this project is to explore how different modeling approaches behave on stock return data and to understand the limitations of prediction in low signal-to-noise environments.

The project includes:

- Feature engineering (lag, rolling statistics, interaction, and nonlinear features)
- Data preprocessing (missing-value handling and outlier removal)
- Feature scaling (standardization)
- Time-based train/test split to avoid data leakage
- Model training using:
  - Linear Regression (gradient descent)
  - Logistic Regression (direction prediction)
- Model evaluation using:
  - R² for regression
  - Accuracy, confusion matrix, and classification report for classification
- Strategy construction using probability-based signals
- Out-of-sample backtesting using actual next returns
- L2 regularization to control model complexity
- Visualization and diagnostics (cost curves, parameter evolution, prediction plots)

---

# 🧠 Feature Engineering

To improve model expressiveness beyond a small baseline feature set, the following engineered variables were introduced.

## 1. Lag Features
- `Return_lag1`
- `Return_lag5`

## 2. Rolling Statistics
- `Momentum_5`, `Momentum_10`
- `Volatility_5`, `Volatility_10`

## 3. Interaction Terms
- `Mom_x_Vol`
- `Mom_x_VolChange`

## 4. Nonlinear Features
- `Momentum_sq`
- `Volatility_sq`

These features are intended to capture:

- temporal dependencies
- nonlinear relationships
- interaction effects between market variables

---

# 📈 Modeling Framework

## 1. Linear Regression (Return Prediction)

This model predicts the **magnitude** of next-period return.

**Key elements**
- Optimized via batch gradient descent
- Evaluated using R²
- Visualized with:
  - Actual vs Predicted plots
  - Cost vs Iteration
  - Weights vs Iteration
  - Bias vs Iteration

---

## 2. Logistic Regression (Direction Prediction)

This model predicts the **probability** that the next return is positive.

**Output**
- Probability in the range \([0,1]\)

**Decision rule**
- Long if probability > 0.5
- Short if probability < 0.5
- Otherwise no position

**Evaluation**
- Accuracy
- Confusion matrix
- Classification report
- Probability distribution plots

---

## 3. L2 Regularization

L2 regularization is applied to logistic regression to reduce overfitting and stabilize coefficients.

**Observed effect**
- Smaller weight magnitudes
- Slight trade-off between flexibility and stability

---

# 📊 Strategy Construction and Backtesting

A simple signal-based trading strategy is built from logistic regression probabilities.

## Signal Rules
- \( +1 \): long position
- \( -1 \): short position
- \( 0 \): no trade

## Return Construction
Strategy returns are computed using **actual next-period returns**, not binary class labels.

## Performance Diagnostics
- Cumulative portfolio value
- Average strategy return
- Volatility
- Sharpe-like ratio
- Number of trades

This makes the project more realistic by connecting model outputs to trading outcomes.

---

# 📈 Results and Observations

## Regression Results

| Model      | Features Used | R² |
|------------|---------------|----|
| Baseline   | Momentum, Volatility, Volume Change | **-0.0009** |
| Engineered | Full feature set (lag, rolling, interaction, nonlinear) | **0.0221** |

## Key Insights

- The baseline model produced a **negative R²**, meaning it performed worse than a naive mean predictor.
- Feature engineering improved R² into **positive territory**, indicating the emergence of weak but meaningful predictive structure.
- Predictions remain noisy and only weakly aligned with actual returns, which is expected in financial markets.

---

# 📊 Visualization Insights

The project includes several visual diagnostics:

## Actual vs Predicted
- Baseline model: near-constant predictions and weak explanatory power
- Engineered model: greater spread and stronger responsiveness

## Perfect-Fit Reference Line
- A \( y = x \) reference line is added to show deviation from ideal prediction

## Optimization Diagnostics
- Cost vs Iteration: confirms convergence behavior
- Weights vs Iteration: shows stabilization of coefficients
- Bias vs Iteration: tracks intercept convergence

## Probability Distribution Plots
- Show how confident the logistic model is
- Help justify threshold-based signal construction

---

# ⚠️ Key Learnings

This project highlights several important realities of quantitative modeling:

- Financial markets have a **low signal-to-noise ratio**
- Predictive power is often **weak and unstable**
- Feature engineering helps, but does not eliminate noise
- Proper preprocessing (especially scaling and outlier handling) is critical
- Logistic regression can be more useful than regression when the goal is trading direction
- Backtesting must use **actual returns**, not classification labels
- Time-based train/test splitting is essential for realistic evaluation

---

# 💾 Reproducibility

The project saves:

- cleaned datasets
- train/test splits
- model outputs
- plots
- summary tables

This improves:

- reproducibility
- debugging
- consistency across experiments

---

# 📦 Requirements

Install dependencies with:

```bash
pip install -r requirements.txt
