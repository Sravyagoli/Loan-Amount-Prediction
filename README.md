# 🏦 Loan Approval Prediction

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
- [Future Improvements](#future-improvements)

---

## Overview

This project tackles a **binary classification problem**: given a set of applicant features, predict whether a loan will be approved (`Y`) or not (`N`). It walks through the complete data science pipeline — from data cleaning and exploratory analysis to model training and evaluation — comparing multiple classification algorithms to find the best performer.

---

## Dataset

- **Source:** Analytics Vidhya Loan Prediction Dataset ([Kaggle link](https://www.kaggle.com/datasets/moma12/train-u6lujux-cvtuz9i-1))
- **Size:** 614 applicants
- **Target variable:** `Loan_Status` (Y = Approved, N = Rejected)

| Feature             | Description                   |
|---------------------|-------------------------------|
| `Gender`            | Male / Female                 |
| `Married`           | Applicant marital status      |
| `Dependents`        | Number of dependents          |
| `Education`         | Graduate / Not Graduate       |
| `Self_Employed`     | Self-employed or not          |
| `ApplicantIncome`   | Applicant's monthly income    |
| `CoapplicantIncome` | Co-applicant's monthly income |
| `LoanAmount`        | Requested loan amount         |
| `Loan_Amount_Term`  | Term of loan in months        |
| `Credit_History`    | Credit history record         |
| `Property_Area`     | Rural / Urban / Semiurban     |

---

## Project Workflow

1. **Data Loading** — Load CSV dataset using Pandas
2. **Exploratory Data Analysis (EDA)**
   - Inspect shape, missing values, and distributions
   - Visualize Education vs Loan Status, Married vs Loan Status using Seaborn
3. **Data Preprocessing**
   - Drop rows with missing values
   - Replace `3+` in Dependents column with `4` for numeric conversion
   - Label encode all categorical columns (Gender, Married, Education, Self_Employed, Property_Area, Loan_Status)
4. **Feature/Target Split** — Extract features (`X`) and target (`y`)
5. **Train-Test Split** — 75% training, 25% testing (`random_state=42`)
6. **Model Training & Evaluation** — Four classifiers trained and compared using confusion matrices and accuracy scores

---

## Models Used

| Model                  | Key Parameters                           |
|------------------------|------------------------------------------|
| Logistic Regression    | Default                                  |
| K-Nearest Neighbors    | `n_neighbors=15`                         |
| Support Vector Machine | `kernel='rbf'`                           |
| Random Forest          | `n_estimators=30`, `criterion='entropy'` |

---

## Results

| Model                  | Accuracy |
|------------------------|----------|
| Logistic Regression    | 79%      |
| KNN (k=15)             | 72%      |
| SVM (RBF kernel)       | 81%      |
| **Random Forest**      | **82%**  |

✅ **Random Forest achieved the best accuracy at 82%**, using entropy criterion with 30 estimators.

Each model was evaluated using:
- Confusion Matrix (visualized as a heatmap)
- Accuracy Score

---

## Technologies Used

- **Python 3**
- **NumPy** — Numerical operations
- **Pandas** — Data loading and manipulation
- **Seaborn** — Data visualization
- **Scikit-learn** — ML models and evaluation metrics

---

## How to Run

1. **Clone the repository**
```bash
git clone https://github.com/Sravyagoli/Loan-Amount-Prediction.git
cd Loan-Amount-Prediction
```

2. **Install dependencies**
```bash
pip install numpy pandas seaborn scikit-learn
```

3. **Add the dataset**
Place `train_u6lujuX_CVtuZ9i.csv` in the project directory

4. **Run the notebook**
Open `Loan_Amount_Prediction.ipynb` in Jupyter Notebook or Google Colab and run all cells

---

## Future Improvements

- Apply `StandardScaler` to improve KNN and SVM performance
- Use Stratified K-Fold Cross-Validation for more robust evaluation
- Explore SMOTE to handle class imbalance
- Add feature importance visualization for Random Forest
- Try XGBoost and compare against current best model
