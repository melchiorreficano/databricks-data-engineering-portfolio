# Project 1 — CSV Bronze Ingestion

## Goal
Ingest a CSV sales file into Databricks using PySpark and save it as a Bronze Delta table.

---

## Technologies Used

- Databricks
- Python
- PySpark
- Spark SQL
- Delta Lake

---

## Pipeline Architecture

CSV File
→ Spark DataFrame
→ Bronze Delta Table
→ SQL Analysis

---

## What I Practised

- Reading CSV files with PySpark
- Understanding DataFrames
- Understanding schemas
- Saving Delta tables
- Running SQL queries
- Basic data engineering pipeline concepts

---

## PySpark Code Used

```python
df = spark.read.option("header", True).option("inferSchema", True)\
    .csv("/Volumes/workspace/default/databricks_files/sales_orders.csv")

display(df)

df.write.format("delta").mode("overwrite").saveAsTable("bronze_sales_orders")
```

---

## SQL Queries Used

```sql
SELECT * FROM bronze_sales_orders;

SELECT COUNT(*) FROM bronze_sales_orders;

SELECT country, COUNT(*) AS total_orders
FROM bronze_sales_orders
GROUP BY country;

SELECT SUM(quantity * unit_price) AS total_revenue
FROM bronze_sales_orders;
```

---

## What I Learned

I learned how to ingest raw CSV data into Databricks, create a DataFrame, save it as a Bronze Delta table, and query it using SQL.
