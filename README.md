# Cognitive Decline Predictor

> Can modifiable lifestyle factors predict cognitive decline — and does physical activity protect the brain regardless of genetic risk?

This project investigates whether five modifiable lifestyle factors (physical activity, sleep quality, BMI, blood pressure, and HbA1c) can predict 12-month cognitive change in a clinically heterogeneous sample of 240 adults across the cognitive impairment spectrum. It uses Pearson correlations, one-way ANOVA, and multiple linear regression, with a dedicated analysis of APOE4 genetic risk as a moderator.

The dataset originates from the PMIM202 Health Data Modelling module at Swansea University (MSc Health Data Science), and the analysis extends the original assignment work with refined modelling, multicollinearity diagnostics, and interactive visualisations.

📓 **[View the full analysis on Kaggle](https://www.kaggle.com/code/yousufaayon/cognitive-decline-predictor)**

---

## The Sample

240 participants were recruited across three diagnostic groups:

| Group | n | Mean Age | Mean MoCA Change |
|---|---|---|---|
| Cognitively Normal (CN) | 101 | 66.2 | -0.33 |
| Mild Cognitive Impairment (MCI) | 76 | 70.8 | -0.40 |
| Alzheimer's Disease (AD) | 63 | 75.0 | -0.93 |

CN participants were on average 9 years younger than AD patients, exercised nearly four times as much (3,240 vs 839 METs/week), and had substantially better sleep quality scores — pointing to strong confounding between lifestyle and disease stage that the regression models needed to untangle.

---

## What the Analysis Found

**Lifestyle factors do correlate with cognitive change — but diagnosis explains most of it.**

In unadjusted Pearson correlations, all five lifestyle predictors were significantly associated with 12-month MoCA change (all p < 0.01). Physical activity was the strongest positive predictor (r = 0.303) and BMI the strongest negative predictor (r = -0.302).

Once diagnosis, demographics, and genetic risk were entered into the regression model, the picture changed. A multicollinearity check flagged severe VIF inflation for Age (VIF = 229) and BMI (VIF = 262) — both essentially collinear with Diagnosis. After removing them, the refined model was more stable and revealed that **physical activity was the only lifestyle factor with a significant independent effect** on cognitive outcomes (β = 0.000194, p = 0.034). Each additional 1,000 METs per week was associated with approximately 0.19 points less cognitive decline over 12 months.

APOE4 carriers showed worse average MoCA change than non-carriers (-0.601 vs -0.434), but the interaction between physical activity and APOE4 status was non-significant (p = 0.349). The protective effect of exercise appears consistent regardless of genetic risk.

---

## Model Summary

| Model | R² | Adj R² | F-statistic | p |
|---|---|---|---|---|
| Full model (12 predictors) | 0.120 | 0.073 | 2.579 | 0.003 |
| Refined model (Age & BMI removed) | 0.116 | 0.077 | 3.007 | 0.001 |
| APOE4 interaction model | 0.120 | 0.077 | 2.812 | 0.002 |

The refined model explains approximately 12% of variance in 12-month cognitive change — modest but consistent with the broader literature on lifestyle interventions in cognitive ageing, where diagnostic stage dominates short-term trajectories.

---

## Analytical Approach

The notebook is written in **R** and follows an IMRaD-inspired structure:

- Descriptive statistics and group comparisons by diagnosis
- Pearson correlations with 95% confidence intervals
- One-way ANOVA with Tukey post-hoc tests
- Multiple linear regression with VIF-based multicollinearity diagnostics
- Refined model after removing collinear predictors
- APOE4 interaction model testing genetic moderation of physical activity effects
- Visualisations using ggplot2: scatter plots, boxplots, coefficient plots, interaction plots

---

## Repo Structure

```
cognitive-decline-predictor/
│
├── cognitive-decline-predictor.ipynb   # Full R analysis notebook
├── pmim202_biomarkers_dataset.csv      # Lifestyle & biomarker variables (n=240)
├── pmim202_imaging_genetic_dataset.csv # Imaging, genetic & demographic variables
└── README.md
```

---

## Context & Background

This analysis builds on work originally completed for the PMIM202 Health Data Modelling
module (MSc Health Data Science, Swansea University). The original report examined the same
five lifestyle predictors using the same datasets, reaching broadly consistent conclusions.
This Kaggle notebook extends that work by adding multicollinearity diagnostics, a refined
regression model, and a formal test of APOE4 as a moderator — analyses not included in
the original submission.

The findings are consistent with evidence from large-scale prevention trials including
FINGER (Ngandu et al., 2015) and MAPT (Vellas et al., 2014), which identified physical
activity as the most consistently effective modifiable factor for reducing cognitive decline
in at-risk populations.

---

## Other Projects

- [NHS Prescription Cost Analysis](https://github.com/alpsAyon/nhs-prescription-analysis) — 54 million prescriptions, Apr–Jun 2025
- [COVID-19 Wales Population Health](https://github.com/alpsAyon/covid19-wales-health) — Seven-wave pandemic analysis for Wales

---

**Yousuf** | MSc Health Data Science, Swansea University
[Kaggle](https://www.kaggle.com/yousufaayon) · [GitHub](https://github.com/alpsAyon)
