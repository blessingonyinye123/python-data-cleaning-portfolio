# Healthcare Diabetes Data Cleaning & Quality Audit

## Project Overview
This project performs an end-to-end data cleaning, quality audit, and feature engineering pipeline on a noisy clinical records dataset used for diabetes risk assessment. The raw dataset suffered from extensive row duplication and biologically impossible zero values across critical physiological metrics.

## Tech Stack
* **Language:** Python
* **Libraries:** Pandas, NumPy
* **Environment:** Anaconda Jupyter Notebooks

---

## Data Quality & Impact Summary

* **Total Records:** Reduced from 2,768 rows to 778 unique patient profiles by purging 1,990 artificial duplicates (71.8% reduction).
* **Missing Values:** Replaced hidden zero values (up to 48.5% missing in key metrics like insulin) with cohort-conditioned medians, leaving 0 missing values.
* **Engineered Features:** Added 2 clinical risk features (`bmi_category` and `age_group`).
* **Header Standardization:** Converted all mixed-case column names to clean `snake_case`.

---

## Detailed Data Cleaning & Transformation Pipeline

### 1. Deduplication Audit
* Identified 1,990 exact duplicate patient rows resulting from redundant data ingestion.
* Audited and purged duplicates to retain 778 unique patient clinical profiles.

### 2. Hidden Zero Detection & Audit
Physiological indicators cannot naturally be zero in living patients. Uncovered hidden missing values masked as zeros across 5 key features:
* `insulin`: 374 missing values (48.46%)
* `skin_thickness`: 227 missing values (29.43%)
* `blood_pressure`: 35 missing values (4.63%)
* `bmi`: 11 missing values (1.41%)
* `glucose`: 5 missing values (0.64%)

### 3. Cohort-Stratified Median Imputation
* Rather than global mean/median filling (which skews distribution), missing values were imputed using outcome-conditioned medians grouped by diabetic status (`outcome` = 0 vs. 1).
* Preserved natural variance and physiological distribution differences between non-diabetic and diabetic cohorts.

### 4. Risk Factor Binned Feature Engineering
* **`bmi_category`:** Binned continuous BMI readings into standard clinical classifications:
  * Underweight (< 18.5)
  * Normal (18.5 – 24.9)
  * Overweight (25.0 – 29.9)
  * Obese (≥ 30.0)
* **`age_group`:** Segmented patient age into cohort risk brackets: `21–30`, `31–40`, `41–50`, and `50+`.

---

## Execution Workflow

The pipeline runs directly within Jupyter Notebook using standard Python data analysis tools:

* **Input Data:** The raw file `Healthcare-Diabetes.csv` is loaded into a Pandas DataFrame.
* **Audit & Imputation:** Python scripts identify duplicate records, handle hidden zero values, and perform group-stratified medians.
* **Export:** Executing the notebook outputs the standardized dataset directly to `cleaned_healthcare_diabetes.csv`.

---

## Dataset Files
* **Raw Input:** [`Healthcare-Diabetes.csv`](./Healthcare-Diabetes.csv)
* **Cleaned Output:** [`cleaned_healthcare_diabetes.csv`](./cleaned_healthcare_diabetes.csv)
