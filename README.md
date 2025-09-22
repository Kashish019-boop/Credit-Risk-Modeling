# Credit Risk Modeling using Machine Learning

## Overview

This project predicts **credit approval risk (Approved\_Flag: P1–P4)** using two datasets (`case_study1.xlsx`, `case_study2.xlsx`). The workflow includes data cleaning, feature selection, encoding, scaling, and training multiple models (Random Forest, XGBoost, Decision Tree). XGBoost is tuned further with hyperparameter search.

---

## Files

* `credit_risk_modeling_using_ml.py` — main script
* `case_study1.xlsx`, `case_study2.xlsx` — datasets

---

## Quick Start

```bash
python -m venv venv
source venv/bin/activate   # or venv\\Scripts\\activate on Windows
pip install -r requirements.txt
python credit_risk_modeling_using_ml.py
```

**requirements.txt**

```
numpy
pandas
matplotlib
scikit-learn
xgboost
statsmodels
scipy
openpyxl
```

---

## Process

1. **Data prep**: Handle `-99999` as missing, drop bad rows/columns, merge on `PROSPECTID`.
2. **Feature selection**: Chi-square (categorical), VIF (multicollinearity), ANOVA (numeric significance).
3. **Encoding**: Ordinal mapping for `EDUCATION`, one-hot for other categorical variables.
4. **Scaling**: StandardScaler on selected numeric features.
5. **Models**: Random Forest, XGBoost, Decision Tree.
6. **Tuning**: GridSearchCV + manual hyperparameter sweeps for XGBoost.
7. **Evaluation**: Accuracy + per-class precision/recall/F1.

---

## Outputs

* Console prints: feature tests, model accuracy, precision/recall/F1 per class, best hyperparameters.
* Predicted `Approved_Flag` for test set.

---

## Issues & Improvements

* **Scaling leakage**: scale after train/test split (use Pipelines).
* **VIF routine**: fix iterative dropping logic.
* **Evaluation**: use stratified CV, confusion matrix, ROC AUC.
* **Efficiency**: replace manual hyperparameter loop with RandomizedSearchCV/Optuna.
* **Reproducibility**: save models with joblib, use consistent seeds.

---

## Next Steps

* Handle class imbalance (SMOTE/class weights).
* Add feature importance plots.
* Package code into functions/notebook with configs.

---

*Generated to document and improve the original script.*
