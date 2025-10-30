# Substance Use Risk Prediction

Ensemble regression model predicting drug use risk from personality traits and behavioral factors.

## Overview

This project develops a continuous risk scoring system for substance use based on the Big Five personality traits and demographic factors. Using ensemble methods (Random Forest + Gradient Boosting), the model achieves strong predictive performance (R² = 0.991, RMSE = 0.103).

**Key Features:**
- Novel continuous risk score from ordinal drug recency data
- Weighted by substance severity (heroin: 3.0, cannabis: 1.0, etc.)
- Stacked ensemble with 10-fold cross-validation
- Robust missing data handling and residual diagnostics

## Dataset

- **Source**: [UCI Drug Consumption (Quantified)](https://archive.ics.uci.edu/dataset/373/drug+consumption+quantified)
- **N**: 1,885 individuals
- **Features**: Big Five personality traits (NEO-FFI-R), demographics, substance use history across 18 drugs

## Results

| Model | Validation RMSE | Test RMSE | R² |
|-------|-----------------|-----------|-----|
| Random Forest | 0.137 | - | - |
| Gradient Boosting | 0.137 | - | - |
| **Stacked Ensemble** | **0.137** | **0.103** | **0.991** |

### Key Findings

- **Openness to Experience**: Strongest predictor of cannabis, ecstasy, LSD use
- **Conscientiousness**: Protective effect against substance use
- **Neuroticism**: Associated with nicotine and cannabis use
- **Ensemble composition**: 96.7% GBM + 3.3% Random Forest

## Methodology

1. **Risk Score Construction**: Three approaches compared
   - Additive (sum of recency scores)
   - Weighted by severity
   - PCA-derived composite

2. **Ensemble Model**: Stacked approach using:
   - Base learners: Random Forest, Gradient Boosting Machine
   - Meta-learner: Generalized Linear Model (GLM)

3. **Validation**: 10-fold cross-validation with residual analysis

## Repository Contents

- `analysis/`: R Markdown analysis file
- `results/`: Figures and outputs
- `data/`: Data download instructions

## Usage
```r
# Install required packages
install.packages(c("caret", "randomForest", "gbm", "caretEnsemble", 
                   "h2o", "xgboost", "ggplot2", "psych", "car"))

# Run analysis
rmarkdown::render("analysis/PredictingDrugUseEnsemble.Rmd")
```

## Limitations

- **Sample bias**: 78% ages 18-44, 91% White
- **Self-reported data**: Social desirability bias
- **Cross-sectional**: Cannot infer causation
- **Severity weights**: Literature-based, not clinically validated

* **Not validated for clinical use** - requires IRB approval, prospective validation, and bias auditing

## Future Work

- Deep learning comparison (neural networks)
- Multimodal extension (neuroimaging + genetics)
- Fairness analysis across demographic groups
- Longitudinal validation

## Citation
```bibtex
@misc{mccray2025druguse,
  title={Ensemble Regression for Substance Use Risk Prediction},
  author={McCray, Victoria P.},
  year={2025},
  url={https://github.com/yourusername/drug-use-risk-prediction}
}
```

## References

Fehrman, E., et al. (2017). The Five Factor Model of personality and evaluation of drug consumption risk. *Data Science: Innovative Developments in Data Analysis and Clustering*, 231-242.

## Author

**Victoria McCray**  
MSc Bioinformatics Candidate, Northeastern University  
Health Data Scientist, Guidehouse

[LinkedIn](https://linkedin.com/in/victoria-mccray) | victoriapmccray@gmail.com

## License

MIT License
