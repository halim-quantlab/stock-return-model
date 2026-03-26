📊 Simple Stock Return Model — Learning-Focused Quant Project

This project develops a practical, end-to-end machine learning pipeline applied to financial time series data, with a strong emphasis on intuition, robustness, and realistic evaluation rather than purely maximizing predictive accuracy.

⸻

🎯 Objective

The goal of this project is to explore how different modeling approaches behave on financial data, and to understand the limitations of predictive modeling in low signal-to-noise environments such as stock returns.

The project implements:
- Feature engineering (lag, rolling statistics, interaction, nonlinear features)
- Data preprocessing (handling missing values, outlier removal)
- Feature scaling (standardization)
- Time-based train/test split (no data leakage)
- Model training using:
- Linear Regression (gradient descent)
- Logistic Regression (direction prediction)
- Model evaluation using:
- R² (regression)
- Accuracy, confusion matrix, classification report (classification)
- Strategy construction using probability-based signals
- Backtesting using actual returns (out-of-sample)
- Regularization (L2) to control model complexity
- Visualization and diagnostics (cost curves, weights, predictions)

⸻

🧠 Feature Engineering

To improve model expressiveness, the following features were introduced:

1. Lag Features
- Return_lag1, Return_lag5

2. Rolling Statistics
- Momentum (rolling mean)
- Volatility (rolling standard deviation)

3. Interaction Terms
- Momentum × Volatility
- Momentum × Volume Change

4. Nonlinear Features
- Squared terms (Momentum², Volatility²)

These features aim to capture:
- temporal dependencies
- nonlinear relationships
- interaction effects

⸻

📈 Modeling Framework

🔹 1. Linear Regression (Return Prediction)
	- Predicts magnitude of next-period return
	- Optimized via gradient descent
	- Evaluated using:
	- R² score
	- Actual vs Predicted plots
	- Cost convergence and parameter evolution

⸻

🔹 2. Logistic Regression (Direction Prediction)
	- Predicts probability of positive return
	- Output: probability ∈ [0, 1]

Decision Rule:
	- Long if probability > 0.55
	- Short if probability < 0.45
	- Otherwise no position

Evaluation:
	- Accuracy
	- Confusion matrix
	- Classification report
	- Probability distribution

⸻

🔹 3. Regularization (L2)
	- Applied to logistic regression
	- Reduces overfitting
	- Stabilizes weight magnitudes

Observed effects:
	- Smaller weights
	- Slight trade-off between bias and variance


⸻

📈 Results & Observations

Regression Models
image.png

🔍 Key Insights
	- Baseline model shows negative R², meaning worse than predicting the mean
	- Feature engineering improves R² to positive territory, indicating the emergence of weak predictive signal
	- Predictions remain noisy and weakly aligned with actual returns

⸻

📊 Visualization Insights
	- Actual vs Predicted plots
	- Baseline → near-constant predictions
	- Engineered → greater spread and responsiveness
	- Perfect-fit reference line (y = x)
	- Highlights deviation from ideal predictions
	- Cost vs Iteration
	- Confirms convergence of gradient descent
	- Weights vs Iteration
	- Shows stabilization of feature importance

⸻

⚠️ Key Learnings

This project highlights important realities of quantitative modeling:
	- Financial markets have low signal-to-noise ratio
	- Predictive power is typically weak and unstable
	- Feature engineering helps, but does not solve the problem
	- Proper preprocessing (scaling, outlier handling) is critical
	- Logistic regression can be more useful than regression for trading decisions
	- Backtesting must use actual returns, not classification labels
	- Train/test split is essential to avoid misleading results

⸻

💾 Reproducibility

The project includes saving:
	- Cleaned datasets
	- Train/test splits
	- Model outputs
	- Plots and summaries

This ensures:
	- reproducibility
	- debugging capability
	- consistent backtesting

⸻

📦 Requirements

Install dependencies with:
pip install -r requirements.txt

Main libraries used:
	- numpy
	- pandas
	- matplotlib
	- seaborn
	- scikit-learn

⸻

🧩 Summary

This project demonstrates a complete pipeline from raw financial data to model evaluation and strategy backtesting.

Rather than focusing solely on predictive accuracy, it emphasizes:
	- understanding model behavior
	- interpreting weak signals
	- evaluating models realistically
	- bridging theory and real-world finance

It serves as a strong foundation for more advanced work such as:
	- factor models
	- regime detection
	- portfolio optimization
	- machine learning-based trading strategies

