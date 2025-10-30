# Ensemble Regression for Substance Use Risk Prediction

Predictive modeling of drug use risk using personality traits, demographics, and substance use history from the UCI Drug Consumption dataset.

[![R](https://img.shields.io/badge/R-4.0+-blue.svg)](https://www.r-project.org/)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)

[Video Presentation](https://youtu.be/GkFWRQEywSI) | [Full Analysis](analysis/PredictingDrugUseEnsemble.html)

---

## Overview

This project develops a **continuous risk scoring system** for substance use based on personality traits (Big Five) and behavioral factors. Unlike traditional classification approaches, this regression-based method provides granular risk assessment suitable for clinical decision support.

### Key Contributions

1. **Novel risk quantification**: Transformed ordinal drug recency data into continuous risk scores using three approaches:
   - Additive (sum-based)
   - Weighted by substance severity
   - PCA-derived composite score

2. **Ensemble methodology**: Stacked model combining Random Forest and Gradient Boosting (meta-learner: GLM)
   - **Validation RMSE: 0.137**
   - **Test RMSE: 0.103**
   - **R² = 0.991** (explains 99% of variance)

3. **Robust evaluation**: 10-fold cross-validation, missing data simulation (5%), residual diagnostics

---

## Methodology

### Data
- **Source**: [UCI Drug Consumption (Quantified)](https://archive.ics.uci.edu/dataset/373/drug+consumption+quantified)
- **N**: 1,885 individuals
- **Features**: 
  - Big Five personality traits (NEO-FFI-R)
  - Demographics (age, gender, education, ethnicity)
  - Substance use across 18 drugs (ordinal recency: never → last day)

### Risk Score Construction

**Weighted Risk Score Formula:**
```
Risk = Σ (substance_recency × severity_weight)

Weights:
- Heroin: 3.0
- Cocaine: 2.5
- Meth: 2.2
- Amphetamines: 2.0
- Ecstasy: 1.8
- Cannabis: 1.0
- Alcohol: 0.5
```

Standardized via z-score transformation for modeling.

### Models Compared

| Model | Validation RMSE | Test RMSE | R² |
|-------|-----------------|-----------|-----|
| Random Forest | 0.1368 | - | - |
| Gradient Boosting | 0.1368 | - | - |
| **Stacked Ensemble** | **0.1368** | **0.1025** | **0.991** |

**Ensemble composition**: 96.7% GBM + 3.3% Random Forest

---

## Key Findings

### Personality-Drug Associations

From correlation analysis (all p < 0.001):

**Openness to Experience** → Increased use of:
- Cannabis
- Ecstasy  
- Cocaine
- LSD (r = 0.43 with mushrooms)

**Conscientiousness & Agreeableness** → Protective effects:
- Negative associations with nicotine, ecstasy
- Lower multi-drug use patterns

**Neuroticism** → Modest positive associations:
- Nicotine (self-medication hypothesis)
- Cannabis

### Model Interpretability

- **Most predictive features**: PCA Component 1 (captures overall substance use pattern)
- **Residual analysis**: Normally distributed (QQ plot)
- **Low MAE (0.069)**: Predictions within ~7% of actual standardized risk

---

## Usage

### Prerequisites
```r
install.packages(c(
  "caret", "randomForest", "gbm", "caretEnsemble",
  "h2o", "xgboost", "ggplot2", "psych", "car"
))
```

### Run Analysis
```r
# Open in RStudio
rmarkdown::render("analysis/McCrayV.DA5030.Project.Rmd")
```

---

## Limitations & Future Work

### Current Limitations
1. **Sample bias**: 78% ages 18-44, 91% White ethnicity
2. **Self-reported data**: Social desirability bias
3. **Cross-sectional**: Cannot infer causation
4. **Severity weights**: Based on literature review, not clinical validation

### Planned Extensions
1. **Deep learning comparison**: 
   - Feedforward neural networks
   - Attention-based models for feature importance
2. **Multimodal integration**: 
   - Add neuroimaging data (brain structure/function)
   - Genetic risk scores (polygenic risk for addiction)
3. **Fairness analysis**: 
   - Evaluate bias across demographic groups
   - Calibration by ethnicity/age
4. **Longitudinal validation**: 
   - Prospective cohort studies
   - Temporal risk trajectories

---

## Clinical Translation

**Potential Applications:**
- Early intervention screening in primary care
- Treatment prioritization in substance use programs
- Resource allocation for prevention

**NOT validated for clinical use** - requires:
- IRB approval
- Prospective validation
- Bias auditing
- Clinical workflow integration

---

## Citation
```bibtex
@misc{mccray2025druguse,
  title={Ensemble Regression for Substance Use Risk Prediction},
  author={McCray, Victoria P.},
  year={2025},
  howpublished={\url{https://github.com/victoriamccray/drug-use-risk-prediction}}
}
```

---

## References

Fehrman, E., et al. (2017). The Five Factor Model of personality and evaluation of drug consumption risk. *Data Science: Innovative Developments in Data Analysis and Clustering*, 231-242.

---


[LinkedIn](https://linkedin.com/in/victoria-mccray-99399514a) | [GitHub](https://github.com/victoriamccray) | victoriapmccray@gmail.com
