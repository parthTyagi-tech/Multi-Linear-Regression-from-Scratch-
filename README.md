# 📐 MultiLinReg

> **A clean, self-contained Python implementation of Multiple Linear Regression — built from scratch, no black boxes.**

[![Python](https://img.shields.io/badge/Python-3.8%2B-blue?logo=python&logoColor=white)](https://python.org)
[![License: MIT](https://img.shields.io/badge/License-MIT-green.svg)](LICENSE)
[![NumPy](https://img.shields.io/badge/NumPy-Powered-013243?logo=numpy)](https://numpy.org)
[![Status](https://img.shields.io/badge/Status-Active-brightgreen)]()

---

## 🧠 What Is This?

**MultiLinReg** is a from-scratch implementation of **Multiple Linear Regression** in Python. No `sklearn`, no magic — just math, NumPy, and clean code.

Use it to:
- Understand exactly how MLR works under the hood
- Predict a continuous target variable from multiple input features
- Learn the Ordinary Least Squares (OLS) method step-by-step

Whether you're a student, a data science learner, or just curious about what goes on inside `LinearRegression().fit()` — this repo is for you.

---

## 📖 The Math

Given a dataset with **n** observations and **p** features, we model the relationship as:

```
ŷ = β₀ + β₁x₁ + β₂x₂ + ... + βₚxₚ
```

In matrix form:

```
ŷ = Xβ
```

The **Ordinary Least Squares (OLS)** solution that minimizes the sum of squared residuals:

```
β = (XᵀX)⁻¹ Xᵀy
```

Where:
- `X` — Design matrix (features + bias column of 1s)
- `y` — Target vector
- `β` — Learned coefficient vector

---

## 📁 Project Structure

```
multilinreg/
│
├── multilinreg/
│   ├── __init__.py          # Package entry point
│   ├── model.py             # MultipleLinearRegression class
│   └── metrics.py           # R², MSE, MAE, RMSE
│
├── examples/
│   ├── basic_usage.py       # Quick start example
│   └── housing_demo.py      # Real-world demo with housing data
│
├── tests/
│   ├── test_model.py        # Unit tests for model
│   └── test_metrics.py      # Unit tests for metrics
│
├── requirements.txt
├── LICENSE
└── README.md                # You are here
```

---

## 🚀 Quick Start

### Installation

```bash
git clone https://github.com/yourusername/multilinreg.git
cd multilinreg
pip install -r requirements.txt
```

### Usage

```python
import numpy as np
from multilinreg import MultipleLinearRegression

# Sample data: 3 features, 100 observations
X = np.random.rand(100, 3)
y = 3*X[:, 0] + 1.5*X[:, 1] - 2*X[:, 2] + np.random.randn(100) * 0.1

# Split into train/test
split = 80
X_train, X_test = X[:split], X[split:]
y_train, y_test = y[:split], y[split:]

# Fit model
model = MultipleLinearRegression()
model.fit(X_train, y_train)

# Predict
y_pred = model.predict(X_test)

# Evaluate
print("Coefficients:", model.coef_)
print("Intercept:   ", model.intercept_)
print("R² Score:    ", model.score(X_test, y_test))
```

**Output:**
```
Coefficients: [ 2.998  1.503 -1.997]
Intercept:    0.012
R² Score:     0.9987
```

---

## 🔧 API Reference

### `MultipleLinearRegression`

```python
model = MultipleLinearRegression()
```

| Method | Description |
|---|---|
| `model.fit(X, y)` | Train the model using OLS |
| `model.predict(X)` | Return predicted values |
| `model.score(X, y)` | Return the R² coefficient of determination |
| `model.coef_` | Learned feature coefficients (shape: `[p]`) |
| `model.intercept_` | Learned bias/intercept term |
| `model.summary()` | Print a regression summary table |

### `metrics.py`

```python
from multilinreg.metrics import mse, rmse, mae, r2_score

mse(y_true, y_pred)      # Mean Squared Error
rmse(y_true, y_pred)     # Root Mean Squared Error
mae(y_true, y_pred)      # Mean Absolute Error
r2_score(y_true, y_pred) # Coefficient of Determination (R²)
```

---

## 📊 Example Output — `model.summary()`

```
==================================================
         MULTIPLE LINEAR REGRESSION SUMMARY
==================================================
 Observations  : 80
 Features      : 3
--------------------------------------------------
 Coefficient   Value      
--------------------------------------------------
 Intercept     0.0124
 x1            2.9980
 x2            1.5030
 x3           -1.9970
--------------------------------------------------
 R²            0.9987
 Adjusted R²   0.9986
 MSE           0.0103
 RMSE          0.1015
==================================================
```

---

## ⚙️ Requirements

```
numpy>=1.21.0
```

That's it. No pandas, no sklearn, no heavy dependencies.

---

## 🧪 Running Tests

```bash
python -m pytest tests/ -v
```

---

## 📚 Concepts Covered

- [x] Ordinary Least Squares (OLS) derivation
- [x] Design matrix construction (bias term injection)
- [x] Matrix inversion via `np.linalg.inv`
- [x] R², Adjusted R², MSE, RMSE, MAE
- [x] Predictions on unseen data
- [ ] Feature scaling / normalization *(coming soon)*
- [ ] Gradient Descent solver *(coming soon)*
- [ ] Regularization (Ridge / Lasso) *(coming soon)*

---

## 🤔 Why Build It From Scratch?

> *"What I cannot create, I do not understand."*  
> — Richard Feynman

Libraries like `scikit-learn` are production-grade tools, but they abstract away the mathematics. This project exists to make those abstractions transparent — every line of code maps directly to a concept in linear algebra and statistics.

---

## 📄 License

MIT License — see [LICENSE](LICENSE) for details.

---

## 🙋 Contributing

Pull requests are welcome! Feel free to:
- Add new solvers (gradient descent, etc.)
- Improve the summary output
- Add more example notebooks
- Fix any bugs or improve docs

Open an issue first for major changes.

---

<p align="center">Built with 🧮 math and ☕ coffee</p>
