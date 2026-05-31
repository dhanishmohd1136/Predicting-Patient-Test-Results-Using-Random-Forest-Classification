# Predicting Patient Test Results Using Random Forest Classification

## Project Overview

This project applies Machine Learning techniques to predict patient test outcomes using healthcare-related demographic, clinical, and admission information.

The objective is to build a classification model that can assist healthcare organizations in identifying patterns associated with patient test results and support data-driven decision making.

The project follows a complete Machine Learning workflow including:

- Data Understanding
- Data Cleaning
- Exploratory Data Analysis (EDA)
- Feature Engineering
- Data Preprocessing
- Baseline Model Development
- Random Forest Classification
- Hyperparameter Tuning
- Feature Importance Analysis
- Model Evaluation

---

## Dataset

**Source:**

https://www.kaggle.com/datasets/prasad22/healthcare-dataset

### Dataset Summary

| Metric | Value |
|----------|----------|
| Records | 55,500 |
| Features | 15 |
| Target Variable | Test Results |
| Problem Type | Multi-Class Classification |

### Target Classes

| Class |
|---------|
| Abnormal |
| Normal |
| Inconclusive |

Target distribution is approximately balanced across all three classes.

---

## Business Problem

Healthcare providers generate large volumes of patient information during admission and treatment.

Predicting patient test outcomes can help:

- Improve patient monitoring
- Support clinical decision making
- Allocate healthcare resources efficiently
- Identify high-risk cases earlier

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
│   ├── 05_hyperparameter_tuning_and_feature_importance.ipynb
│   └── 06_advanced_random_forest_techniques.ipynb
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

### Duplicate Removal

Duplicate records were identified and removed.

### Feature Engineering

Created:

```python
Length_of_Stay
```

using:

```python
Discharge Date - Date of Admission
```

### Removed Features

The following features were excluded to prevent data leakage and high-cardinality encoding issues:

```text
Name
Doctor
Hospital
Date of Admission
Discharge Date
```

---

## Exploratory Data Analysis

EDA was performed to understand:

- Age distribution
- Gender distribution
- Medical conditions
- Admission types
- Insurance providers
- Billing amount distribution
- Target variable distribution

---

## Data Preprocessing

### Target Encoding

```python
LabelEncoder()
```

used for:

```text
Test Results
```

### Categorical Encoding

```python
pd.get_dummies()
```

used for:

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

| Metric | Value |
|----------|----------|
| Accuracy | 0.333 |

### Decision Tree Classifier

| Metric | Value |
|----------|----------|
| Accuracy | 0.415 |

### Baseline Comparison

| Model | Accuracy |
|---------|---------|
| Logistic Regression | 0.333 |
| Decision Tree | 0.415 |

---

## Random Forest Classification

### Base Model

```python
RandomForestClassifier(
    random_state=42
)
```

### Base Model Accuracy

| Model | Accuracy |
|---------|---------|
| Random Forest | 0.428 |

---

## Hyperparameter Tuning

### GridSearchCV

Parameters tuned:

```python
{
    "n_estimators":[100,200,300],
    "max_depth":[5,10,20,None],
    "min_samples_split":[2,5,10],
    "min_samples_leaf":[1,2,4]
}
```

### Best Parameters

```python
{
    'max_depth': None,
    'min_samples_leaf': 2,
    'min_samples_split': 2,
    'n_estimators': 300
}
```

---

## Tuned Random Forest Performance

| Metric | Value |
|----------|----------|
| Accuracy | 0.435 |

### Classification Report

| Class | Precision | Recall | F1-Score |
|---------|---------|---------|---------|
| Abnormal | 0.44 | 0.45 | 0.44 |
| Inconclusive | 0.44 | 0.42 | 0.43 |
| Normal | 0.43 | 0.43 | 0.43 |

### Overall Metrics

| Metric | Value |
|----------|----------|
| Accuracy | 0.435 |
| Macro Avg F1 | 0.43 |
| Weighted Avg F1 | 0.43 |

---

## Feature Importance

Top features identified by Random Forest:

| Feature | Importance |
|----------|----------|
| Billing Amount | 0.175 |
| Room Number | 0.170 |
| Age | 0.148 |
| Length_of_Stay | 0.135 |
| Gender_Male | 0.027 |
| Admission Type_Emergency | 0.023 |
| Admission Type_Urgent | 0.022 |

### Key Insight

Patient demographics and hospital-related variables such as:

- Billing Amount
- Room Number
- Age
- Length of Stay

contributed most to prediction performance.

---

## Model Comparison

| Model | Accuracy |
|---------|---------|
| Logistic Regression | 0.333 |
| Decision Tree | 0.415 |
| Random Forest | 0.428 |
| Tuned Random Forest | 0.435 |

Random Forest achieved the best overall performance among the evaluated models.

---

## Challenges

### Multi-Class Classification

The target variable contains three classes with overlapping characteristics.

### Limited Predictive Signal

The dataset primarily contains administrative and demographic information rather than detailed clinical measurements.

### Feature Leakage Prevention# Predicting Patient Test Results Using Random Forest Classification

## Project Overview

This project applies Machine Learning techniques to predict patient test outcomes using healthcare-related demographic, clinical, and admission information.

The objective is to build a classification model that can assist healthcare organizations in identifying patterns associated with patient test results and support data-driven decision making.

The project follows a complete Machine Learning workflow including:

- Data Understanding
- Data Cleaning
- Exploratory Data Analysis (EDA)
- Feature Engineering
- Data Preprocessing
- Baseline Model Development
- Random Forest Classification
- Hyperparameter Tuning
- Feature Importance Analysis
- Model Evaluation

