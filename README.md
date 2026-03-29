# 🏦 Loan Status Prediction

A machine learning project that predicts whether a loan application will be approved or rejected based on applicant details such as income, education, marital status, and property area.

---

## 📋 Table of Contents

- [Overview](#overview)
- [Dataset](#dataset)
- [Project Workflow](#project-workflow)
- [Models Used](#models-used)
- [Results](#results)
- [Technologies Used](#technologies-used)
- [How to Run](#how-to-run)
- [Project Structure](#project-structure)

---

## Overview

This project tackles a **binary classification problem**: given a set of applicant features, predict whether a loan will be approved (`Y`) or not (`N`). It walks through the complete data science pipeline — from data cleaning and exploratory analysis to model training and evaluation — comparing multiple classification algorithms to find the best performer.

---

## Dataset

- **Source:** `train_u6lujuX_CVtuZ9i.csv` (Analytics Vidhya Loan Prediction dataset)
- **Target variable:** `Loan_Status` (Y = Approved, N = Rejected)

**Features used:**

| Feature | Description |
|---|---|
| `Gender` | Male / Female |
| `Married` | Applicant marital status |
| `Dependents` | Number of dependents |
| `Education` | Graduate / Not Graduate |
| `Self_Employed` | Self-employed or not |
| `ApplicantIncome` | Applicant's monthly income |
| `CoapplicantIncome` | Co-applicant's monthly income |
| `LoanAmount` | Requested loan amount |
| `Loan_Amount_Term` | Term of loan in months |
| `Credit_History` | Credit history record |
| `Property_Area` | Rural / Urban / Semiurban |

---

## Project Workflow

1. **Data Loading** — Load the CSV dataset using pandas.
2. **Exploratory Data Analysis (EDA)**
   - Inspect shape, head, and missing values.
   - Visualize distributions using seaborn (Education vs Loan Status, Married vs Loan Status).
3. **Data Preprocessing**
   - Drop rows with missing values.
   - Reset index after cleaning.
   - Replace `3+` in the `Dependents` column with `4` for numeric conversion.
   - **Label Encoding** of categorical columns:
     - `Married`: Yes → 1, No → 0
     - `Gender`: Male → 1, Female → 0
     - `Education`: Graduate → 1, Not Graduate → 0
     - `Self_Employed`: Yes → 1, No → 0
     - `Property_Area`: Rural → 0, Urban → 1, Semiurban → 2
     - `Loan_Status`: Y → 1, N → 0
4. **Feature/Target Split** — Features (`X`) and target (`y`) extracted from the dataset.
5. **Train-Test Split** — 75% training, 25% testing (`random_state=42`).
6. **Model Training & Evaluation** — Four classifiers trained and compared.

---

## Models Used

| Model | Library | Key Parameters |
|---|---|---|
| Logistic Regression | `sklearn.linear_model` | Default |
| K-Nearest Neighbors | `sklearn.neighbors` | `n_neighbors=15` |
| Support Vector Machine | `sklearn.svm` | `kernel='rbf'` |
| Random Forest | `sklearn.ensemble` | `n_estimators=30`, `criterion='entropy'` |

Each model is evaluated using:
- **Confusion Matrix** (visualized as a heatmap)
- **Accuracy Score**

---

## Results

All four classifiers were trained and tested on the same train-test split. The **Random Forest Classifier** and **Logistic Regression** generally perform well on this dataset. Refer to the notebook outputs for exact accuracy scores and confusion matrices for each model.

---

## Technologies Used

- **Python 3**
- **NumPy** — Numerical operations
- **Pandas** — Data loading and manipulation
- **Seaborn** — Data visualization
- **Scikit-learn** — Machine learning models and evaluation metrics

---

## How to Run

1. **Clone the repository**
   ```bash
   git clone https://github.com/your-username/loan-status-prediction.git
   cd loan-status-prediction
   ```

2. **Install dependencies**
   ```bash
   pip install numpy pandas seaborn scikit-learn
   ```

3. **Add the dataset**
   Place `train_u6lujuX_CVtuZ9i.csv` in the `/content/` directory (or update the file path in the notebook).

4. **Run the notebook**
   Open `_Loan_Mount_Prediction.ipynb` in Jupyter Notebook or Google Colab and run all cells.

---

## Project Structure

```
loan-status-prediction/
│
├── _Loan_Mount_Prediction.ipynb   # Main notebook
├── train_u6lujuX_CVtuZ9i.csv      # Dataset (not included, download separately)
└── README.md                      # Project documentation
```

---

## 📌 Notes

- The dataset can be downloaded from the [Analytics Vidhya Loan Prediction Challenge](https://datahack.analyticsvidhya.com/contest/practice-problem-loan-prediction-iii/).
- Missing values are handled by dropping rows — future improvements could explore imputation strategies.
- Feature scaling was not applied; adding `StandardScaler` may improve KNN and SVM performance.
