# Customer Churn Prediction

Predict which telecom customers are likely to churn using machine learning.

**Dataset:** [Telco Customer Churn – IBM Watson](https://www.kaggle.com/datasets/blastchar/telco-customer-churn)  
**Target:** `Churn` (binary — 1 = churned, 0 = retained)

---

## Project Overview

This project analyzes the Telco Customer Churn dataset to identify customers at risk of leaving. Two classification models are trained and evaluated: Logistic Regression and Random Forest. Since the dataset is class-imbalanced (~27% churn), SMOTE oversampling is applied to the training data to improve recall on churned customers.

---

## Workflow

1. **Data Loading** — load CSV, inspect shape and dtypes
2. **Data Cleaning** — fix `TotalCharges` column (blank strings → 0.0 for new customers with tenure=0), drop `customerID`
3. **Automated EDA** — `ydata-profiling` report for a full statistical overview
4. **Visual EDA**
   - Categorical features vs churn (countplots)
   - Senior citizen breakdowns by service type
   - Tenure and monthly charges vs churn (boxplots)
   - Monthly charges vs total charges (scatter)
5. **Feature Encoding**
   - Binary columns (`Partner`, `Dependents`, `PhoneService`, `PaperlessBilling`, `Churn`, `gender`) → 0/1
   - Multi-category columns (`MultipleLines`, `InternetService`, `OnlineSecurity`, etc.) → one-hot encoding
6. **Train/Test Split** — 80/20 split with `random_state=42`
7. **Class Imbalance** — SMOTE applied to training set only
8. **Modelling**
   - Logistic Regression
   - Random Forest (200 estimators, max depth 10)
9. **Evaluation** — accuracy, classification report, confusion matrix, AUC-ROC, ROC curve

---

## Key Findings

- Customers on **month-to-month contracts** churn significantly more than those on annual or two-year contracts.
- **Short tenure** is a strong churn signal — most customers who leave do so early.
- **Higher monthly charges** are associated with increased churn.
- Customers without **online security** or **tech support** churn at higher rates.
- **Electronic check** payers show elevated churn compared to other payment methods.

---

                         # This file
```

> **Note:** The dataset (`WA_Fn-UseC_-Telco-Customer-Churn.csv`) is not included in this repo.  
> Download it from [Kaggle](https://www.kaggle.com/datasets/blastchar/telco-customer-churn) and update the file path in cell 2 of the notebook.

---

