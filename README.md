# Predicting Patient Test Results Using Random Forest Classification

## Project Overview

This project explores the application of Machine Learning techniques to predict patient test result categories using healthcare-related demographic, admission, insurance, medication, and billing information.

The project follows a complete end-to-end Machine Learning workflow, including data cleaning, exploratory data analysis, feature engineering, preprocessing, baseline model development, Random Forest classification, hyperparameter tuning, and feature importance analysis.

The primary objective is to evaluate whether patient administrative and demographic information can be used to predict healthcare test outcomes and identify the most influential factors affecting predictions.

---

## Important Note About the Dataset

This dataset is a **synthetic healthcare dataset** created for educational, analytical, and machine learning practice purposes.

The dataset does **not represent real patients**, real hospitals, or actual medical records.

As a result:

* Results should not be interpreted as clinically meaningful.
* Model performance should not be considered representative of real-world healthcare systems.
* The project is intended for demonstrating data science and machine learning workflows.

---

## Dataset Information

### Source

Healthcare Dataset from Kaggle:

https://www.kaggle.com/datasets/prasad22/healthcare-dataset

### Dataset Summary

| Metric          | Value                      |
| --------------- | -------------------------- |
| Records         | 55,500                     |
| Features        | 15                         |
| Target Variable | Test Results               |
| Problem Type    | Multi-Class Classification |

### Target Classes

| Class        |
| ------------ |
| Abnormal     |
| Normal       |
| Inconclusive |

### Target Distribution

| Class        | Count  |
| ------------ | ------ |
| Abnormal     | 18,437 |
| Normal       | 18,331 |
| Inconclusive | 18,198 |

The target variable is well balanced across all classes.

---

## Business Objective

The objective of this project is to investigate whether demographic, admission, insurance, medication, and billing-related variables can be used to predict patient test result categories.

The project demonstrates how classification models can be developed and evaluated within a healthcare analytics context.

---

## Project Structure

```text
healthcare-random-forest-classification/

│
├── data/
│   ├── raw/
│   │   └── healthcare_dataset.csv
│   │
│   └── processed/
│       ├── cleaned_data.csv
│       ├── featured_data.csv
│       └── final_data.csv
│
├── notebooks/
│   ├── 01_data_understanding_and_cleaning.ipynb
│   ├── 02_eda_and_feature_engineering.ipynb
│   ├── 03_preprocessing_and_baseline_models.ipynb
│   ├── 04_random_forest_model.ipynb
│   └── 05_hyperparameter_tuning_and_feature_importance.ipynb
│
├── reports/
│   └── figures/
│
├── README.md
├── requirements.txt
└── .gitignore
```

---

## Data Cleaning

### Steps Performed

* Loaded and inspected dataset
* Checked data types
* Checked missing values
* Removed duplicate records
* Examined target variable distribution

### Feature Engineering

Created a new feature:

```python
Length_of_Stay
```

using:

```python
Discharge Date - Date of Admission
```

### Removed Features

The following columns were removed before modeling:

```text
Name
Doctor
Hospital
Date of Admission
Discharge Date
```

Reasons:

* High-cardinality features
* Potential data leakage
* Limited predictive value
* Excessive dimensionality after one-hot encoding

---

## Exploratory Data Analysis

EDA was conducted to understand:

* Patient age distribution
* Gender distribution
* Medical condition distribution
* Admission type distribution
* Insurance provider distribution
* Billing amount distribution
* Target class distribution
* Correlation among numerical variables

---

## Data Preprocessing

### Target Encoding

Label Encoding was applied to:

```text
Test Results
```

### Categorical Encoding

One-Hot Encoding was applied to:

```text
Gender
Blood Type
Medical Condition
Insurance Provider
Admission Type
Medication
```

### Train-Test Split

```python
test_size = 0.20
random_state = 42
stratify = y
```

---

## Baseline Models

### Logistic Regression

| Metric   | Value  |
| -------- | ------ |
| Accuracy | 33.33% |

### Decision Tree Classifier

| Metric   | Value  |
| -------- | ------ |
| Accuracy | 41.55% |

---

## Random Forest Classification

### Base Random Forest

| Metric   | Value  |
| -------- | ------ |
| Accuracy | 42.79% |

### Hyperparameter Tuning

GridSearchCV was used to optimize:

```python
n_estimators
max_depth
min_samples_split
min_samples_leaf
```

### Tuned Random Forest

| Metric   | Value  |
| -------- | ------ |
| Accuracy | 43.49% |

---

## Classification Performance

| Class        | Precision | Recall | F1-Score |
| ------------ | --------- | ------ | -------- |
| Abnormal     | 0.44      | 0.45   | 0.44     |
| Inconclusive | 0.44      | 0.42   | 0.43     |
| Normal       | 0.43      | 0.43   | 0.43     |

### Overall Metrics

| Metric              | Value  |
| ------------------- | ------ |
| Accuracy            | 43.49% |
| Macro Average F1    | 0.43   |
| Weighted Average F1 | 0.43   |

---

## Model Comparison

| Model               | Accuracy |
| ------------------- | -------- |
| Logistic Regression | 33.33%   |
| Decision Tree       | 41.55%   |
| Random Forest       | 42.79%   |
| Tuned Random Forest | 43.49%   |

The Tuned Random Forest model achieved the best overall performance and was selected as the final model.

---

## Feature Importance

Top features identified by the Random Forest model:

| Feature                  | Importance |
| ------------------------ | ---------- |
| Billing Amount           | 0.175      |
| Room Number              | 0.170      |
| Age                      | 0.148      |
| Length of Stay           | 0.135      |
| Gender_Male              | 0.027      |
| Admission Type_Emergency | 0.023      |
| Admission Type_Urgent    | 0.022      |

---

## Key Findings

* Random Forest outperformed both Logistic Regression and Decision Tree models.
* Hyperparameter tuning improved performance from 42.79% to 43.49%.
* Billing Amount, Room Number, Age, and Length of Stay were the most influential features.
* The relatively low predictive performance indicates limited predictive signal within the available variables.
* Administrative and demographic variables alone are insufficient for highly accurate prediction of patient test outcomes.

---

## Limitations

Several factors likely contributed to the modest model performance:

* The dataset is synthetic rather than real-world clinical data.
* Features primarily represent administrative and demographic information.
* No laboratory measurements were available.
* No vital signs or clinical observations were included.
* Significant overlap exists between target classes.
* Important medical predictors are absent from the dataset.

---

## Future Improvements

Potential enhancements include:

* XGBoost Classification
* LightGBM
* CatBoost
* Ensemble Learning
* SHAP Explainability
* Cross-Validation Optimization
* Model Deployment using Streamlit
* Real-world Healthcare Data Integration

---

## Technologies Used

* Python
* Pandas
* NumPy
* Matplotlib
* Seaborn
* Scikit-Learn
* Jupyter Notebook
* Git
* GitHub

---

## Skills Demonstrated

* Data Cleaning
* Exploratory Data Analysis
* Feature Engineering
* One-Hot Encoding
* Label Encoding
* Classification Modeling
* Random Forest Classification
* Hyperparameter Tuning
* Feature Importance Analysis
* Model Evaluation
* Git Version Control
* GitHub Project Management

---

## Author

**Muhammed Dhanish K**

M.Sc. Applied Statistics and Data Analytics


GitHub:
https://github.com/dhanishmohd1136
