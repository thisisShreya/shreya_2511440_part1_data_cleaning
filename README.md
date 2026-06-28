
## Problem Summary

This project focuses on cleaning, validating, and analyzing a retail sales dataset exported from multiple internal business systems. The original dataset contained inconsistent text formatting, mixed date formats, duplicate records, missing values, invalid discount values, and calculation inconsistencies.

The objective of this project was to transform the raw dataset into a clean, analysis-ready dataset by applying business validation rules, creating calculated columns, documenting data quality issues, and generating business summary reports using Microsoft Excel.

---

# Dataset Description

| Property | Value |
|----------|-------|
| Dataset Name | raw_orders.xlsx |
| Original Records | 932 |
| Original Columns | 21 |
| Cleaned Records | 912 |
| Total Columns After Cleaning | 29 |
| Output Dataset | cleaned_orders.xlsx |

## Original Dataset Columns

- order_id
- order_date
- ship_date
- customer_id
- customer_name
- segment
- region
- state
- city
- category
- sub_category
- product_name
- ship_mode
- quantity
- unit_price
- discount
- sales
- cost
- profit
- payment_status
- order_status

---

# Tools Used

- Microsoft Excel
- Excel Tables
- Filters and Sorting
- Find and Replace
- Conditional Formatting
- Remove Duplicates
- Pivot Tables
- Excel Functions
  - TRIM
  - PROPER
  - SUBSTITUTE
  - IF
  - YEAR
  - TEXT
- GitHub

---

# Cleaning Steps Performed

## Step 1 – Preserve Raw Data

The original dataset (`raw_orders.xlsx`) was kept unchanged throughout the project.

A separate copy named `cleaned_orders.xlsx` was created, and all cleaning operations were performed only on this copy.

---

## Step 2 – Text Cleaning

The following fields were cleaned:

- customer_name
- segment
- region
- state
- city
- category
- sub_category
- ship_mode
- payment_status
- order_status

The following cleaning operations were performed:

- Removed leading spaces
- Removed trailing spaces
- Removed extra spaces between words
- Standardized capitalization
- Corrected inconsistent spellings
- Standardized category names
- Removed unnecessary characters wherever applicable

---

## Step 3 – Date Cleaning

The following columns were standardized:

- order_date
- ship_date

Cleaning included:

- Converting all dates into a consistent Excel date format
- Identifying invalid date values
- Identifying missing dates
- Identifying ship dates occurring before order dates
- Calculating shipping delay in days
- Creating Order Month
- Creating Order Year

---

## Step 4 – Duplicate Handling

Duplicate analysis was performed before removing records.

The following validations were carried out:

- Exact duplicate rows identified
- Duplicate Order IDs checked
- Conflicting duplicate records retained for review
- Exact duplicate rows removed

Duplicate handling details are documented in the Data Quality Report.

---

## Step 5 – Missing Value Treatment

Business rules were applied as follows:

| Missing Field | Action Taken |
|--------------|--------------|
| Region | Filled with "Unknown" |
| Ship Mode | Filled with "Unknown" |
| Discount | Replaced with 0 only when other sales values were valid |

---

## Step 6 – Discount Validation

Discount values were validated for:

- Missing values
- Negative discounts
- Invalid discount values
- Discounts outside the acceptable business range

Invalid discount records were flagged for review instead of being silently removed.

---

## Step 7 – Business Rule Validation

The following business rules were applied:

- Cancelled orders were excluded from completed sales summaries.
- Failed payment orders were excluded from completed sales summaries.
- Refunded orders were summarized separately.
- Invalid shipping records were flagged.
- Missing Region values were replaced with "Unknown".
- Missing Ship Mode values were replaced with "Unknown".
- Missing Discount values were handled according to business rules.
- Data Quality Flags were assigned to every record.

---

# Calculated Columns Added

The following calculated columns were added to the cleaned dataset.

| Column | Description |
|---------|-------------|
| cleaned_discount | Standardized discount value |
| calculated_sales | Quantity × Unit Price × (1 − Discount) |
| calculated_profit | Calculated Sales − Cost |
| profit_margin | Calculated Profit ÷ Calculated Sales |
| shipping_delay_days | Difference between Ship Date and Order Date |
| order_month | Month extracted from Order Date |
| order_year | Year extracted from Order Date |
| data_quality_flag | Indicates Clean, Warning, or Invalid |
| quality_issues | Description of identified issues |

---

# Business Rules Applied

| Business Rule | Action |
|--------------|--------|
| Missing Region | Filled with Unknown |
| Missing Ship Mode | Filled with Unknown |
| Missing Discount | Treated as 0 where appropriate |
| Negative Discount | Flagged as Invalid |
| Invalid Discount | Flagged for Review |
| Ship Date before Order Date | Flagged as Invalid Shipping Record |
| Cancelled Orders | Excluded from completed sales summary |
| Failed Payment Orders | Excluded from completed sales summary |
| Refunded Orders | Reported separately |

---

# Summary of Data Quality Issues

The following data quality issues were identified during the cleaning process:

