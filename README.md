# Predicting Student Success: A Data Mining Approach to Retention in Higher Education

<p align="center">
  <img alt="Python" src="https://img.shields.io/badge/Python-3776AB?style=for-the-badge&logo=python&logoColor=white" />
  <img alt="pandas" src="https://img.shields.io/badge/pandas-150458?style=for-the-badge&logo=pandas&logoColor=white" />
  <img alt="NumPy" src="https://img.shields.io/badge/NumPy-013243?style=for-the-badge&logo=numpy&logoColor=white" />
  <img alt="scikit-learn" src="https://img.shields.io/badge/scikit--learn-F7931E?style=for-the-badge&logo=scikit-learn&logoColor=white" />
  <img alt="imbalanced-learn" src="https://img.shields.io/badge/imbalanced--learn-0C5FAF?style=for-the-badge&logo=python&logoColor=white" />
  <img alt="Jupyter" src="https://img.shields.io/badge/Jupyter-F37626?style=for-the-badge&logo=jupyter&logoColor=white" />
</p>

<p align="center">
  <b>Predicting student dropout risk using academic, financial, and demographic data to support proactive retention strategies in higher education.</b>
</p>

---

## Introduction

This project applies data mining and machine learning to predict student attrition in higher education. The goal is to identify students at risk of dropping out early enough for academic advisors and institutions to intervene effectively.

Using a dataset of 4,424 undergraduate records from the UCI Machine Learning Repository, the analysis examines academic performance, tuition status, scholarships, and demographic variables to model dropout risk.

---

## Project Overview

**Predicting Student Success: A Data Mining Approach to Retention in Higher Education** combines exploratory data analysis, feature engineering, class-imbalance handling, and predictive modeling to study student retention.

The project focuses on four research questions:

- Is first-semester academic performance a reliable early warning signal?
- Do financial factors such as tuition status and scholarship holding affect success?
- Do age and admission grades differentiate dropouts from graduates?
- Can a machine learning model predict at-risk students in real time?

The final workflow includes cleaning, encoding, scaling, SMOTE-ENN resampling, Decision Tree modeling, hyperparameter tuning, and probability calibration.

---

## Dataset Overview

The dataset includes 4,424 undergraduate students and 36 features across three major categories.

### Feature Groups

- Academic performance: enrolled units, evaluations, approved units, and grades.
- Socio-economic status: tuition status, scholarship status, unemployment rate, and GDP-related variables.
- Demographics: age at enrollment, gender, marital status, and displaced status.

### Target Variable

The target includes three student outcomes:

- Graduate.
- Dropout.
- Enrolled.

The modeling objective is to detect dropout risk and rank students by likelihood of attrition.

---

## Data Processing

The dataset was preprocessed to improve consistency and support modeling.

### Steps Performed

- Standardized column names.
- Engineered a first-semester success rate using approved units divided by enrolled units.
- Label encoded categorical variables.
- Standardized numerical variables with `StandardScaler`.
- Addressed class imbalance with `SMOTE-ENN`.

This preparation helped the model focus on meaningful retention patterns instead of being biased toward the majority class.

---

## Analysis Approach

The analysis was divided into two parts: exploratory diagnostics and predictive modeling.

### Exploratory Diagnostics

- Students with fewer than 50% approved units in the first semester were at critical risk.
- Late or missing tuition payments were strongly associated with lower success rates.
- Scholarship holders showed better retention outcomes.
- Admission grades were less informative than current university performance.

### Predictive Modeling

- A Decision Tree classifier was selected for interpretability.
- RandomizedSearchCV was used for hyperparameter tuning.
- The model was calibrated with sigmoid scaling to improve probability reliability.
- The decision threshold was adjusted to prioritize recall and catch more at-risk students.

---

## Results Summary

The final model achieved strong predictive ranking performance.

### Performance Metrics

- ROC AUC: 0.835
- Accuracy: 62.37%
- F1 Score: 60.67%

### Interpretation

- The model is effective at ranking dropout risk.
- First-semester approved units were one of the strongest predictors.
- Tuition payment status was a major signal of retention risk.
- Age at enrollment also contributed meaningfully.

### Top Drivers

The strongest features included:

1. Curricular Units 2nd Sem (Grade).
2. Curricular Units 1st Sem (Approved).
3. Age at Enrollment.

These results show that early academic momentum matters more than pre-admission history alone.

### ROC Curve

<p align="center">
  <img src="image_1.png" alt="ROC Curve" width="900" />
</p>

The ROC curves show that the model separates the three outcomes reasonably well, with Graduate performing strongest and Enrolled performing more weakly. This supports the use of a multi-class classification approach for student retention analysis.

---

## Key Figures

### RQ1: Academic Tipping Point

<p align="center">
  <img src="image_3.png" alt="Approved Units in 1st Semester by Final Outcome" width="900" />
</p>

The first-semester approved-units plot shows a clear separation between dropouts and graduates. Students approving fewer than 50% of enrolled units in the first semester are at immediate risk.

### RQ3: Demographic and Academic Preparation Profile

<p align="center">
  <img src="image_2.png" alt="Demographic and Academic Preparation Profile by Final Outcome" width="900" />
</p>

The violin plots suggest that dropouts tend to be older at enrollment, while admission grades are more similar across groups. This indicates that current performance and current circumstances matter more than pre-admission grades.

---

## Key Findings

- Dropout risk follows clear academic and financial patterns.
- First-semester performance is the strongest early warning signal.
- Tuition payment status is a major retention indicator.
- High school grades are not enough to predict retention.
- A calibrated machine learning model can support targeted intervention.

---

## Tech Stack

| Category | Tools |
|---|---|
| Language | Python |
| Data Handling | pandas, NumPy |
| Machine Learning | scikit-learn |
| Imbalanced Learning | imbalanced-learn |
| Visualization | Matplotlib, Seaborn |
| Environment | Jupyter Notebook, Google Colab |
| Outputs | Notebook, PDF report, PowerPoint presentation |

---

## Repository Structure

```bash
.
├── dropout_prediction_code.ipynb
├── dropout_prediction_report.pdf
├── Student_Dropout_Prediction_PPT.pptx
├── image_1.png
├── image_2.png
├── image_3.png
└── README.md
```

---

## Practical Use

This project can help universities identify students who may need support early in the semester. Instead of using generic retention outreach, advisors can focus tutoring, counseling, and financial support on students with the highest predicted risk.

---

## Future Improvements

- Compare the Decision Tree with Random Forest, XGBoost, and Logistic Regression.
- Add SHAP or permutation-based explainability.
- Test alternative threshold strategies.
- Evaluate fairness across student subgroups.
- Build an advisor dashboard for weekly risk monitoring.

---

## Acknowledgments

This project was developed using the UCI Student Academic Performance dataset and inspired by prior work in educational data mining and student success prediction.
