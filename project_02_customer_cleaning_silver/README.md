# Project 2 — Customer Cleaning Silver Pipeline

## Goal

Read dirty customer data, clean and standardize it using PySpark, and save the results as a Silver Delta table.

---

## Technologies Used

- Databricks
- Python
- PySpark
- Spark SQL
- Delta Lake

---

## Pipeline Architecture

Dirty Customer CSV
→ Raw DataFrame
→ Data Cleaning
→ Standardization
→ Silver Delta Table

---

## What I Practised

- Reading CSV files with PySpark
- Data cleaning
- Handling NULL values
- Data quality checks
- Standardizing text values
- Creating Silver tables
- Medallion Architecture (Bronze → Silver)

---

## PySpark Functions Used

- lower()
- col()
- filter()
- withColumn()
- when()
- isin()
- otherwise()

---

## PySpark Code Used

```python
from pyspark.sql.functions import lower, col, when

df = spark.read.option("header", True).option("inferSchema", True)\
    .csv("/Volumes/workspace/default/databricks_files/customers_dirty.csv")

df_clean = df.withColumn("email", lower(col("email")))

df_clean = df_clean.filter(col("email").contains("@"))

df_clean = df_clean.filter(col("first_name") != "")

df_clean = df_clean.withColumn(
    "country_clean",
    when(col("country").isin("IT", "Italy"), "Italy")
    .when(col("country").isin("UK", "United Kingdom", "uk"), "United Kingdom")
    .otherwise("Unknown")
)

display(df_clean)
```

---

## Data Quality Decisions

Not all missing data is treated the same.

Examples:

- Missing email → Critical field → Remove row
- Missing customer identifier → Critical field → Remove row
- Missing signup date → Optional field → Keep NULL value

This is an important concept in real-world data engineering because data quality decisions affect reporting, dashboards, and analytics.

---

## What I Learned

I learned how data engineers clean and standardize messy customer data before it is used by dashboards, analysts, and business users.

I also learned the difference between:

- Critical fields (email, customer identifiers)
- Optional fields (such as signup dates)

and how data quality decisions affect downstream analytics.

I learned how the Silver layer of the Medallion Architecture contains clean, trusted, and reusable business data.
