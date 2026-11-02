# Used-Car Price Prediction with Linear, Ridge and Lasso Regression

A regression project exploring how vehicle specifications, condition, and equipment features relate to used-car prices. The workflow covers exploratory analysis, feature engineering, log-target transformation, multicollinearity checks, and regularized linear models.

## Objective

Estimate used-car prices from attributes such as mileage, vehicle age, engine power, displacement, fuel type, brand, body type, and equipment.

The project compares a Linear Regression baseline with Ridge (L2) and Lasso (L1) regression to assess whether regularization improves generalization after feature engineering.

## Data

The notebook reports **15,915 raw observations** and loads the input from:

```text
Car_Price_data.csv
```

That CSV is not currently included in the repository. Obtain the source dataset separately and place it in the project root using the exact filename expected by the notebook before running the analysis.

The notebook uses vehicle attributes such as:

- Mileage (`km`) and vehicle age.
- Engine power (`hp_kW`) and displacement (`Displacement_cc`).
- Fuel, body type, brand, gears, and VAT status.
- Equipment lists covering comfort, entertainment, safety, and extras.

The original dataset source and licence should be added to this README before redistributing the data.

## Methodology

### 1. Exploratory analysis

- Inspect numerical and categorical feature distributions.
- Examine class imbalance in categorical fields.
- Investigate the right-skewed target price distribution.
- Review missing values and outliers.

### 2. Feature engineering

- Extract brand information from `make_model`.
- Consolidate rare categories to reduce sparse one-hot features.
- Convert comma-separated equipment fields into count features:
  - `comfort_count`
  - `safety_count`
  - `extras_count`
- Apply a log transformation to the target and model `log_price`.

### 3. Preprocessing and split

- The notebook uses a **70:30 train/test split** with `random_state=0`.
- Categorical variables are encoded for regression.
- Numerical features are scaled using MinMax scaling.
- The target used by the models is `log_price`, not the original price column.

### 4. Multicollinearity

Correlation analysis and Variance Inflation Factor (VIF) are used to investigate redundant predictors, including relationships among gears, displacement, weight, and other vehicle specifications.

### 5. Models and tuning

| Model | Regularization | Tuning |
|---|---|---|
| Linear Regression | None | Baseline |
| Ridge | L2 | Five-fold GridSearchCV |
| Lasso | L1 | Five-fold GridSearchCV |

The notebook's final selected values are:

| Model | Selected alpha |
|---|---:|
| Ridge | 0.0001 |
| Lasso | 0.00000886 |

## Test-set results

The following values are taken from the notebook's final comparison table.

| Model | MAE | RMSE | R² |
|---|---:|---:|---:|
| Linear Regression | 0.089543 | 0.120346 | 0.895732 |
| Ridge Regression | 0.089543 | 0.120346 | 0.895732 |
| Lasso Regression | 0.089540 | 0.120340 | 0.895742 |


**Important metric interpretation:** These metrics are calculated against `log_price`. MAE and RMSE are therefore in log-price units, not in the original currency of the car listing. They should not be presented as an average error of 0.0895 or 0.1203 currency units. To communicate price error in currency, inverse-transform predictions and evaluate them against the original `price` values.

### Key takeaway

All three models perform almost identically on the reported test split. Ridge and Lasso provide negligible improvement over the unregularized baseline, suggesting that the chosen preprocessing and feature engineering already produce a reasonably stable linear modeling problem.

## Technology stack

Python, pandas, NumPy, Matplotlib, Seaborn, scikit-learn, Linear Regression, Ridge, Lasso, GridSearchCV, VIF.

## Repository contents

```text
.
├── RR_Car_Price_Prediction_Piyush.ipynb
├── RR_Car_Price_Prediction_Piyush.pdf
└── README.md
```

- [Open the analysis notebook](./RR_Car_Price_Prediction_Piyush.ipynb)
- [Open the project report](./RR_Car_Price_Prediction_Piyush.pdf)

## How to run

Clone the repository:

```bash
git clone https://github.com/piyush0920/Car_price_predictions.git
cd Car_price_predictions
```

Install the main dependencies:

```bash
pip install pandas numpy matplotlib seaborn scikit-learn statsmodels jupyter
```

Place `Car_Price_data.csv` in the repository root and launch:

```bash
jupyter notebook RR_Car_Price_Prediction_Piyush.ipynb
```

Run the notebook cells in order. The input CSV must be obtained separately because it is not part of the committed repository.

## Limitations and next steps

- Add the original dataset source and licence.
- Evaluate inverse-transformed predictions in the original price unit.
- Compare against non-linear models such as Random Forest or Gradient Boosting using the same held-out split.
- Consider cross-validation and a more recent external test set to assess robustness across vehicle markets.

## Author

**Piyush Sharma**  
[GitHub](https://github.com/piyush0920) · [Portfolio](https://piyush0920.github.io/) · [LinkedIn](https://linkedin.com/in/piyush-sharma-6591171ba)
