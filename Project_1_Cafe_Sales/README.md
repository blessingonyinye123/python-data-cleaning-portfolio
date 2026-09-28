# Cafe Sales Data Cleaning & Revenue Quality Audit

## Project Overview
This project performs a comprehensive data cleaning, standardization, and quality assurance pipeline on an operational cafe sales dataset. The raw dataset contained inconsistent formatting, missing item attributes, structural gaps in sales records, and erroneous price calculations that impacted financial reporting accuracy.

## Tech Stack
* **Language:** Python
* **Libraries:** Pandas, NumPy
* **Environment:** Anaconda Jupyter Notebooks

---

## Data Quality & Impact Summary

* **Missing Data Resolution:** Identified and imputed missing item names and prices using historical item lookup mappings.
* **Format Standardization:** Standardized mixed-date formats and normalized payment method text for clean database integration.
* **Financial Integrity:** Corrected miscalculated line-item totals and removed invalid transaction entries.
* **Header Standardization:** Converted all mixed-case column names to consistent `snake_case`.

---

## Detailed Data Cleaning & Transformation Pipeline

### 1. Header & Text Normalization
* Standardized all column headers into `snake_case` format for seamless Python and SQL querying.
* Normalized categorical fields (e.g., payment methods, item descriptions) to fix inconsistent capitalization and leading/trailing whitespace.

### 2. Missing Value & Price Imputation
* Audited incomplete transaction records where item details or prices were omitted.
* Applied dictionary-based lookups and conditional logic to fill missing prices based on item categories.

### 3. Date & Timestamp Parsing
* Converted varied string representations of transaction dates into unified `YYYY-MM-DD` datetime formats.
* Validated chronological integrity across daily transaction batches.

### 4. Financial Audit & Feature Consistency
* Verified line-item totals (`quantity * unit_price = total_spent`) and corrected computational discrepancies.
* Ensured zero or negative values in price/quantity fields were validated or handled appropriately.

---

## Execution Workflow

The pipeline runs directly within Jupyter Notebook using standard Python data analysis tools:

* **Input Data:** The raw sales dataset is loaded into a Pandas DataFrame.
* **Audit & Imputation:** Python scripts clean textual noise, standardize dates, and impute missing values.
* **Export:** Executing the notebook exports the cleaned, standardized dataset for downstream financial reporting and analytics.

---

## Dataset Files
* **Raw Input:** [`dirty_cafe_sales.csv`](./dirty_cafe_sales.csv)
* **Cleaned Output:** [`cleaned_cafe_sales.csv`](./cleaned_cafe_sales.csv)
