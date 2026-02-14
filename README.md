# Day 15 Mini Project – End-to-End Data Cleaning

## Project Overview

In this mini project, I built a simple end-to-end data cleaning pipeline using Python and pandas.
The main goal was to take raw and messy data and turn it into a clean dataset that is ready for analysis or machine learning.

## Dataset Problems

From the first inspection, I noticed several issues:

* Wrong data types for numeric and date columns
* Missing values in important numeric features
* Outliers, especially in the income column
* Different spellings and formats for city names
* Datetime values without a unified timezone

## Cleaning Steps

The `cleaning_step` function performs these steps:

1. **Type Conversion**
   Convert `age` and `income` to numeric and `signup_time` to datetime so calculations and time analysis work correctly.

2. **Handling Missing Values**

   * Fill missing `age` with the **mean** because age is close to normally distributed.
   * Fill missing `income` with the **median** since income is skewed and affected by extreme values.
   * Create `missing_per_row` to track missing values in each row.

3. **Outlier Treatment**

   * Remove unrealistic ages using **Z-score**.
   * Limit extreme income values using **IQR capping** without deleting records.

4. **Text Cleaning**
   Standardize city names by trimming spaces, converting to lowercase, removing symbols, and applying canonical mapping to avoid duplicate categories.

5. **Datetime Standardization**
   Convert `signup_time` to a **UTC timezone-aware** datetime for consistent time comparison.

## Final Result

After cleaning, the dataset becomes:

* Clean and consistent
* Free from major missing or extreme issues
* Ready for reliable analysis or modeling

## Cleaning Decisions

```python
cleaning_decisions = {
  "age": "Converted to numeric for calculations, filled missing values with the mean because age is roughly normally distributed, and removed extreme values using Z-score to keep ages realistic.",
  "income": "Converted to numeric for analysis, filled missing values with the median since income is skewed and affected by high values, and capped outliers using IQR to reduce their impact without removing records.",
  "city": "Cleaned and standardized city names to avoid duplicate categories with different spellings and make categorical analysis more accurate.",
  "signup_time": "Converted to datetime and unified the timezone to UTC to ensure consistent and correct time-based comparisons."
}
```

This project shows how Week 1–3 data cleaning techniques can be applied in a real, simple, and practical workflow.
