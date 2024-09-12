# Genotype Analysis Tool: Statistical Analysis for Genetic Data

This R-based tool is developed to perform in-depth statistical analysis on genetic data. It computes genotype probabilities, examines allele distributions, and conducts statistical tests to compare allele frequency differences across populations. The tool generates both descriptive and inferential statistics, offering comprehensive insights through visual representations of the data.

# Features

- Genotype Probabilities and Distributions:  Calculate and visualize the probability mass function (PMF) and cumulative distribution function (CDF) for alternate alleles across two genomic sites.

- Observed Data and Distribution Visualization: Visualize allele distributions, compute statistical metrics (mean, variability, skewness), and perform hypothesis tests to compare allele frequencies across populations.

- General Linear Model for Risk Analysis: Fit and reduce a linear model to evaluate the significance of genotypes, ancestry, and income in predicting risk, with statistical reports and visual outputs.

- Mixture Model for Income Distribution: Model income as a mixture of normal distributions using the EM algorithm, with bootstrapped confidence intervals for parameter estimation.

# Required Libraries
To use this tool, these libraries need to be installed

install.packages(c("tidyverse", "MASS", "knitr"))
