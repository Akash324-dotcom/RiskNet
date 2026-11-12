
# RiskNet — Credit Card Fraud Detection 

## Overview

This repository is a **credit card fraud detection** project built as part of a structured learning roadmap (data analytics → machine learning). The detailed problem statement, EDA, data checks and visualizations are documented inside the Jupyter notebook to keep the analysis close to the code.

**Status: exploration and data preparation are done; model training and evaluation are not yet in the repo** (see [Where it stands](#where-it-stands)).

---

## Problem Statement (Summary)

Financial institutions face significant losses due to fraudulent credit card transactions, compounded by **extreme class imbalance (~0.17% fraud rate)**. Traditional accuracy-based evaluation is misleading in such scenarios.

**Objective:**
Build an analytics-driven fraud detection pipeline that:

* Explores anonymized transaction behavior
* Prepares the data correctly for imbalanced classification
* Trains baseline and ML models suited for imbalanced data *(next step)*
* Evaluates performance using **Precision-Recall–focused metrics** *(next step)*

>  Full problem statement and justification are documented in `01_getting_started.ipynb`.

---

## Data Access
The dataset is not included due to size and privacy constraints.
Download it from Kaggle (Credit Card Fraud Detection dataset) - https://www.kaggle.com/datasets/mlg-ulb/creditcardfraud
and place it in:
banking_fraudulant_analytics/data/

---

## Dataset

* Public European credit card transaction dataset (Sept 2013)
* ~284,807 transactions, 492 frauds
* Features `V1–V28` are **PCA-transformed** for confidentiality
* `Time` and `Amount` are original features
* `Class`: 1 = Fraud, 0 = Legitimate

 **Note:** Raw dataset is intentionally excluded from GitHub due to size limits.

---

## Project Structure

```text
banking_fraudulant_analytics/
│
├── notebooks/
│   └── 01_getting_started.ipynb   # problem statement, EDA, data checks, train/test split
├── data/                          # put creditcard.csv here (ignored by git)
└── requirements.txt
```

---

## Where it stands

### Done (results from the notebook)

| Step | Result |
|---|---|
| Size and types | 284,807 rows × 31 columns, all numeric |
| Missing values | None in any column |
| Class balance | 284,315 legitimate and **492 fraud (0.1727%)** |
| Feature engineering | `Time` (seconds) converted to `Hour` (hour of day), then dropped |
| Correlations | `V1`–`V28` are uncorrelated with each other (as expected after PCA). The strongest pairs involve the original columns: `Amount`–`V2` (−0.53), `Time`–`V3` (−0.42), `Amount`–`V7` (0.40) |
| Distributions | Histograms of every feature for fraud versus legitimate transactions |
| Train/test split | 80/20, `random_state=100`: 227,845 train rows (396 fraud) and 56,962 test rows (96 fraud). The split is **not stratified**, so the fraud share differs slightly (0.174% train, 0.169% test) |

The last notebook cell draws a confusion matrix of `y_test` against itself. That is a check that the plotting function works, **not a model result**.

### Not done yet

* A trained model of any kind (no logistic regression baseline, no tree-based model)
* Scaling of `Amount` and the imputation step described in the notebook (no values are missing, so imputation is not needed for this dataset)
* Precision, recall, F1 and AUPRC on the test set
* Any reported fraud-detection performance

### Next

1. Stratified split, so the 492 frauds are spread evenly.
2. Logistic regression baseline with class weights, then a gradient-boosted model.
3. Evaluate on the held-out test set with Precision-Recall curve and AUPRC, plus precision and recall at a chosen threshold, because accuracy is misleading at 0.17% fraud.
4. Record the numbers here.

---

## Tools & Technologies

* Python
* Pandas, NumPy
* Scikit-learn (train/test split and metrics so far)
* Matplotlib, Seaborn
* Jupyter Notebook (VS Code)
* Git & GitHub
  
---

## Disclaimer

This project uses anonymized, PCA-transformed data for educational purposes and does not reflect any proprietary banking system.
