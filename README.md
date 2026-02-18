# Predictive Modeling of Arrhythmic Complications Post-AMI

Machine learning project on a real-world cohort of 1,700 acute myocardial infarction (AMI) patients, aiming to predict in-hospital arrhythmic complications using routinely collected clinical and ECG-related variables.

## Project Summary

- Dataset: 1,700 AMI patients, 111 input variables (clinical, labs, ECG, therapies)
- Outcome: binary label indicating the occurrence of any arrhythmic complication during hospitalization
- Goal: compare interpretable vs non-interpretable ML models in terms of performance and explainability

## Methods

### Preprocessing
- Feature aggregation for sparse clinically-related categorical variables
- Missing data handling: remove features with >50% missingness, impute remaining missing values (median/mode)
- Outlier handling: Winsorization (IQR-based)
- Scaling: RobustScaler
- Class imbalance: SMOTE applied within training folds only (to prevent leakage)

### Feature Selection
- Unsupervised filtering: near-zero variance and correlation filtering
- Supervised filtering: Chi-squared for categorical features, LDA coefficients for numerical features

### Models
Evaluated models:
- Logistic Regression
- Decision Tree
- KNN
- Linear SVM
- Random Forest
- Gradient Boosting
- MLP (ANN)
- Soft-voting ensemble

Validation:
- stratified train/test split + stratified 10-fold cross-validation on training set
- performance metrics: AUC, precision, recall, F1-score, confusion matrix, ROC curve

Explainability:
- SHAP, permutation importance, and LIME for local explanations

## Results
Models achieved comparable moderate performance (AUC ~0.65–0.69; F1 ~0.36–0.41), suggesting data constraints as the main limiting factor rather than model complexity.
Consistently important predictors included rare ECG anomalies, age, lidocaine use, and markers of metabolic/inflammatory imbalance.

## Repository Contents

- `notebooks/code.ipynb`  
  End-to-end notebook: preprocessing, feature selection, model training, evaluation, and explainability.

- `docs/Report.pdf`  
  Full report (Abstract, Background, Methods, Results, Discussion, Conclusions, Bibliography).

- `docs/Slides.pptx`  
  Project presentation slides.

- `docs/Project_Specifications.pdf`  
  Course project specifications and evaluation criteria.


## Reproducibility Notes
Raw data are not included in this repository. The notebook is structured to be reproducible once the dataset is available locally.
