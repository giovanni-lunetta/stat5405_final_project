# Predicting NFL Rushing Yards
### Statistical Computing (STAT 5405) — University of Connecticut, Fall 2023

---

## Overview

This project builds predictive models to estimate the yards gained by an NFL running back following a handoff. Using player tracking data from the NFL Big Data Bowl competition, we compare three regression approaches to identify which best captures the complex, multi-player dynamics of a rushing play.

**Authors:** Giovanni Lunetta, Sam Lutzel
**Course:** STAT 5405 — Statistical Computing, University of Connecticut

---

## Research Question

> Can player tracking data — speed, acceleration, orientation, field position, and game context — accurately predict the yards gained on an NFL rushing play?

---

## Data

- **Source:** NFL Big Data Bowl — player tracking data provided by the NFL
- **Coverage:** 2017, 2018, and first half of the 2019 NFL regular seasons
- **Size:** 682,154 rows × 49 columns (one row per player per play)
- **Target variable:** `Yards` — yards gained on the rushing play
- **Key features:** Player speed/acceleration/orientation, defenders in the box, down & distance, yard line, field position, offense/defense personnel groupings, weather, turf type

---

## Methods

Three regression models compared on predictive accuracy:

| Model | Implementation |
|---|---|
| Multiple Linear Regression (MLR) | OLS via `lm()` in R |
| Generalized Linear Model (GLM) | `glm()` in R |
| XGBoost | `xgboost` package in R |

**Evaluation metrics:** Mean Squared Error (MSE), Mean Absolute Error (MAE), R²

**Preprocessing:** Categorical encoding, feature scaling, removal of passing plays, randomization of play order to ensure independence between observations.

---

## Repository Structure

```
.
├── python/
│   └── cleaning_python.ipynb       # Initial data cleaning in Python
├── r/
│   ├── cleaning_r.qmd              # Data cleaning and preparation in R
│   └── DataPreparation.qmd         # Feature engineering and EDA
├── project_proposal/
│   └── project_proposal.qmd        # Original project proposal (Reveal.js slides)
├── project_report/
│   └── project_report/
│       ├── project_report.qmd      # Full written report (Quarto/LaTeX)
│       ├── project_report.pdf      # Final submitted PDF
│       └── R-SourceCode            # R source code used in the report
└── README.md
```

---

## How to Run

**Prerequisites (R):**
```r
install.packages(c("tidyverse", "ggplot2", "dplyr", "xgboost", "caret", "broom"))
```

**Prerequisites (Python):**
```bash
pip install pandas numpy
```

Data files from the NFL Big Data Bowl are required and are not included in this repository. The competition dataset can be accessed via Kaggle.

---

## Key Findings

- XGBoost outperformed both MLR and GLM on MSE and MAE, capturing non-linear interactions between player tracking variables
- Defenders in the box, yards to the first down, and player speed were among the most predictive features
- The distribution of rushing yards is right-skewed — most plays gain 0–5 yards, with a long tail of breakout runs — posing a challenge for linear models

---

## Authors

- **Giovanni Lunetta** — UConn MS Data Science
- **Sam Lutzel** — UConn MS Data Science
