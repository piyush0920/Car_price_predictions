# 🚗 Car Price Prediction using Linear, Ridge & Lasso Regression

A machine learning project focused on predicting car prices using **Linear Regression**, **Ridge**, and **Lasso** models, with an emphasis on **regularization techniques**, **feature engineering**, and **model evaluation**.

---

## 📌 Overview

This project aims to build a regression model to estimate car prices based on vehicle attributes such as:

- Mileage (`km`)
- Age  
- Engine specifications (`hp_kW`, `Displacement_cc`)  
- Fuel type  
- Brand  
- Equipment features  

The project follows a complete machine learning workflow:

> **EDA → Feature Engineering → Preprocessing → Modeling → Evaluation → Interpretation**

---

## 📂 Project Structure

---

## 📊 Exploratory Data Analysis (EDA)

### Key Observations:
- Dataset contains both **numerical and categorical features**
- Some categorical variables show **class imbalance**
- Several columns contain **comma-separated values**

### 🎯 Target Variable: `price`
- Highly **right-skewed**
- Contains **high-value outliers**

### ✅ Transformation:
- Applied **log transformation**:
  - Improved normality
  - Reduced skewness
  - Stabilized variance

---

## ⚙️ Feature Engineering & Preprocessing

### 1. Categorical Feature Handling
- Grouped **rare categories** to reduce sparsity
- Extracted **brand** from `make_model`

### 2. Text Feature Engineering
Converted comma-separated features into **count-based variables**:
- `comfort_count`
- `safety_count`
- `extras_count`

### 3. Train-Test Split
- 80% Training  
- 20% Testing  

### 4. Feature Scaling
- Applied **Min-Max Scaling** to numerical features
- Left **binary variables unscaled**

---

## 🔗 Multicollinearity Analysis

- Used:
  - **Correlation Heatmap**
  - **Variance Inflation Factor (VIF)**

### Insights:
- Some features showed **high VIF values** (e.g., gears, displacement, weight)
- Instead of removing features:
  - Addressed multicollinearity using **regularization**

---

## 🤖 Models Implemented

### 1. Linear Regression (Baseline)
- Trained on log-transformed target
- Serves as a benchmark

---

### 2. Ridge Regression (L2 Regularization)
- Tuned using **5-fold cross-validation**
- Optimal alpha: **0.01**
- Helps reduce coefficient variance

---

### 3. Lasso Regression (L1 Regularization)
- Performs **feature selection**
- Optimal alpha found at **lower boundary**
- Minimal regularization impact observed

---

## 📈 Model Performance

| Model              | MAE      | RMSE     | R²       |
|--------------------|----------|----------|----------|
| Linear Regression  | 0.089543 | 0.120346 | 0.895732 |
| Ridge Regression   | 0.089543 | 0.120346 | 0.895732 |
| Lasso Regression   | 0.089540 | 0.120340 | 0.895742 |

### 📌 Key Insight:
- All models performed **almost identically**
- Regularization had **minimal impact**

---

## 📉 Residual Diagnostics

### Observations:
- Residuals are:
  - Randomly scattered around zero ✅
  - Approximately normally distributed ✅  

### Conclusion:
- No major violations of:
  - Linearity  
  - Homoscedasticity  

---

## 🔍 Interpretation of Results

- Despite multicollinearity:
  - Regularization had **limited effect**
- Reason:
  - Strong **feature engineering**
  - Proper **data preprocessing**

---

## 🧠 Key Takeaways

- ✅ Feature engineering > Model complexity  
- ✅ Log transformation significantly improves performance  
- ✅ Multicollinearity does not always harm predictive power  
- ✅ Regularization should be **validated, not assumed necessary**  
- ✅ Simple models can perform exceptionally well with clean data  

---

## 🚀 Future Improvements

- Try **non-linear models** (Random Forest, XGBoost)
- Perform **hyperparameter optimization**
- Use **feature importance techniques**
- Deploy as a **web app (Streamlit / Flask)**

---

## 👤 Author

**Piyush Sharma**

- 📧 Open to opportunities in Data Science / Analytics  
- 💼 Skilled in ML, EDA, and statistical modeling  

---

## ⭐ If you found this useful

Give this repo a ⭐ and feel free to fork it!
