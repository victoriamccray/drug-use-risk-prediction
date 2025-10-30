# Data

## Source

This project uses the **Drug Consumption (Quantified)** dataset from the UCI Machine Learning Repository.

- **URL**: https://archive.ics.uci.edu/dataset/373/drug+consumption+quantified
- **Direct download**: https://archive.ics.uci.edu/static/public/373/data.csv

## Description

- **N**: 1,885 individuals
- **Features**: 32 (12 personality/demographic + 18 substance use + 2 behavioral)

### Variables

**Demographics:**
- Age, Gender, Education, Country, Ethnicity

**Personality (NEO-FFI-R):**
- Neuroticism (Nscore)
- Extraversion (Escore)
- Openness (Oscore)
- Agreeableness (Ascore)
- Conscientiousness (Cscore)

**Behavioral:**
- Impulsiveness (BIS-11)
- Sensation Seeking (ImpSS)

**Substance Use (18 drugs):**
Each rated on 7-point scale:
- CL0: Never used
- CL1: Used over a decade ago
- CL2: Used in last decade
- CL3: Used in last year
- CL4: Used in last month
- CL5: Used in last week
- CL6: Used in last day

Substances: Alcohol, Amphetamines, Amyl Nitrite, Benzodiazepines, Caffeine, Cannabis, Chocolate (control), Cocaine, Crack, Ecstasy, Heroin, Ketamine, Legal Highs, LSD, Methadone, Mushrooms, Nicotine, VSA

## Usage in Analysis

The R Markdown file (`analysis/PredictingDrugUseEnsemble.Rmd`) downloads the data automatically from the UCI repository. No manual download needed.

## Citation

Fehrman, E., Muhammad, A. K., Mirkes, E. M., Egan, V., & Gorban, A. N. (2017). The Five Factor Model of personality and evaluation of drug consumption risk. *arXiv preprint arXiv:1506.06297*.
