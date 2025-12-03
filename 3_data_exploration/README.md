## Exploratory Data Analysis (EDA)

In this Exploratory Data Analysis (EDA) stage, we carefully examine the cleaned datasets prepared in `0_datasets/`.  
The purpose is to develop an intuitive understanding of the structure, behavior, and relationships embedded in the data before conducting any statistical modeling, causal inference, or machine learning.


---

###  1. Input Data Used for Analysis

EDA uses the final prepared datasets saved from the data-cleaning stage:

#### [`panel_regression_inner_join.csv`](../data_preparation/cleaned_data/panel_regression_inner_join.csv)
A balanced panel created using strict inner joins.  
Only countries and years with complete data across all variables are included.  
Useful for visualizing clean, uninterrupted time-series patterns.

#### [`panel_full_left_join.csv`](../data_preparation/cleaned_data/panel_full_left_join.csv)
An unbalanced panel created using left joins.  
This dataset retains countries even when some variables are missing, giving the broadest exploratory view.

Both datasets include:

- Country name & ISO-3 code  
- Year (2010–2024)  
- Net FDI inflows  
- GDP (current USD)  
- GDP growth rates  
- Trade openness  
- Inflation (CPI)  
- Electricity access  
- Education enrollment  
- LPI (logistics) scores  
- CPI (corruption) scores  
- Income group classification  

These variables together allow us to explore macroeconomic development patterns across LICs, LMICs, and UMICs.

---

### 2. What the EDA Scripts Do

### **a. Load and Inspect the Data**
Each notebook begins by reading both datasets and inspecting:

- Number of rows/columns  
- Preview of raw observations  
- Data types and value ranges  
- Missingness patterns  

This step helps ensure the data structure is well understood before deeper exploration.

### **b. Produce Descriptive Statistics**
The EDA notebooks compute:

- `.describe()` summaries  
- Country-level means and trends  
- Year-to-year changes  
- Distributions for all numeric variables  

This statistical overview highlights central tendencies, variation, and potential anomalies.

### **c. Generate Visualizations**
Visual exploration is central to this stage. The notebooks produce:

#### **1. Country-Level Profiles**
Dual-axis time-series plots for countries such as:

- China (CHN)  
- India (IND)  
- Nigeria (NGA)  

These show:

- FDI inflows over time  
- GDP growth over time  

Their joint visualization helps identify whether FDI movements correspond with real economic growth.

#### **2. Distribution Plots**
Histograms and KDE plots help assess whether variables behave as expected  
(e.g., right-skewed FDI patterns in developing economies).

#### **3. Correlation Heatmaps**
These descriptive heatmaps reveal broad relationships between variables but do not imply causality.

#### **4. Missing Data Maps**
Visual diagnostics (e.g., using `missingno`) show which countries or years lack data, helping guide decisions for later modeling.

---

### 3. What EDA Does *Not* Include

To preserve methodological integrity, EDA **does not**:

- Run regressions  
- Conduct causal inference  
- Use machine learning  
- Clean or transform datasets further  
- Modify any dataset inside `0_datasets/`  

EDA is purely observational and non-interventionist.

---

### 4. Overview of Scripts and Notebooks

| File Name | Description |
|----------|-------------|
| **`EDA_country_profiles.ipynb`** | Creates dual-axis visualizations for FDI and GDP growth for selected countries. Helps reveal dynamic macroeconomic patterns. |
| **`EDA_summary_statistics.ipynb`** | Generates descriptive statistics, missing-value analyses, and data summaries. |
| **`EDA_visualizations.ipynb`** | Produces broader exploratory visuals such as histograms, KDE plots, and correlation heatmaps. |

---
