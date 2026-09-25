# Clinical Statistical Analysis of Heart Disease

## Overview

Statistical analysis of **50,000 synthetic patient records** to investigate demographic, lifestyle, and clinical factors associated with heart disease.

The project combines **exploratory data analysis, hypothesis testing, effect-size analysis, and multivariable logistic regression** to distinguish statistically meaningful associations from weaker relationships.

> This dataset is synthetic and the findings should not be interpreted as clinical evidence.

## Data

* **50,000 records, 21 variables**
* **Target:** `Heart_Disease`
* **Predictors:** demographic, lifestyle, clinical, and medical-history variables
* **Outcome:** 26,827 without heart disease; 23,173 with heart disease

Missing values were assessed during preprocessing, categorical variables were encoded, and selected variables were excluded from the final modelling dataset.

## Analysis

The analysis included:

* Exploratory Data Analysis
* Independent-group hypothesis testing
* Chi-square tests
* Cohen's d
* Cramér's V
* Multivariable logistic regression
* Odds ratios and 95% confidence intervals
* Variance Inflation Factor (VIF)
* Likelihood Ratio Test
* ROC-AUC and classification metrics

## Key Findings

Age and total cholesterol showed substantial differences between participants with and without heart disease:

| Variable          | No Heart Disease | Heart Disease |      Effect Size |
| ----------------- | ---------------: | ------------: | ---------------: |
| Age               |            49.36 |         60.37 | Cohen's d = 0.82 |
| Total Cholesterol |           209.55 |        241.93 | Cohen's d = 0.81 |

Categorical analysis identified significant associations for:

* **Hypertension:** Cramér's V = 0.405
* **Previous Heart Attack:** Cramér's V = 0.240

Smoking showed negligible association in this dataset (Cramér's V = 0.002).

## Logistic Regression

A multivariable logistic regression model was used to estimate adjusted associations.

The strongest statistically significant predictors were:

| Predictor             | Odds Ratio | p-value |
| --------------------- | ---------: | ------: |
| Age                   |      1.106 |  <0.001 |
| Diabetes              |     27.212 |  <0.001 |
| Previous Heart Attack |     29.359 |  <0.001 |
| Total Cholesterol     |      1.034 |  <0.001 |

All predictor VIFs were below **1.33**, indicating no concerning multicollinearity.

## Model Performance

Using a stratified 80/20 train-test split:

| Metric    | Test Score |
| --------- | ---------: |
| ROC-AUC   |  **0.903** |
| Accuracy  | **81.65%** |
| Precision | **80.95%** |
| Recall    | **79.01%** |
| F1-score  | **79.97%** |

## Limitations

* The dataset is synthetic and may not represent real clinical populations.
* Statistical associations do not establish causality.
* `Previous_Heart_Attack` may overlap conceptually with the outcome.
* Missing `Alcohol_Intake` values were treated as `"No"`.
* The model was not externally validated.

## Tools

**Python · Pandas · NumPy · SciPy · Statsmodels · Scikit-learn · Matplotlib · Seaborn**
