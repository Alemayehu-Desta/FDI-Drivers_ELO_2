## **FDI Determinants in Developing Economies**  
### *MIT Emerging Talent – Individual Collaborative Data Science Project (CDSP)*  

<p align="center">
  <img src="https://img.shields.io/badge/Project-Type%3A%20Econometrics%20%2B%20ML-blue" />
  <img src="https://img.shields.io/badge/Data-Panel%20Data%202010–2023-green" />
  <img src="https://img.shields.io/badge/Status-Complete-brightgreen" />
  <img src="https://img.shields.io/badge/Made%20With-Python%20%7C%20Tableau%20%7C%20Statsmodels-yellow" />
</p>

<p align="center">
  <img width="600" src="https://images.unsplash.com/photo-1644867356984-dfcf75f1a4bb?auto=format&fit=crop&w=1200&q=60" />
</p>

---

## **Project Overview**

This repository contains a fully reproducible data science workflow investigating:

> **Which macroeconomic, structural, and institutional variables best predict FDI inflows in developing economies?**

Using **panel econometrics**, **machine learning**, and **policy-oriented visualization**, this project analyzes the drivers of FDI using data from 2010–2023 across dozens of developing countries.

The structure follows the **MIT Emerging Talent – Collaborative Data Science Project (CDSP)** methodology.

---
---

<details>
<summary><h2>Table of Contents (Click to Expand)</h2></summary>

- [Research Question](#-research-question)
- [Project Milestones](#-project-milestones)
- [Analysis Summary](#-analysis-summary)
- [Machine Learning – Random Forest](#-machine-learning--random-forest)
- [Key Findings](#-key-findings)
- [Limitations](#-limitations)
- [Future Work](#-future-work)
- [Tech Stack](#-tech-stack)

</details>

---

## **Directory Structure**

```plaintext
/
├── README.md                   # Main project overview
├── guide.md                    # Template usage guide
├── notes/                      # Research notes & resources
├── 0_domain_study/             # FDI theory, literature & context
├── 1_datasets/                 # Raw + cleaned datasets (read-only)
├── 2_data_preparation/         # Cleaning & merging scripts
├── 3_data_exploration/         # EDA & diagnostics
├── 4_data_analysis/            # Econometric + ML models
├── 5_communication_strategy/   # Communication artifacts & messaging
└── 6_final_presentation/       # Slide deck & presentation assets

```

## Research Question

### **What structural, institutional, and macroeconomic indicators most strongly explain or predict FDI inflows in developing economies?**

**Key variables include:**

- Logistics Performance Index (LPI)  
- Electricity Access  
- Corruption Perception  
- Education Enrollment  
- Inflation  
- GDP Growth  
- Trade Openness  

---

## Project Milestones

### **0.Domain Study**
- Reviewed foundational FDI literature  
- Explored theories of agglomeration & path dependency  

### **1.Problem Identification**
- Defined the development challenge of uneven FDI distribution  
- Framed an empirical research question grounded in theory  

### **2.Data Collection**
- Collected World Bank, WGI, and LPI data  
- Documented metadata in `/1_datasets`  

### **3.Data Exploration**
- Ran EDA to inspect distributions, missingness, and trends  
- Produced correlation maps and country profiles  

### **4.Data Analysis**
- Built econometric models (Pooled OLS, Fixed Effects attempt)  
- Built ML models (Random Forest Regressor)  
- Compared causal vs predictive workflows  

### **5.Communication Strategy**
- Developed policy messaging & visual storytelling artifacts  

### **6.Final Presentation**
- Synthesized methods, results, and recommendations into slides  

---

## Analysis Summary

### Regression Modeling

**Baseline regression equation:**

log(FDI_it) =
    β0
    + β1 * GDP_growth_it
    + β2 * Trade_pct_GDP_it
    + β3 * Inflation_CPI_it
    + β4 * LPI_score_it
    + β5 * CPI_it
    + β6 * Electricity_access_it
    + β7 * Education_enrollment_it
    + ε_it


  
---

### Statistically Significant Predictors (p < 0.05)

| Variable            | Interpretation                                      |
|--------------------|------------------------------------------------------|
| **LPI Score**      | Strong logistics attract investment.                 |
| **Electricity Access** | Power reliability is a prerequisite for investment. |
| **Inflation (Moderate)** | Indicates active, growing economies.           |

---

### Non-Significant Predictors
- GDP Growth (volatile & noisy)  
- Trade Openness (collinear with GDP size)  
- CPI (corruption), Education (long-run effects not captured)  

---

### Machine Learning — Random Forest

### Target  
  log(FDI_it)

  
### Predictors
- Macroeconomic & structural variables  
- **Lagged FDI:** `log(FDI_{i,t-1})`  

### Why Lagged FDI?
Because **FDI is path-dependent** — countries that received investment last year tend to keep receiving it.

---

### ML Feature Importance (Top Signals)

1. **Lagged FDI** → strongest predictor  
2. **Electricity Access**  
3. **LPI Score**  
4. Inflation, Trade, CPI (lower but still relevant)  

---

### How ML Differs From OLS
- ML aims to **predict**, not interpret  
- Handles nonlinear relationships  
- Tolerates multicollinearity  
- Automatically learns variable interactions  

---

## Key Findings

### 1. FDI is sticky  
Prior-year investment strongly predicts future FDI inflows.

### 2. Infrastructure is king  
Electricity access & logistics capacity outperform institutional variables.

### 3. Global cycles matter  
Year effects suggest global shocks dominate domestic reforms.

### 4. Governance matters less than assumed  
Investors may “price in” corruption if infrastructure is strong.

---

### Limitations
- Missing data for some variables  
- Fixed-effects model could not be estimated with clustered SEs  
- ML cannot infer causality  
- Global shocks not fully modeled  

---

### Future Work
- Dynamic Panel Models (Arellano-Bond GMM)  
- SHAP value interpretability for ML  
- Regional fixed effects  
- Tableau dashboard enhancement  
- Expand dataset to include HICs  

---

### Tech Stack

<p align="left">
  <img src="https://img.shields.io/badge/Python-3.10-blue" />
  <img src="https://img.shields.io/badge/Libraries-pandas%20%7C%20statsmodels%20%7C%20sklearn-orange" />
  <img src="https://img.shields.io/badge/Visualization-Plotly%20%7C%20Tableau-green" />
  <img src="https://img.shields.io/badge/Notebook-Jupyter-lightgrey" />
</p>







