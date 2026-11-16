# PerfectPetClub Customer Churn – Data Audit

## 1. Project Overview

This document records the data inspection, quality checks, cleaning and transformation activities performed for the PerfectPetClub Customer Churn project.

The objective of the data audit was to assess the quality and suitability of the source data before using it for machine learning.

## 2. Data Sources

The ETL pipeline uses data extracted from:

- SQLite database – structured customer and transactional information.
- CSV files – supplementary CRM, server activity and customer survey information.

The different sources were inspected and prepared for integration into a single customer-level dataset.

## 3. Data Inspection

The source data was examined to understand:

- Dataset structure and column names.
- Data types and field consistency.
- Missing and duplicate records.
- Relationships between customer records.
- Suitability of available variables for churn prediction.

Customer identifiers were used to support the integration of relevant information from different sources.

## 4. Data Cleaning

The following data preparation activities were performed:

- Inspected and handled missing values.
- Checked for duplicate records.
- Standardised data types where required.
- Removed personally identifiable information, including email addresses.
- Prepared categorical variables for machine learning.
- Checked the consistency of customer-level records.

## 5. Feature Engineering

Additional customer-level features were created from the available source data.

Examples include:

- Total orders.
- Total spend.
- Average order value.
- Total logins.
- Total reviews.
- Average customer rating.
- Total CRM interactions.
- Satisfaction score.
- Days since last order.

The `days_since_last_order` feature was calculated using the maximum `last_order_date` available in the dataset as the reference date.

Categorical income values were converted into numerical indicator columns through one-hot encoding.

## 6. Churn Target Definition

The target variable was created using the `auto_renew` field:

- `churn = 1` when `auto_renew = 0`.
- `churn = 0` when `auto_renew` is not 0.

The original `auto_renew` column was removed after creating the target variable to avoid directly including the source target field among the predictors.

## 7. Data Quality Audit Results

The final processed dataset was checked after ETL.

| Audit Metric | Result |
|---|---:|
| Total customer records | 221 |
| Total columns | 34 |
| Predictor features | 33 |
| Target variable | 1 |
| Missing values | 0 |
| Duplicate rows | 0 |
| Churn = 0 | 135 |
| Churn = 1 | 86 |

The final dataset contains 221 customer records and 34 columns, consisting of 33 predictor features and one churn target.

## 8. Data Storage

The cleaned and transformed dataset was saved in Parquet format for efficient use in the machine learning stage.

Output file:

`data/processed/perfectpetclub_processed.parquet`

Parquet was selected because it provides a structured, columnar storage format suitable for analytical processing with Apache Spark.

## 9. Data Quality Considerations and Limitations

Although the final dataset contains no missing values or duplicate rows, several considerations remain:

- The dataset contains only 221 customer records, which limits the amount of training data available.
- The churn target is derived from the `auto_renew` field and therefore represents the project's operational definition of churn.
- The `days_since_last_order` feature has a substantial relationship with the target and requires further investigation to ensure that it is available at the intended prediction time.
- The class distribution is not perfectly balanced, with 135 non-churn and 86 churn records.
- Further validation using a larger and independent dataset would improve confidence in the results.

## 10. Conclusion

The data audit confirms that the ETL pipeline produced a processed dataset containing 221 customer records, 33 predictor features and one churn target. Missing values and duplicate rows were absent from the final output. The dataset was successfully saved in Parquet format and prepared for the subsequent PySpark machine learning workflow.