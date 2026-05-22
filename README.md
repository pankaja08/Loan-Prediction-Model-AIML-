# Loan-Prediction-Model-AIML-
🚀 Transforming the Loan Approval Process in Sri Lanka with Machine Learning


An end-to-end Machine Learning solution designed to automate and accelerate the credit evaluation process, specifically addressing real-world operational inefficiencies in retail banking.

## 📌 Project Overview & Context

In traditional banking ecosystems—and specifically within **Sri Lanka**—securing a bank loan is often a highly time-consuming, manual, and tedious process. Applicants face extensive waiting times, manual paperwork verification, and prolonged decision cycles. For busy individuals, especially entrepreneurs and small business owners, these delays represent significant operational bottlenecks.

This project introduces an automated **Loan Eligibility Prediction Model** that instantly evaluates an applicant's financial and demographic indicators to predict loan approval. Developed as a core assignment for the **Artificial Intelligence & Machine Learning (IT2011)** module during Year 2, Semester 1 at SLIIT, this system utilizes a robust machine learning pipeline to deliver fast, objective, and accurate credit decisions.

---

## 🛠️ Machine Learning Pipeline Architecture

To guarantee reproducible, reliable, and leak-free performance, the entire workflow is enclosed within a scikit-learn pipeline object (`Imputation` ➡️ `Encoding` ➡️ `Scaling` ➡️ `Estimator`).

### 1. Preprocessing & EDA
* [cite_start]**Data Cleaning & Imputation:** Inspected missingness patterns and recorded column-level issues to guide safe imputation workflows[cite: 33].
* [cite_start]**Outlier Treatment:** Detected extreme entries using the Interquartile Range (IQR) rule ($Q1 - 1.5 \times IQR$ to $Q3 + 1.5 \times IQR$)[cite: 35]. [cite_start]Heavy right-skewed variables (such as income) were stabilized via log-transformations or winsorization[cite: 36].
* [cite_start]**Categorical Encoding:** Applied **Label Encoding** for binary parameters (e.g., gender, previous defaults) [cite: 39] [cite_start]and **One-Hot Encoding** for multi-class nominal features (e.g., home ownership, education levels, loan intent) [cite: 40] [cite_start]inside the pipeline to completely isolate validation folds[cite: 41].
* [cite_start]**Feature Scaling:** Configured `StandardScaler` to generate zero-mean, unit-variance distributions for distance-based and linear classifiers (Logistic Regression, SVM) [cite: 43][cite_start], while bypassing scaling steps for tree-based models to respect their scale-invariant nature[cite: 44, 65].
* [cite_start]**Class Imbalance Mitigation:** Accounted for historical class imbalances using training-fold-only resampling (SMOTE) and adjusted internal estimator class weights[cite: 66].

### 2. Feature Set (14 Main Attributes)

[cite_start]The model evaluates an applicant's profile based on the following attributes[cite: 22]:

| Attribute Name | Data Type | Description |
| :--- | :--- | :--- |
| `loan_status` | Binary (Target) | [cite_start]1 = Approved, 0 = Rejected [cite: 23, 24, 26] |
| `person_age` | Numeric | [cite_start]Age of the loan applicant [cite: 22] |
| `person_gender` | Categorical | [cite_start]Gender identity of the applicant [cite: 22] |
| `person_education` | Categorical | [cite_start]Highest educational qualification [cite: 22] |
| `person_income` | Numeric | [cite_start]Annual income of the applicant [cite: 22] |
| `person_emp_exp` | Numeric | [cite_start]Employment experience in years [cite: 22] |
| `person_home_ownership` | Categorical | [cite_start]Housing status (Rent, Own, Mortgage, etc.) [cite: 22] |
| `loan_intent` | Categorical | [cite_start]Purpose of the loan request [cite: 22] |
| `loan_int_rate` | Numeric | [cite_start]Interest rate applicable to the loan [cite: 22] |
| `loan_percent_income` | Numeric | [cite_start]Loan amount expressed as a ratio of annual income [cite: 22] |
| `cb_person_cred_hist_length`| Numeric | [cite_start]Length of credit history in years [cite: 22] |
| `credit_score` | Numeric | [cite_start]Quantified credit rating score [cite: 22] |
| `previous_loan_defaults_on_file`| Binary | [cite_start]Historical default record indicator (Y/N) [cite: 22] |

