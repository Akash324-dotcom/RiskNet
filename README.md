
# RiskNet — Credit Card Fraud Detection 

## Overview

This repository contains an end-to-end **credit card fraud detection** project built as part of a structured learning roadmap (data analytics → machine learning). The **detailed problem statement, EDA, data cleaning, visualizations, and modeling rationale are intentionally documented inside the Jupyter notebooks** to keep analysis close to code.

---

## Problem Statement (Summary)

Financial institutions face significant losses due to fraudulent credit card transactions, compounded by **extreme class imbalance (~0.17% fraud rate)**. Traditional accuracy-based evaluation is misleading in such scenarios.

**Objective:**
Build an analytics-driven fraud detection pipeline that:

* Explores anonymized transaction behavior
* Handles missing values and scaling correctly
* Trains baseline and ML models suited for imbalanced data
* Evaluates performance using **Precision-Recall–focused metrics**

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
│   ├── 01_getting_started.ipynb
│
├── data/                         # Dataset path (ignored in git)
├── README.md
└── .gitignore
```

---

## Methodology (High Level)

* **Exploratory Data Analysis:** Class imbalance, amount distribution, correlation heatmaps
* **Preprocessing:**

  * Median imputation for robustness
  * Standard scaling prior to ML models
* **Modeling:**

  * Logistic Regression (baseline)
  * Tree-based / ensemble models (where applicable)
* **Evaluation:**

  * Precision, Recall, F1-score
  * **Area Under Precision-Recall Curve (AUPRC)**

📊 Detailed reasoning and code live inside the notebooks.

---

## Key Outcomes (Example)

* Improved fraud recall while controlling false positives
* Demonstrated why PR-based metrics outperform accuracy in imbalanced datasets
* Built a reproducible, modular ML pipeline suitable for banking use cases

(Exact metrics and plots are documented in `02_fraud_model.ipynb`.)

---

## Tools & Technologies

* Python
* Pandas, NumPy
* Scikit-learn
* Matplotlib, Seaborn
* Jupyter Notebook (VS Code)
* Git & GitHub
  
---

## Disclaimer

This project uses anonymized, PCA-transformed data for educational purposes and does not reflect any proprietary banking system.
