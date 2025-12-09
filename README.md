# SQL-data-cleaning-project 
# Dirty Café Sales Data Cleaning Project (PostgreSQL)

## Overview
This project demonstrates a full end-to-end data-cleaning workflow using PostgreSQL.  
The dataset comes from a fictional café with inconsistent, messy, and poorly typed transactional data.  

The goal is to transform the raw dataset into a clean, analysis-ready table, apply data quality checks, and perform exploratory analysis — all using SQL.

---

## Objectives
- Load raw CSV into a PostgreSQL database  
- Clean incorrect data types (strings stored as numbers, invalid dates, etc.)  
- Standardize text fields (items, payment methods, locations)  
- Handle missing and invalid values  
- Deduplicate rows  
- Build a fully cleaned table for downstream analysis  
- Generate insights using SQL-based EDA  

---

## Dataset Description

**Raw table:** `dirty_cafe_sales`  
Columns include:

- `transaction_id`
- `item`
- `quantity_ren` (dirty — stored as text)
- `price_per_unit` (dirty — text)
- `total_amount_spent` (dirty — text)
- `payment_method`
- `location`
- `transaction_date` (dirty — invalid values such as "unknown")

Issues identified:
- Numeric fields stored as text  
- Date column contains invalid strings  
- Inconsistent casing (e.g., “cash”, “CASH”, “ Cash ”)  
- Extra spaces in text columns  
- Missing values in multiple columns  

---

## Cleaning Approach

### 1. Create a clean target table  
A new table `clean_cafe_sales` is created for cleaned, validated rows.

### 2. Data type correction  
- Convert quantity → INTEGER  
- Convert unit price and total → NUMERIC  
- Convert valid date strings → DATE  

### 3. Text normalization  
- Trim whitespace  
- Normalize casing  
- Remove extra spaces using `REGEXP_REPLACE`  

### 4. Missing and invalid value handling  
- Rows with invalid numeric or date fields are excluded from the clean table  
- Clean table contains only valid, usable records  

### 5. Deduplication  
Duplicate `transaction_id` rows are removed by selecting the first valid record.

### 6. Data validation checks  
Validation queries ensure the cleaned table is accurate and free of type issues.

---

## Project Files

### `/sql/create_raw_table.sql`
Creates the initial table and loads the CSV.

### `/sql/clean_data.sql`
Full cleaning transformation pipeline.

### `/sql/validation_checks.sql`
Data-quality and completeness checks.

### `/sql/analysis_queries.sql`
Exploratory Data Analysis (EDA) queries.

---

## Example Insights

Included in `analysis_queries.sql`:
- Top-selling items  
- Revenue by month  
- Most common payment methods  
- Daily and weekly transaction trends  

---

## How to Reproduce This Project

1. Install PostgreSQL  
2. Create a new database  
3. Run `create_raw_table.sql`  
4. Run `clean_data.sql`  
5. Optional: export clean data using `\copy`  
6. Execute `analysis_queries.sql` to reproduce insights  

---

## Skills Demonstrated
- SQL data cleaning  
- Data type handling  
- String manipulation  
- Conditional logic and CASE expressions  
- Deduplication strategies  
- EDA in SQL  
- Repository structuring for analytics projects  

---

## Final Notes
This project is designed to demonstrate practical, job-ready SQL skills for Data Analyst roles.  
All SQL is modular and can be reused in larger data-cleaning pipelines.

