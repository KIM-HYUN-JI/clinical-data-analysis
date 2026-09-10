# Clinical Data Analysis: 30-Day Readmission Prediction

A clinical data analysis and machine learning project using more than 100,000 hospital encounters to explore and predict 30-day hospital readmission.

This project demonstrates an end-to-end data analysis workflow including data quality assessment, exploratory data analysis, preprocessing, class-imbalance handling, predictive modeling, model evaluation, and interpretation.

## Objective

The goal of this analysis is to identify patterns associated with hospital readmission within 30 days and build an interpretable baseline prediction model.

The original readmission outcome was converted into a binary target:

- `<30` → 30-day readmission
- `>30` or `NO` → no 30-day readmission

## Dataset

**Diabetes 130-US Hospitals for Years 1999–2008**  
UCI Machine Learning Repository

- 101,766 hospital encounters
- Demographic, diagnostic, treatment, and hospitalization-related variables
- Binary prediction target: readmission within 30 days

Dataset source: UCI Machine Learning Repository, Dataset ID 296.

## Analysis Workflow

### 1. Data Quality Assessment
- Examined missing values across clinical variables
- Identified variables with extensive missingness
- Excluded high-missingness variables from baseline modeling

### 2. Exploratory Data Analysis
- Examined the distribution of 30-day readmission
- Identified substantial class imbalance
- Approximately 11.2% of encounters resulted in readmission within 30 days

### 3. Data Preprocessing
- Median imputation for numerical variables
- Most-frequent imputation for categorical variables
- Standardization of numerical features
- One-hot encoding of categorical features
- Stratified train/test split

### 4. Predictive Modeling
An interpretable Logistic Regression model was developed as a baseline classifier.

Class weighting was applied to account for the imbalanced outcome distribution.

### 5. Model Evaluation

The baseline model achieved:

- **ROC-AUC: 0.643**
- **Recall for 30-day readmission: 0.55**
- **Precision for 30-day readmission: 0.17**
- **F1-score for 30-day readmission: 0.26**

Because of class imbalance, model performance was evaluated using ROC-AUC, recall, precision, and F1-score rather than accuracy alone.

### 6. Model Interpretation
- Examined the confusion matrix
- Evaluated logistic regression coefficients
- Identified variables contributing most strongly to predicted readmission risk

## Key Takeaway

The analysis demonstrates that clinical prediction problems require more than maximizing accuracy. In an imbalanced clinical outcome, improving sensitivity to patients at risk can substantially increase false-positive predictions.

This trade-off should be considered when interpreting predictive models in healthcare settings.

## Tools

- Python
- pandas
- NumPy
- scikit-learn
- matplotlib
- seaborn
- Google Colab

## Repository Structure

```text
clinical-data-analysis/
├── notebooks/
│   └── clinical_readmission_analysis.ipynb
└── README.md

Limitations

This project is intended as a data-analysis portfolio demonstration rather than a clinically deployable prediction model.

The dataset is historical, several variables contain substantial missingness, and model performance may not generalize to contemporary clinical populations. Future work could include feature engineering, threshold optimization, calibration assessment, tree-based models, and external validation.

Data Source

Diabetes 130-US Hospitals for Years 1999–2008
UCI Machine Learning Repository
https://archive.ics.uci.edu/dataset/296/diabetes+130-us+hospitals+for+years+1999-2008