| Issue Identified | Status |
|------------------|--------|
| Extra spaces in text fields | Corrected |
| Inconsistent capitalization | Corrected |
| Duplicate records | Identified and handled |
| Duplicate Order IDs | Flagged for review |
| Missing Region values | Filled with "Unknown" |
| Missing Ship Mode values | Filled with "Unknown" |
| Missing Discount values | Replaced according to business rules |
| Negative Discount values | Flagged as Invalid |
| Invalid Discount values | Flagged |
| Ship Date before Order Date | Flagged |
| Sales and Profit inconsistencies | Validated |

All identified issues were documented in the Data Quality Report.

---

# Pivot Reports Created

The following business reports were created in **pivot_summary.xlsx**.

## 1. Sales and Profit by Region

This report summarizes:

- Order Count
- Total Sales
- Total Profit
- Average Profit Margin

The report excludes cancelled and failed-payment orders to provide an accurate representation of completed business performance.

---

## 2. Sales and Profit by Category and Sub-Category

This report provides:

- Sales by Category
- Sales by Sub-Category
- Profit by Category
- Profit by Sub-Category

The report helps identify the highest-performing product categories.

---

## 3. Order Count by Ship Mode

This report summarizes the number of customer orders processed through each shipping method.

It helps evaluate shipping preferences and logistics performance.

---

## 4. Profit Margin by Customer Segment

This report compares profitability across different customer segments, allowing management to identify the most profitable customer groups.

---

## 5. Cancelled, Failed and Refunded Orders by Region

This report summarizes excluded business transactions by region, including:

- Cancelled Orders
- Failed Payment Orders
- Refunded Orders

This information helps identify operational issues across different regions.

---

## 6. Monthly Sales Trend

The Monthly Sales Trend report summarizes:

- Monthly Order Count
- Monthly Sales
- Monthly Profit

This report helps identify seasonal sales patterns and overall business growth.

---

# Key Business Insights

Based on the cleaned dataset and pivot analysis, the following business insights were identified:

- South region generated the highest completed sales among all regions.
- Technology products contributed the highest overall revenue.
- Consumer customers achieved the highest average profit margin.
- A number of orders contained invalid shipping dates that require further business review.
- Missing values and inconsistent text formatting significantly affected data quality before cleaning.
- Duplicate records and invalid discounts were successfully identified and documented.
- Excluding cancelled and failed-payment orders provided a more accurate representation of actual business performance.

---

# Assumptions

The following assumptions were made while cleaning the dataset:

- Missing Region values were replaced with **Unknown**.
- Missing Ship Mode values were replaced with **Unknown**.
- Missing Discount values were replaced with **0** only when the remaining sales information was valid.
- Duplicate Order IDs containing conflicting information were retained and flagged for manual review.
- Sales and Profit calculations were performed using the cleaned dataset.
- Business summaries were generated using completed and valid transactions.

---

# Limitations

Although every effort was made to improve data quality, the following limitations remain:

- Some duplicate Order IDs require manual business verification.
- Certain business-specific validation rules were not available in the dataset.
- Original source data may contain business exceptions that cannot be automatically identified.
- Sales and Profit calculations depend on the accuracy of the original Cost values.
- Business conclusions are based only on the provided dataset.

---

# Output Files

The project repository contains the following output files:

```
data/
├── raw_orders.xlsx
└── cleaned_orders.xlsx

outputs/
├── data_quality_report.xlsx
├── pivot_summary.xlsx
└── cleaning_log.md

screenshots/
├── raw_data_preview.png
├── cleaned_data_preview.png
├── pivot_summary_1.png
└── pivot_summary_2.png

README.md
```

---

# Screenshots Included

The repository includes the following screenshots:

| Screenshot | Description |
|------------|-------------|
| raw_data_preview.png | Raw dataset before cleaning |
| cleaned_data_preview.png | Cleaned dataset with calculated columns |
| pivot_summary_1.png | Sales and Profit by Region |
| pivot_summary_2.png | Monthly Sales Trend |

---

# Repository Structure

```
studentname_studentid_part1_data_cleaning/
│
└── part1_data_cleaning/
    ├── data/
    │   ├── raw_orders.xlsx
    │   └── cleaned_orders.xlsx
    │
    ├── outputs/
    │   ├── data_quality_report.xlsx
    │   ├── pivot_summary.xlsx
    │   └── cleaning_log.md
    │
    ├── screenshots/
    │   ├── raw_data_preview.png
    │   ├── cleaned_data_preview.png
    │   ├── pivot_summary_1.png
    │   └── pivot_summary_2.png
    │
    └── README.md
```

---

# Conclusion

The raw retail sales dataset was successfully cleaned, validated, and transformed into an analysis-ready dataset using Microsoft Excel. Text inconsistencies, missing values, duplicate records, invalid discounts, and date-related issues were identified and handled according to the specified business rules.

The cleaned dataset was further enhanced with calculated columns and validated using comprehensive data quality checks. Multiple pivot reports were created to summarize regional sales, category performance, customer profitability, shipping methods, excluded orders, and monthly sales trends.

The final outputs provide reliable, well-documented, and business-ready information that supports effective decision-making and demonstrates a complete data cleaning and reporting workflow.

---
