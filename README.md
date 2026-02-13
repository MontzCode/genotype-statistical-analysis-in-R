# Genotype Statistical Analysis

Statistical modelling and probabilistic analysis of genomic data implemented in R, completed as part of the MSc Artificial Intelligence in the Biosciences programme at Queen Mary University of London.

The assignment covers four problems spanning probability theory, hypothesis testing, linear modelling with stepwise selection, and likelihood-based parameter estimation using the Expectation-Maximisation algorithm.

---

## Table of Contents

- [Overview](#overview)
- [Project Structure](#project-structure)
- [Requirements](#requirements)
- [Problems Covered](#problems-covered)
- [Key Results](#key-results)

---

## Overview

This project applies core statistical and probabilistic methods to genomic and clinical datasets. It moves from foundational probability (PMF and CDF of alternate allele counts) through to applied statistical modelling (GLM with AIC-based selection) and likelihood-based estimation (EM algorithm with bootstrapped confidence intervals).

All analysis is implemented in R using base statistical functions alongside packages from the tidyverse and MASS ecosystems.

---

## Project Structure

```
genotype-statistical-analysis/
│
├── genotype_statistical_analysis.pdf    # Full rendered notebook with outputs
├── assignment.csv                        # Input data for Problems 3 and 4 (not tracked)
└── README.md
```

---

## Requirements

```r
install.packages(c("tidyverse", "MASS", "knitr"))
```

---

## Problems Covered

**Problem 1 — Probability Mass Function and CDF of Alternate Allele Counts**

Constructs the sample space for the sum of alternate alleles across two genomic sites using `expand.grid()`, computes the PMF via frequency normalisation, and visualises both the PMF as a bar chart and the CDF as a step plot. The resulting distribution is symmetric around G = 2, with probabilities ranging from 1/9 at the extremes to 3/9 at the centre.

**Problem 2 — Observed Genotype Distribution and Hypothesis Testing**

Computes G (total alternate alleles) for ten individuals across two genomic sites by string parsing, then calculates the mean (2.0), standard deviation (1.15) and skewness (0) of the observed distribution. A two-sample t-test comparing G against a second dataset G2 returns t = 2.64 and p = 0.025, leading to rejection of the null hypothesis of equal means at α = 0.05.

**Problem 3 — Linear Model with Stepwise AIC Selection**

Fits a full linear model predicting disease risk from genotypes, ancestry and income. Stepwise AIC-based selection via `stepAIC()` removes income from the model (AIC drops from 877.33 to 875.35), yielding a reduced model where genotypes (p < 2e-16) and ancestry (Groups 2 and 3 at p = 0.005 and p = 1.89e-05 respectively) are both significant predictors. The model explains 42.4% of variance in disease risk (adjusted R² = 0.416). Residual diagnostics confirm homoscedasticity and normality of residuals (Shapiro-Wilk W = 0.996, p = 0.870).

**Problem 4 — EM Algorithm for Gaussian Mixture Model**

Implements the Expectation-Maximisation algorithm from scratch to fit a two-component normal mixture model to income data. The E-step computes posterior responsibilities for each component; the M-step updates all five parameters (α, μ₁, μ₂, σ₁, σ₂) iteratively until convergence. Bootstrap confidence intervals (n = 1000 resamples) are computed for each parameter estimate.

| Parameter | Estimate | 95% CI Lower | 95% CI Upper |
|---|---|---|---|
| α | 0.605 | 0.535 | 0.668 |
| μ₁ | 30.125 | 29.460 | 30.870 |
| μ₂ | 49.801 | 48.304 | 50.910 |
| σ₁ | 3.083 | 2.681 | 3.481 |
| σ₂ | 4.812 | 4.016 | 5.846 |

---

## Key Results

The stepwise model selection in Problem 3 demonstrates that income does not contribute meaningfully to explaining variance in disease risk once genotype and ancestry are accounted for. The genotype effect is the dominant predictor, with ancestry acting as a significant modifier — Ancestry Group 3 showing the largest elevated risk relative to Group 1.

The EM algorithm implementation in Problem 4 successfully separates the income distribution into two distinct Gaussian components with well-separated means (30.1 and 49.8), suggesting a bimodal income structure in the data. The bootstrapped confidence intervals are narrow relative to the parameter estimates, indicating stable convergence.
