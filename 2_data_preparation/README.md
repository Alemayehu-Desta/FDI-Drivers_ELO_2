## Data Preparation 

This folder contains the Python scripts and notebooks used to clean, standardize, and prepare all datasets for the Foreign Direct Investment (FDI) analysis project.

---

## Reproducibility Principles

- **Raw datasets in - [../1_datasets/](../1_datasets/) are never modified.**
- **All cleaned outputs are written as new files in this folder.**
- **Anyone cloning this repository can re-run the scripts and reproduce the final analytical datasets.**

---

## 1️. Income Classification Filtering

### **Input Dataset**
- `income_class.xlsx` (World Bank income classification)

### **What the script does**
- Standardizes column names to:  
  `Country`, `Code`, `Income_group`
- Filters countries to keep only:
  - **Low income**
  - **Lower middle income**
  - **Upper middle income**
- Extracts **129 valid ISO-3 country codes**
- These codes become the master filter for all other datasets.

### **Output**
- Filtered income classification table  
- Set of allowed country codes (129 total)

---

## 2. Cleaning & Standardizing All Datasets

The following datasets are processed from `0_datasets/`:

| Dataset | Filename | Final Variable |
|--------|----------|----------------|
| Net FDI inflows | `nations_netFDI.csv` | `FDI_inflows` |
| GDP (current USD) | `country_GDP_size.csv` | `GDP_current_USD` |
| GDP growth | `annual_GDP_growth.csv` | `GDP_growth` |
| Trade openness | `trade_openness.csv` | `Trade_pct_GDP` |
| Inflation | `inflation.csv` | `Inflation_CPI` |
| Electricity access | `electricity.csv` | `Electricity_access` |
| Education enrollment | `education.csv` | `Education_enrollment` |
| Logistics Performance Index | `LPI_score.csv` | `LPI_score` |
| Corruption index (CPI) | `corruption.csv` | `CPI` |

---

### 2A️. Wide → Long Conversion  
(Used for most datasets)

Each dataset undergoes:

1. Standardize country & code columns  
2. Filter to the **129 allowed income-group countries**  
3. Auto-detect year columns  
4. Rename them to a consistent four-digit year format  
5. Convert wide → long:  
6. Filter for **years 2010–2024**

### Typical Output Shape


---

### 2B️. CPI Dataset (Already Long Format)

The CPI dataset is cleaned by:

- Standardizing column names (`Country`, `Code`, `Year`, `CPI`)
- Filtering to allowed countries
- Filtering years 2010–2024

### Output Shape

---

## 3. Merging Process — Final Panels Produced

Two merged datasets are created for different analytical needs.

---

### 🔹 A. INNER JOIN PANEL (Strict, Balanced)

- Merged on: `Country`, `Code`, `Year`
- Keeps only rows where **all datasets contain data**
- Produces a **balanced panel** (ideal for regressions)

📄 **Output File:**  
`panel_innerjoin_strict.csv`

---

### 🔹 B. LEFT JOIN PANEL (Max Coverage, Unbalanced)

- Merged **on Code only**  
- Missing years in LPI/CPI remain as `NaN`  
- Produces an **unbalanced panel** with maximum available data  

📄 **Output File:**  
`panel_leftjoin_code_only.csv`

---

## 4️. Summary of Outputs

| File | Description |
|------|-------------|
| [`panel_innerjoin_strict.csv`](./cleaned/panel_innerjoin_strict.csv) | Balanced panel, complete data, regression-ready |
| [`panel_leftjoin_code_only.csv`](./cleaned/panel_leftjoin_code_only.csv) | Unbalanced panel, maximum coverage, exploratory analysis |
| Long-format intermediate tables | Generated in memory, not saved individually |

---

## 5. Reproducibility Notes

- Scripts never modify original datasets  
- All transformations are deterministic  
- Parameters (`year_min`, `year_max`) ensure reproducible filtering  
- Process can be re-run end-to-end on any machine

---