---

## Dataset

**Source:**

https://www.kaggle.com/datasets/prasad22/healthcare-dataset

### Dataset Summary

| Metric | Value |
|----------|----------|
| Records | 55,500 |
| Features | 15 |
| Target Variable | Test Results |
| Problem Type | Multi-Class Classification |

### Target Classes

| Class |
|---------|
| Abnormal |
| Normal |
| Inconclusive |

Target distribution is approximately balanced across all three classes.

---

## Business Problem

Healthcare providers generate large volumes of patient information during admission and treatment.

Predicting patient test outcomes can help:

- Improve patient monitoring
- Support clinical decision making
- Allocate healthcare resources efficiently
- Identify high-risk cases earlier

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
│   ├── 05_hyperparameter_tuning_and_feature_importance.ipynb
│   └── 06_advanced_random_forest_techniques.ipynb
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

### Duplicate Removal

Duplicate records were identified and removed.

### Feature Engineering

Created:

```python
Length_of_Stay
```

using:

```python
Discharge Date - Date of Admission
```

### Removed Features

The following features were excluded to prevent data leakage and high-cardinality encoding issues:

```text
Name
Doctor
Hospital
Date of Admission
Discharge Date
```

---

## Exploratory Data Analysis

EDA was performed to understand:

- Age distribution
- Gender distribution
- Medical conditions
- Admission types
- Insurance providers
- Billing amount distribution
- Target variable distribution

---

## Data Preprocessing

### Target Encoding

```python
LabelEncoder()
```

used for:

```text
Test Results
```

### Categorical Encoding

```python
pd.get_dummies()
```

used for:

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

| Metric | Value |
|----------|----------|
| Accuracy | 0.333 |

### Decision Tree Classifier

| Metric | Value |
|----------|----------|
| Accuracy | 0.415 |

### Baseline Comparison

| Model | Accuracy |
|---------|---------|
| Logistic Regression | 0.333 |
| Decision Tree | 0.415 |

---

## Random Forest Classification

### Base Model

```python
RandomForestClassifier(
    random_state=42
)
```

### Base Model Accuracy

| Model | Accuracy |
|---------|---------|
| Random Forest | 0.428 |

---

## Hyperparameter Tuning

### GridSearchCV

Parameters tuned:

```python
{
    "n_estimators":[100,200,300],
    "max_depth":[5,10,20,None],
    "min_samples_split":[2,5,10],
    "min_samples_leaf":[1,2,4]
}
```

### Best Parameters

```python
{
    'max_depth': None,
    'min_samples_leaf': 2,
    'min_samples_split': 2,
    'n_estimators': 300
}
```

---

## Tuned Random Forest Performance

| Metric | Value |
|----------|----------|
| Accuracy | 0.435 |

### Classification Report

| Class | Precision | Recall | F1-Score |
|---------|---------|---------|---------|
| Abnormal | 0.44 | 0.45 | 0.44 |
| Inconclusive | 0.44 | 0.42 | 0.43 |
| Normal | 0.43 | 0.43 | 0.43 |

### Overall Metrics

| Metric | Value |
|----------|----------|
| Accuracy | 0.435 |
| Macro Avg F1 | 0.43 |
| Weighted Avg F1 | 0.43 |

---

## Feature Importance

Top features identified by Random Forest:

| Feature | Importance |
|----------|----------|
| Billing Amount | 0.175 |
| Room Number | 0.170 |
| Age | 0.148 |
| Length_of_Stay | 0.135 |
| Gender_Male | 0.027 |
| Admission Type_Emergency | 0.023 |
| Admission Type_Urgent | 0.022 |

### Key Insight

Patient demographics and hospital-related variables such as:

- Billing Amount
- Room Number
- Age
- Length of Stay

contributed most to prediction performance.

---

## Model Comparison

| Model | Accuracy |
|---------|---------|
| Logistic Regression | 0.333 |
| Decision Tree | 0.415 |
| Random Forest | 0.428 |
| Tuned Random Forest | 0.435 |

Random Forest achieved the best overall performance among the evaluated models.

---

## Challenges

### Multi-Class Classification

The target variable contains three classes with overlapping characteristics.

### Limited Predictive Signal

The dataset primarily contains administrative and demographic information rather than detailed clinical measurements.

### Feature Leakage Prevention

Several high-cardinality identifier features were removed to improve generalization.

---

## Future Improvements

- XGBoost Classifier
- LightGBM
- CatBoost
- SHAP Explainability
- Cross Validation Optimization
- Ensemble Learning Approaches
- Streamlit Deployment
- Healthcare Dashboard Development

---

## Technologies Used

- Python
- Pandas
- NumPy
- Matplotlib
- Seaborn
- Scikit-Learn
- Jupyter Notebook

---

## Author

**Muhammed Dhanish K**

M.Sc. Applied Statistics and Data Analytics

AI / ML Engineer | Data Analyst | Data Science Enthusiast

GitHub:
https://github.com/dhanishmohd1136


Several high-cardinality identifier features were removed to improve generalization.

---

## Future Improvements

- XGBoost Classifier
- LightGBM
- CatBoost
- SHAP Explainability
- Cross Validation Optimization
- Ensemble Learning Approaches
- Streamlit Deployment
- Healthcare Dashboard Development

---

## Technologies Used

- Python
- Pandas
- NumPy
- Matplotlib
- Seaborn
- Scikit-Learn
- Jupyter Notebook

---

## Author

**Muhammed Dhanish K**

M.Sc. Applied Statistics and Data Analytics

AI / ML Engineer | Data Analyst | Data Science Enthusiast

GitHub:
https://github.com/dhanishmohd1136
