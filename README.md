# Loan-Prediction-Model-AIML-
🚀 Transforming the Loan Approval Process in Sri Lanka with Machine Learning


# Smart Loan Eligibility Prediction System

An end-to-end Machine Learning solution designed to automate and accelerate the credit evaluation process, specifically addressing real-world operational inefficiencies in retail banking.

## 📌 Project Overview & Context

In traditional banking ecosystems—and specifically within **Sri Lanka**—securing a bank loan is often a highly time-consuming, manual, and tedious process. Applicants face extensive waiting times, manual paperwork verification, and prolonged decision cycles. For busy individuals, especially entrepreneurs and small business owners, these delays represent significant operational bottlenecks.

This project introduces an automated **Loan Eligibility Prediction Model** that instantly evaluates an applicant's financial and demographic indicators to predict loan approval. Developed as a core assignment for the **Artificial Intelligence & Machine Learning (IT2011)** module during Year 2, Semester 1 at SLIIT, this system utilizes a robust machine learning pipeline to deliver fast, objective, and accurate credit decisions.

---

## 🛠️ Machine Learning Pipeline Architecture

To guarantee reproducible, reliable, and leak-free performance, the entire workflow is enclosed within a scikit-learn pipeline object (`Imputation` ➡️ `Encoding` ➡️ `Scaling` ➡️ `Estimator`).

### 1. Preprocessing & EDA
* **Data Cleaning & Imputation:** Inspected missingness patterns and recorded column-level issues to guide safe imputation workflows.
* **Outlier Treatment:** Detected extreme entries using the Interquartile Range (IQR) rule ($Q1 - 1.5 \times IQR$ to $Q3 + 1.5 \times IQR$). Heavy right-skewed variables (such as income) were stabilized via log-transformations or winsorization.
* **Categorical Encoding:** Applied **Label Encoding** for binary parameters (e.g., gender, previous defaults) and **One-Hot Encoding** for multi-class nominal features (e.g., home ownership, education levels, loan intent) inside the pipeline to completely isolate validation folds.
* **Feature Scaling:** Configured `StandardScaler` to generate zero-mean, unit-variance distributions for distance-based and linear classifiers (Logistic Regression, SVM), while bypassing scaling steps for tree-based models to respect their scale-invariant nature.
* **Class Imbalance Mitigation:** Accounted for historical class imbalances using training-fold-only resampling (SMOTE) and adjusted internal estimator class weights.

### 2. Feature Set (14 Main Attributes)

The model evaluates an applicant's profile based on the following attributes:

| Attribute Name | Data Type | Description |
| :--- | :--- | :--- |
| `loan_status` | Binary (Target) | 1 = Approved, 0 = Rejected |
| `person_age` | Numeric | Age of the loan applicant |
| `person_gender` | Categorical | Gender identity of the applicant |
| `person_education` | Categorical | Highest educational qualification |
| `person_income` | Numeric | Annual income of the applicant |
| `person_emp_exp` | Numeric | Employment experience in years |
| `person_home_ownership` | Categorical | Housing status (Rent, Own, Mortgage, etc.) |
| `loan_intent` | Categorical | Purpose of the loan request |
| `loan_int_rate` | Numeric | Interest rate applicable to the loan |
| `loan_percent_income` | Numeric | Loan amount expressed as a ratio of annual income |
| `cb_person_cred_hist_length` | Numeric | Length of credit history in years |
| `credit_score` | Numeric | Quantified credit rating score |
| `previous_loan_defaults_on_file` | Binary | Historical default record indicator (Y/N) |

---

## 📊 Model Evaluation & Comparison

We trained, hyperparameter-tuned, and benchmarked **6 different machine learning models** using a stratified 80/20 train/test split combined with Stratified 5-Fold Cross-Validation. 

### Performance Summary Table

| Model Classifier | Accuracy | Precision | Recall (Sensitivity) | F1-Score |
| :--- | :---: | :---: | :---: | :---: |
| **Random Forest** | **0.910500** | **0.915633** | **0.904803** | **0.910186** |
| Decision Tree | 0.895071 | 0.875169 | 0.922189 | 0.898064 |
| MLP Neural Network | 0.889071 | 0.903664 | 0.871598 | 0.887341 |
| Support Vector Machine (SVM) | 0.887929 | 0.908396 | 0.863474 | 0.885366 |
| Logistic Regression | 0.879214 | 0.912996 | 0.838963 | 0.874415 |
| K-Nearest Neighbors (KNN) | 0.875286 | 0.887973 | 0.859627 | 0.873570 |

### 🏆 Key Selection & Insights
* **The Winner:** The **Random Forest** algorithm demonstrated the most balanced, robust, and reliable classification results with an overall accuracy of **91.05%** and an F1-score of **0.9102**.
* **Alternative Observation:** While the standalone *Decision Tree* achieved a higher raw Recall rate (0.9222), it suffered from a lower precision rate, marking Random Forest as the mathematically optimal architecture for deployment.
* **Explainability:** Global feature importance scores and local **SHAP (SHapley Additive exPlanations)** values were incorporated to make predictions fully transparent and interpretable for human audit tracks.

---

## ⚖️ Ethical Considerations & Responsible AI

Automated scoring algorithms run the inherent risk of encoding or amplifying historical bias present within training datasets. To combat this, the platform integrates:
1. **Bias Evaluation:** Continuous parity checks via statistical measures like *Demographic Parity* and *Equal Opportunity* targeting sensitive attributes (age groups, gender).
2. **Human-in-the-Loop Oversight:** Integrated manual fallback mechanisms and review workflows for marginal or high-impact decisions.
3. **Transparency Documentation:** Implemented comprehensive model cards highlighting system data sources, operational limits, and intended business constraints.

---

## 👥 Group Members & Contributors (Group: 2025-Y2-S1-MLB-B12G2-08)

This project was successfully researched, designed, and executed by our team at the **Sri Lanka Institute of Information Technology (SLIIT)**:

| Student ID | Name |
| :---: | :--- |
| **IT24103504** | **Yunidu E.D.P** |
| **IT24103569** | **Wanigasekara W.M.S.N.M** |
| **IT24103535** | **Sawandi T.G.A** |
| **IT24103555** | **Senan R.A.D.T** |
| **IT24103517** | **Abesundara N. S** |
| **IT24103554** | **Perera K.V. N** |

---
*Developed as part of the Artificial Intelligence and Machine Learning - IT2011 Module (Year 2, Semester 1).*
