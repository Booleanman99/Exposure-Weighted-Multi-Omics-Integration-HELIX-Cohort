# Exposure-Weighted Multi-Omics Integration for Pediatric Metabolic Risk Profiling

An exploratory study leveraging the HELIX (Human Early-Life Exposome) cohort to develop an exposure-weighted multi-omics integration framework for pediatric metabolic risk assessment.

## Summary

This project integrates environmental exposure data with multi-omics molecular profiles to predict pediatric metabolic risk. Using data from the HELIX cohort, we developed a machine learning pipeline that combines:

- **Environmental Exposures**: Air pollution (NO2, PM2.5, PM10), heavy metals, persistent organic pollutants, lifestyle factors
- **Multi-Omics Data**: Methylome, transcriptome, miRNA, proteome, and metabolome profiles
- **Temporal Windows**: Both pregnancy and childhood exposure periods

### Key Findings

| Metric | Value |
|--------|-------|
| **Sample Size** | 1,301 children |
| **Total Features** | 255 (206 exposure + 49 omics-derived) |
| **Omics Layers** | 5 (methylome, transcriptome, miRNA, proteome, metabolome) |
| **Non-zero LASSO Predictors** | 65 features retained |
| **High-Risk Threshold** | 75th percentile (risk score ≥ 67.31) |

### Model Performance (5-Fold Cross-Validation)

| Model | AUC | Accuracy | F1 Score |
|-------|-----|----------|----------|
| Logistic Regression (LASSO) | 0.997 ± 0.001 | 0.968 ± 0.011 | 0.936 ± 0.021 |
| XGBoost | 0.986 ± 0.007 | 0.940 ± 0.007 | 0.872 ± 0.015 |
| Random Forest | 0.961 ± 0.013 | 0.875 ± 0.025 | 0.671 ± 0.090 |

### Top Predictive Features

The LASSO-regularized model identified key predictors including:
- **Metabolome risk scores** (coefficient: 8.19)
- **Transcriptome risk scores** (coefficient: 4.86)
- **Proteome risk scores** (coefficient: 2.72)
- **Methylome child risk** (coefficient: 1.36)
- Environmental factors: chloroform exposure, PFNA, benzene, particulate matter

## Report Location

The complete project report and presentation can be found in the **[`Final/`](./Final/)** folder:
- [`Exposure-Weighted-Multi-Omics-Integration-HELIX-Cohort_FINAL_DRAFT.pdf`](./Final/Exposure-Weighted-Multi-Omics-Integration-HELIX-Cohort_FINAL_DRAFT.pdf) - Full project report
- [`Exposure-Weighted-Multi-Omics-Integration-HELIX-Cohort_Presentation.pdf`](./Final/Exposure-Weighted-Multi-Omics-Integration-HELIX-Cohort_Presentation.pdf) - Project presentation

Additional progress reports are available in the [`Reports/`](./Reports/) folder.

## Repository Structure

```
├── Final/                  # Final report and presentation
├── FINAL.ipynb             # Main analysis notebook
├── Pipeline/               # Data processing pipeline
│   └── Exposure ONLY/      # Exposure-only analysis
├── Pathway Enrichment/     # Pathway enrichment analysis
│   └── Serum Metabolites/  # Metabolite pathway results
├── Reports/                # Progress reports
├── ipynb PDFs/             # PDF exports of notebooks
└── Maitre_HELIX_study_2018 (1).pdf  # Reference paper
```

## Methods

1. **Data Integration**: Merged exposure data with omics-derived risk scores for each molecular layer
2. **Feature Selection**: LASSO regularization (λ = 2.78) for interpretable feature selection
3. **Risk Stratification**: Binary classification using 75th percentile threshold
4. **Validation**: 5-fold stratified cross-validation
5. **Interpretation**: SHAP analysis for feature importance

## Reference

This study uses data from the HELIX cohort as described in:
> Maitre et al. (2018). Human Early Life Exposome (HELIX) study: a European population-based exposome cohort.

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.
