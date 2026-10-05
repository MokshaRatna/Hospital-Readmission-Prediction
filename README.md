# Hospital Readmission Prediction Using Elastic Net

A machine learning and web-based academic project that predicts the risk of **hospital readmission within 30 days** using **Elastic Net Regularized Logistic Regression**.

> **Academic Project:** This system is intended for educational and demonstration purposes only. It is not a clinical diagnostic or treatment system.

---

## 📌 Project Overview

Hospital readmissions can increase healthcare costs and indicate the need for closer patient follow-up. This project develops a machine learning model to estimate whether a patient is likely to be readmitted within 30 days.

The system combines:

- Data preprocessing
- Exploratory Data Analysis
- Feature selection
- Elastic Net Regularized Logistic Regression
- Model evaluation
- FastAPI backend
- React frontend
- SQLite database
- Patient visit history
- Administrator dashboard

### Prediction Target

- `<30` → `1` — Readmitted within 30 days
- `>30` or `NO` → `0` — Not readmitted within 30 days

---

## 🗂️ Dataset

The project uses the **Diabetes 130-US Hospitals Dataset** from the UCI Machine Learning Repository.

| Property | Value |
|---|---:|
| Hospital encounters | 101,766 |
| Original CSV columns | 50 |
| Cleaned columns | 43 |
| Readmitted within 30 days | 11,357 |
| Not readmitted within 30 days | 90,409 |
| Positive rate | 11.16% |
| Missing cells after cleaning | 0 |
| Duplicate rows | 0 |

---

## 🔧 Data Preprocessing

The following preprocessing steps were performed:

1. Converted `?` values into missing values.
2. Removed `encounter_id` and `patient_nbr`.
3. Removed highly incomplete features such as `weight`, `payer_code`, and `medical_specialty`.
4. Removed features with no useful variation.
5. Filled categorical missing values with `Unknown`.
6. Median-imputed numerical missing values.
7. Converted the target into a binary classification problem.
8. Prepared categorical and numerical features for model training.

---

## 📊 Exploratory Data Analysis

### Target Distribution

The dataset is imbalanced, with considerably more encounters that were not followed by readmission within 30 days.

![Target Distribution](assets/target_distribution.png)

---

## 🤖 Machine Learning Model

The project uses:

### Elastic Net Regularized Logistic Regression

Elastic Net combines:

- **L1 regularization** for feature selection.
- **L2 regularization** for handling correlated features and improving model stability.

### Model Configuration

```text
Algorithm        : Logistic Regression
Penalty          : Elastic Net
Solver           : SAGA
C                : 0.05
L1 Ratio         : 0.20
Class Weight     : Balanced
Train/Test Split : 80/20 Stratified Split
