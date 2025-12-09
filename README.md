# Fault-gouge-shear-strength-dataset
The full Excel dataset is temporarily not publicly downloadable. 

It will be fully released after the associated manuscript is accepted. 

Researchers who are interested in using the data may contact the corresponding author.


Fault gouge shear strength dataset (Datasets A, B, C) compiled from literature for machine learning analysis


## Overview

This repository provides the fault gouge dataset used in our study on machine-learning–based prediction of fault gouge shear strength.

All data are stored in a single Excel file:

- **File:** `Fault gouge dataset.xlsx`  

The dataset is made publicly available to support reproducibility, reuse, and further research on data-driven modeling in geomechanics.

---

## File structure

**File:** `Fault gouge dataset.xlsx`

- **Row 1**  
  Header row containing the **names of all features** (input and target variables).

- **Column 1**  
  Sample identifiers / names.

- **Rows 2–352**  
  Data records for all samples, divided into three subsets:

  - **Rows 2–76**  
    **Dataset A** – fault gouge samples with **complete features**.  
    Used for:
    - Benchmarking classical ML models (GPR, SVR, DTR, KRR, MLP)  
    - Data preprocessing and feature correlation/SHAP analysis

  - **Rows 77–156**  
    **Dataset B** – fault gouge samples with **missing / incomplete features**.  
    Used for:
    - Models that can handle missing values (e.g., TabNet, TabPFN)  
    - Extending the training context beyond Dataset A

  - **Rows 157–352**  
    **Dataset C** – auxiliary **loess and clay** samples.  
    Used for:
    - Auxiliary tasks for TabPFN  
    - Providing physically similar but non–fault-gouge samples to enrich the task context  
    - Note: Dataset C is not used to build a separate model; it supports small-sample generalization.

---

## Columns

- **Row 1 (header):**  
  Contains the names of all variables, including:
  - Sample ID (first column)
  - Geometrical, petrophysical, and hydro-mechanical properties (input features)
  - Shear strength and other mechanical parameters (targets / labels)

- **Rows 2–352:**  
  Numeric values corresponding to these feature names.

---

## Example usage (Python / pandas)

```python
import pandas as pd

df = pd.read_excel("Fault gouge dataset.xlsx")

# Dataset A: rows 2–76 (zero-based index 1–75)
df_A = df.iloc[1:76, :]

# Dataset B: rows 77–156 (index 76–155)
df_B = df.iloc[76:156, :]

# Dataset C: rows 157–352 (index 156–351)
df_C = df.iloc[156:352, :]
