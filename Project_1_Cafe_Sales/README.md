# Dirty Cafe Sales — End-to-End Data Cleaning Project

## Project Overview
This project focuses on transforming a raw, corrupted retail sales dataset (**10,000 records**) into a structured, validated, and analysis-ready dataset. The data contained severe real-world data quality issues, including mismatched data types, hidden text errors, missing numeric values, and inconsistent categorical entries.

Using **Python** and **pandas**, I developed a programmatic cleaning pipeline that systematically audited, repaired, and validated the dataset while preserving maximum data integrity.

---

## Tools & Technologies Used
* **Language:** Python
* **Libraries:** `pandas`, `numpy`
* **Environment:** Jupyter Notebook / Anaconda

---

## Key Data Quality Issues & Solutions

### 1. Messy Column Headers
* **Issue:** Headers contained spaces and uppercase characters (e.g., `Price Per Unit`).
* **Solution:** Renamed all headers to standard `snake_case` using `.str.lower()` and `.str.replace()`.
* **Impact:** Prevented syntax errors and streamlined pandas queries.

### 2. Hidden Text Placeholders
* **Issue:** Missing values were masked as strings like `'ERROR'`, `'UNKNOWN'`, `'N/A'`, or blank spaces.
* **Solution:** Converted all invalid placeholder strings into true `NaN` objects using `np.nan`.
* **Impact:** Uncovered the true extent of missing data for accurate auditing.

### 3. Incorrect Data Types
* **Issue:** Numeric values (`quantity`, `price_per_unit`, `total_spent`) and dates were stored as raw text (`str`).
* **Solution:** Cast numeric columns to `float64` via `pd.to_numeric(errors='coerce')` and `transaction_date` to `datetime64`.
* **Impact:** Enabled numerical computations, aggregation, and time-series filtering.

### 4. Missing Numeric Values
* **Issue:** Over 500 records had missing values across linked financial columns.
* **Solution:** Applied mathematical imputation using the relationship: `total_spent = quantity * price_per_unit`.
* **Impact:** Successfully recovered over 450 numeric entries without dropping data.

### 5. Missing Menu Item Names
* **Issue:** 969 rows were missing the categorical `item` name.
* **Solution:** Built a lookup dictionary mapping fixed unit prices back to menu items (e.g., $2.00 → Coffee, $1.00 → Cookie).
* **Impact:** Recovered 963 missing item names (99.4% item recovery rate).

### 6. Categorical Inconsistencies
* **Issue:** Whitespace noise and missing records in `payment_method` and `location`.
* **Solution:** Stripped padding, standardized text to Title Case, and imputed unassigned values as `'Unknown'`.
* **Impact:** Created consistent categorical dimensions for downstream analysis and dashboarding.

---

## Summary of Results
* **Initial Records:** 10,000 rows, 8 columns (all raw string types)
* **Final Clean Records:** 9,485 valid rows (94.85% data preservation rate)
* **Missing Values Remaining:** 0 missing values across key operational columns
* **Output Artifact:** Exported as `cleaned_cafe_sales.csv`

---

## How to Run
1. Clone this repository.
2. Install dependencies: `pip install pandas numpy`
3. Launch Jupyter Notebook and run `Cafe_Sales_Data_Cleaning.ipynb`.
