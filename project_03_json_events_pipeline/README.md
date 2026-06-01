# Project 3 — JSON Events Pipeline

## Goal

Build an end-to-end Medallion Architecture pipeline using JSON event data.

## Technologies Used

- Databricks
- Python
- PySpark
- Spark SQL
- Delta Lake

## Pipeline Architecture

JSON Files → Bronze → Silver → Gold

## Bronze Layer

- Read raw JSON event files
- Preserve original structure
- Store data in a Bronze Delta table

## Silver Layer

- Clean and standardize event data
- Select required columns
- Apply data quality transformations
- Save results to a Silver Delta table

## Gold Layer

- Aggregate event metrics
- Create business-ready datasets
- Save results to a Gold Delta table

## Skills Demonstrated

- JSON data ingestion
- PySpark DataFrame transformations
- Delta Lake table creation
- Medallion Architecture
- Data quality processing
- Business aggregation
- Spark SQL

## Outcome

An end-to-end Bronze, Silver and Gold data pipeline was built using Databricks and PySpark, transforming raw JSON event data into analytics-ready datasets.