---

## 📊 Model Evaluation & Comparison

[cite_start]We trained, hyperparameter-tuned, and benchmarked **6 different machine learning models** using a stratified 80/20 train/test split combined with Stratified 5-Fold Cross-Validation[cite: 56, 77]. 

### [cite_start]Performance Summary Table [cite: 87]

| Model Classifier | Accuracy | Precision | Recall (Sensitivity) | F1-Score |
| :--- | :---: | :---: | :---: | :---: |
| **Random Forest** | **0.910500** | **0.915633** | **0.904803** | **0.910186** |
| Decision Tree | 0.895071 | 0.875169 | 0.922189 | 0.898064 |
| MLP Neural Network | 0.889071 | 0.903664 | 0.871598 | 0.887341 |
| Support Vector Machine (SVM) | 0.887929 | 0.908396 | 0.863474 | 0.885366 |
| Logistic Regression | 0.879214 | 0.912996 | 0.838963 | 0.874415 |
| K-Nearest Neighbors (KNN) | 0.875286 | 0.887973 | 0.859627 | 0.873570 |

### 🏆 Key Selection & Insights
* [cite_start]**The Winner:** The **Random Forest** algorithm demonstrated the most balanced, robust, and reliable classification results with an overall accuracy of **91.05%** and an F1-score of **0.9102**[cite: 89].
* [cite_start]**Alternative Observation:** While the standalone *Decision Tree* achieved a higher raw Recall rate (0.9222), it suffered from a lower precision rate [cite: 90][cite_start], marking Random Forest as the mathematically optimal architecture for deployment[cite: 93].
* [cite_start]**Explainability:** Global feature importance scores and local **SHAP (SHapley Additive exPlanations)** values were incorporated to make predictions fully transparent and interpretable for human audit tracks[cite: 71, 72].

---

## ⚖️ Ethical Considerations & Responsible AI

[cite_start]Automated scoring algorithms run the inherent risk of encoding or amplifying historical bias present within training datasets[cite: 8]. To combat this, the platform integrates:
1. [cite_start]**Bias Evaluation:** Continuous parity checks via statistical measures like *Demographic Parity* and *Equal Opportunity* targeting sensitive attributes (age groups, gender)[cite: 16, 98].
2. [cite_start]**Human-in-the-Loop Oversight:** Integrated manual fallback mechanisms and review workflows for marginal or high-impact decisions[cite: 100].
3. [cite_start]**Transparency Documentation:** Implemented comprehensive model cards highlighting system data sources, operational limits, and intended business constraints[cite: 73, 99].

---

## 👥 Group Members & Contributors (Group: 2025-Y2-S1-MLB-B12G2-08)

[cite_start]This project was successfully researched, designed, and executed by our team at the **Sri Lanka Institute of Information Technology (SLIIT)**[cite: 1, 4]:

| Student ID | Name |
| :---: | :--- |
| **IT24103504** | [cite_start]**Yunidu E.D.P** [cite: 5] |
| **IT24103569** | [cite_start]**Wanigasekara W.M.S.N.M** [cite: 5] |
| **IT24103535** | [cite_start]**Sawandi T.G.A** [cite: 5] |
| **IT24103555** | [cite_start]**Senan R.A.D.T** [cite: 5] |
| **IT24103517** | [cite_start]**Abesundara N. S** [cite: 5] |
| **IT24103554** | **Perera K.V. [cite_start]N** [cite: 5] |

---
[cite_start]*Developed as part of the Artificial Intelligence and Machine Learning - IT2011 Module (Year 2, Semester 1)[cite: 3].*
