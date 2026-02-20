# Wavelet-Informed Time-Series Modelling of Climate–Disease Synchrony  
## Operational Early Warning of Lassa Fever in Nigeria

**Author:** Ayokunle John TADEMA  
**Affiliation:** Department of Computer Science, McPherson University, Seriki Sotayo  
**Contact:** tademaaj@mcu.edu.ng | ORCID: 0000-0001-6334-3850  

---

## Overview

This repository contains all R analysis code for the manuscript:

> *Wavelet-Informed Time-Series Modelling of Climate–Disease Synchrony for Operational Early Warning of Lassa Fever*

The framework identifies rainfall–disease lag structures using wavelet coherence and converts them into a four-tier operational early warning alert system across six Nigerian states (2018–2025).

---

## Repository Structure

```
lassa-fever-sarimax/
├── R/
│   ├── 00_setup.R                   # Package installation and global settings
│   ├── 01_data_processing.R         # Data loading, cleaning, interpolation
│   ├── 02_descriptive_statistics.R  # Transmission regime classification (VMR, zero-inflation)
│   ├── 03_stl_decomposition.R       # STL seasonal decomposition
│   ├── 04_wrai_construction.R       # Weekly Rainfall Anomaly Index (WRAI)
│   ├── 05_wavelet_coherence.R       # Wavelet coherence + phase-lag extraction + bootstrap CIs
│   ├── 06_lag_ccf_analysis.R        # Cross-correlation function lag estimation
│   ├── 07_sarimax_modelling.R       # SARIMAX model selection, fitting, diagnostics
│   ├── 08_model_comparison.R        # SARIMA vs SARIMAX: LR tests, AIC, WRAI coefficients
│   ├── 09_zinb_sensitivity.R        # ZINB sensitivity analysis + threshold comparison
│   ├── 10_forecast_validation.R     # Rolling-origin validation, multi-horizon MAE/RMSE
│   ├── 11_alert_thresholds.R        # Four-tier alert system definition and calibration
│   ├── 12_alert_validation.R        # Alert sensitivity, PPV, lead time + bootstrap CIs
│   ├── 13_onset_detection.R         # Climate contribution to outbreak onset timing (S3.8)
│   ├── 14_uncertainty_quantification.R  # Block bootstrap MAE CIs; event-level bootstrap
│   ├── 15_supplementary_tables.R    # Generate all supplementary tables S5–S9
│   └── 16_figures.R                 # All manuscript and supplementary figures
├── data/
│   └── README_data.md               # Data source descriptions (NCDC + CHIRPS)
├── outputs/                         # Auto-generated tables and figures
├── figures/                         # Auto-generated publication figures
└── README.md                        # This file
```

---

## Data Sources

| Data | Source | Resolution | Period |
|------|--------|-----------|--------|
| Lassa fever cases | [NCDC Situation Reports](https://ncdc.gov.ng) | Weekly, by state | Epi-W1 2018 – W46 2025 |
| Rainfall | [CHIRPS v2.0](https://data.chc.ucsb.edu/products/CHIRPS-2.0/) | 0.05°, daily → weekly | 2018–2025 |

---

## R Requirements

R ≥ 4.2.0. All packages are installed in `00_setup.R`.

---

## Running the Analysis

Run scripts in numbered order:

```r
source("R/00_setup.R")
source("R/01_data_processing.R")
# ... continue in sequence
```

Or run everything at once:

```r
scripts <- list.files("R", full.names = TRUE, pattern = "\\.R$")
for (s in scripts) source(s)
```

---

## License

Code: MIT License  
Data: NCDC (public domain); CHIRPS (CC-BY 4.0)
