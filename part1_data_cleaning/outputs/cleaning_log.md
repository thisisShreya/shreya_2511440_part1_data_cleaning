# Cleaning Log

---

# 1. Objective

The objective of this project was to clean and validate a retail sales dataset by identifying and correcting data quality issues. The cleaned dataset was prepared for business reporting and analysis by applying business validation rules, creating calculated columns, and documenting all cleaning activities.

The original dataset remained unchanged throughout the project.

---

# 2. Issues Identified

The following data quality issues were identified during the initial inspection of the dataset.

## 2.1 Text Formatting Issues

Several text fields contained inconsistent formatting.

Issues identified included:

- Leading spaces
- Trailing spaces
- Multiple spaces between words
- Inconsistent capitalization
- Similar values written in different formats
- Missing text values

Affected columns included:

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

---

## 2.2 Date Issues

The Order Date and Ship Date columns contained inconsistent date formats.

The following issues were identified:

- Mixed date formats
- Missing date values
- Ship Date occurring before Order Date
- Invalid date entries

These records were reviewed and validated before analysis.

---

## 2.3 Duplicate Records

Duplicate analysis identified two types of duplicates.

### Exact Duplicate Rows

Rows containing identical values across all columns.

### Duplicate Order IDs

Order IDs appearing multiple times with conflicting information.

These records were retained and flagged for manual review instead of being deleted.

---

## 2.4 Missing Values

Missing values were identified in several business-critical fields.

Examples included:

- Region
- Ship Mode
- Discount

Business rules were applied to handle these missing values.

---

## 2.5 Discount Validation Issues

The following discount issues were found:

- Missing discount values
- Negative discount values
- Discount values outside the acceptable business range

Invalid discount records were flagged for review.

---

## 2.6 Order Status Issues

Order Status values contained inconsistent spellings and formatting.

Examples included:

- completed
- COMPLETED
- Completed

All values were standardized into a single format.

---

## 2.7 Payment Status Issues

Payment Status values also contained inconsistent formatting.

Examples included:

- paid
- Paid
- PAID

All payment status values were standardized.

---

# 3. Cleaning Actions Performed

The following cleaning actions were completed using Microsoft Excel.

---

## 3.1 Text Cleaning

The following Excel features were used:

- TRIM
- PROPER
- SUBSTITUTE
- Find and Replace

Cleaning actions included:

- Removing leading spaces
- Removing trailing spaces
- Removing extra spaces
- Standardizing capitalization
- Correcting inconsistent text values
- Standardizing category names
- Standardizing customer segments
- Standardizing regions
- Standardizing shipping modes
- Standardizing payment status
- Standardizing order status

---

## 3.2 Date Cleaning

The following actions were completed:

- Converted all dates into a consistent Excel date format.
- Verified Order Date values.
- Verified Ship Date values.
- Identified missing dates.
- Flagged Ship Dates occurring before Order Dates.
- Calculated Shipping Delay Days.

---

## 3.3 Duplicate Handling

Duplicate records were handled carefully.

Actions performed:

- Exact duplicate rows were removed.
- Duplicate Order IDs with conflicting information were retained.
- Conflicting records were marked for manual review.
- Duplicate summary prepared in the Data Quality Report.

---

## 3.4 Missing Value Treatment

The following business rules were applied.

| Field | Action Taken |
|--------|--------------|
| Region | Filled with "Unknown" |
| Ship Mode | Filled with "Unknown" |
| Discount | Replaced with 0 only when other sales information was valid |

---

## 3.5 Discount Validation

Discount values were checked for:

- Missing values
- Negative values
- Invalid values
- Values exceeding the acceptable business range

Invalid discount records were flagged rather than removed.

---

## 3.6 Business Validation

The cleaned dataset was validated using the following business rules.

| Business Rule | Action Taken |
|--------------|--------------|
| Missing Region | Filled with Unknown |
| Missing Ship Mode | Filled with Unknown |
| Missing Discount | Replaced according to business rule |
| Negative Discount | Flagged as Invalid |
| Invalid Discount | Flagged for review |
| Ship Date before Order Date | Flagged |
| Cancelled Orders | Excluded from completed sales summaries |
| Failed Payments | Excluded from completed sales summaries |
| Refunded Orders | Reported separately |

---

# 4. Calculated Columns Created

The following calculated columns were added to the cleaned dataset.

