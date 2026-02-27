# Flu Shot Vaccine Prediction

This project predicts the likelihood of individuals receiving H1N1 and seasonal flu vaccines using machine learning models. The solution implements an ensemble approach with multiple gradient boosting algorithms and advanced feature engineering.

Overview

This is a binary classification problem that predicts:
- **H1N1 vaccine uptake** - Whether a respondent received the H1N1 flu vaccine
- **Seasonal vaccine uptake** - Whether a respondent received the seasonal flu vaccine

The models are trained on survey data containing demographic information, health behaviors, opinions about vaccines, and doctor recommendations.

Key Features

### Advanced Feature Engineering
- **Doctor recommendation interactions** - Combined effects of medical advice
- **Opinion-based features** - Risk perception and vaccine effectiveness beliefs
- **Behavioral patterns** - Protective vs. risky health behaviors
- **Demographic encoding** - Age groups, education levels, income categories
- **Health risk indicators** - Chronic conditions and insurance status

### Model Architecture
- **Multi-algorithm ensemble** with 6 different models per target:
  - LightGBM (2 variants)
  - XGBoost (2 variants)
  - CatBoost (2 variants)
- **Cross-validation** with 15 folds
- **Probability calibration** using isotonic regression
- **Optimized ensembling** via differential evolution

### Performance Metrics
- **ROC AUC Score** as primary evaluation metric
- **Log Loss** for probabilistic accuracy
- **Cross-validated** results to ensure robustness

StructureStructure

```
Flu_Shot/
├── Flu_shot.ipynb          # Main Jupyter notebook with full implementation
├── training_set_features.csv   # Training features (input data)
├── training_set_labels.csv     # Training labels (target variables)
├── test_set_features.csv       # Test features for prediction
├── submission.csv              # Final predictions output
├── README.md               # This file
└── .gitignore              # Git ignore rules
```

Requirements

### Python Packages
```
numpy
pandas
scikit-learn
matplotlib
lightgbm
xgboost
catboost
category-encoders
optuna
scipy
```

### Installation
```bash
pip install lightgbm catboost xgboost pandas numpy scikit-learn matplotlib category-encoders optuna scipy
```

Usage

1. **Prepare Data**: Place the following CSV files in the project directory:
   - `training_set_features.csv`
   - `training_set_labels.csv`
   - `test_set_features.csv`

2. **Run the Model**:
   Open and execute `Flu_shot.ipynb` in Jupyter Notebook or JupyterLab

3. **Output**: 
   - Results are displayed in the notebook
   - `submission.csv` file is generated with final predictions
   - ROC curves are visualized for model performance

Model Performance

The ensemble approach achieves state-of-the-art results through:
- **Feature-rich engineering** creating over 20 additional meaningful features
- **Multi-model diversity** reducing overfitting and improving generalization
- **Optimized weight selection** using evolutionary algorithms
- **Proper calibration** ensuring reliable probability estimates

Detailscal Details

### Encoding Strategy
- **Label Encoding** for categorical variables
- **Target Encoding** with smoothing
- **WOE Encoding** (Weight of Evidence) for logistic relationship capture

### Cross-Validation
- **Stratified 15-fold** to maintain label distribution
- **Seed-fixed** for reproducible results
- **Out-of-fold predictions** for unbiased evaluation

### Ensemble Optimization
- **Differential Evolution** algorithm for weight optimization
- **ROC AUC maximization** as objective function
- **Non-negative weight constraints** with normalization

Data Dictionary

Key features include:
- **Demographics**: age_group, education, income_poverty, marital_status
- **Health Behaviors**: behavioral_antiviral_meds, behavioral_wash_hands, etc.
- **Medical Opinions**: opinion_h1n1_risk, opinion_seas_vacc_effective, etc.
- **Doctor Recommendations**: doctor_recc_h1n1, doctor_recc_seasonal
- **Health Status**: chronic_med_condition, health_worker, health_insurance

Results

The final submission includes probability scores for:
- `h1n1_vaccine` - Likelihood of H1N1 vaccination (0-1)
- `seasonal_vaccine` - Likelihood of seasonal vaccination (0-1)

Models are evaluated on ROC AUC scores and cross-validated log loss to ensure robust performance.


This solution leverages:
- Gradient boosting best practices
- Advanced feature engineering techniques
- Ensemble learning principles
- Probability calibration methods
- Evolutionary optimization algorithms

---
**Author**: Prasad Huddar  
**Date**: February 2026