| Column | Purpose |
|---------|---------|
| cleaned_discount | Standardized discount value |
| calculated_sales | Recalculated sales amount |
| calculated_profit | Calculated profit |
| profit_margin | Profit percentage |
| shipping_delay_days | Delivery time in days |
| order_month | Month extracted from Order Date |
| order_year | Year extracted from Order Date |
| data_quality_flag | Indicates Clean, Warning or Invalid |

---

# 5. Assumptions Made

The following assumptions were applied during the data cleaning process.

1. Missing **Region** values were replaced with **"Unknown"** to preserve records for analysis.

2. Missing **Ship Mode** values were replaced with **"Unknown"** because the actual shipping method could not be determined from the available data.

3. Missing **Discount** values were replaced with **0** only when the remaining sales-related fields were complete and valid.

4. Duplicate **Order IDs** containing conflicting information were retained and flagged instead of being removed because the correct record could not be identified automatically.

5. Cancelled and Failed Payment orders were excluded from completed sales summaries to ensure accurate business reporting.

6. Refunded orders were summarized separately from completed business transactions.

7. Sales and Profit calculations were performed using the cleaned dataset after applying all validation rules.

---

# 6. Records Removed

The following records were removed during the cleaning process.

| Action | Description |
|---------|-------------|
| Exact Duplicate Rows | Removed after verification |
| Conflicting Duplicate Order IDs | Not removed; retained for manual review |

No valid business records were deleted during the cleaning process.

Only exact duplicate records were removed.

---

# 7. Records Flagged

Records containing business rule violations were retained but flagged for review.

Examples include:

- Missing Region values
- Missing Ship Mode values
- Invalid Discount values
- Negative Discount values
- Ship Date before Order Date
- Duplicate Order IDs
- Cancelled Orders
- Failed Payment Orders

The **Data Quality Flag** column was used to classify records as:

| Flag | Description |
|------|-------------|
| Clean | Record contains no identified issues |
| Warning | Minor issues corrected during cleaning |
| Invalid | Record contains significant business rule violations |

---

# 8. Data Validation Summary

The cleaned dataset was validated using multiple quality checks.

Validation included:

- Text consistency
- Date validation
- Duplicate verification
- Missing value checks
- Discount validation
- Sales calculation verification
- Profit calculation verification
- Business rule validation

These validation checks improved the overall reliability of the dataset for business reporting.

---

# 9. Business Rules Verification

The following business rules were verified before preparing the final reports.

| Validation Rule | Status |
|-----------------|--------|
| Missing Region handled | Completed |
| Missing Ship Mode handled | Completed |
| Missing Discount handled | Completed |
| Invalid Discount identified | Completed |
| Duplicate Records verified | Completed |
| Duplicate Order IDs reviewed | Completed |
| Shipping Delay calculated | Completed |
| Profit Margin calculated | Completed |
| Order Month extracted | Completed |
| Order Year extracted | Completed |
| Data Quality Flag assigned | Completed |

---

# 10. Final Dataset Review

After all cleaning activities were completed, the dataset was reviewed to ensure:

- Required columns were present.
- Calculated columns were added correctly.
- Duplicate records were handled appropriately.
- Missing values were addressed according to business rules.
- Date values were standardized.
- Pivot reports could be generated without errors.
- Data Quality Report accurately summarized identified issues.

---

# 11. Limitations

Although the dataset was successfully cleaned, the following limitations remain.

- Some duplicate Order IDs require manual business verification.
- Original source data may contain business-specific exceptions that cannot be identified automatically.
- Missing values were handled according to assignment requirements and available information.
- Business conclusions are based only on the provided dataset.
- Some business decisions may require additional organizational context that was not available in the dataset.

---


# 12. Conclusion

The retail sales dataset was successfully cleaned, validated, and transformed into a business-ready dataset using Microsoft Excel.

All major data quality issues—including inconsistent text formatting, missing values, duplicate records, invalid discounts, and date inconsistencies—were identified and addressed according to the specified business rules.

The cleaned dataset includes additional calculated columns, improved data consistency, and validation flags that support reliable business reporting and analysis. Comprehensive documentation, quality reports, pivot summaries, and screenshots were also prepared to provide a complete and well-documented project submission.

The final deliverables satisfy the assignment requirements and provide a structured workflow for data cleaning, validation, and Excel-based business reporting.

---
