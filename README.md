# ETL-Pipeline-Using-AirFlow
ETL Pipeline with Dockerized Apache Airflow
📊 Sales Data ETL Architecture

A modular, containerized ETL pipeline built using Apache Airflow, PostgreSQL, and Docker, designed for reproducibility, operational clarity, and seamless BI integration with Power BI.

This project demonstrates an end-to-end Bronze–Silver–Gold data architecture for processing sales data and enabling analytics-ready reporting.

🧩 Business Problem

Manual processing of daily sales data using Microsoft Excel was:

Time-consuming

Error-prone

Delaying actionable insights for stakeholders

Sales and Marketing teams lacked timely access to clean, reliable data for decision-making.

💡 Solution

An automated ETL pipeline was developed to:

Eliminate manual data handling

Enforce data quality and validation rules

Standardize transformations

Accelerate the data-to-insight cycle

Enable faster, data-driven decisions through Power BI

🔄 ETL Workflow

The Airflow DAG sales_etl_pipeline orchestrates the following tasks:

Task Name	Description
init_schema	Creates PostgreSQL schemas and tables using SQL scripts
load_master_data	Loads reference/master data from CSV files
run_etl_pipeline	Executes the full ETL flow (Bronze → Silver → Gold)
grant_powerbi_access	Grants Power BI users access to Gold-layer tables

Each task is modular, reusable, and independently testable, with audit logging built into the ETL process.

🧪 ETL Layer Design
🥉 Bronze Layer

Reads raw sales CSV files from data/raw/

Adds ingestion timestamps

Loads raw data into the Bronze schema in PostgreSQL

🥈 Silver Layer

Extracts the latest batch from Bronze

Performs:

Data quality checks

Deduplication

Business rule validation

Loads cleaned and validated data into the Silver schema

🥇 Gold Layer

Aggregates total sales from the latest Silver batch

Creates fact and dimension tables

Loads analytics-ready data into the Gold schema

Serves as the reporting layer for BI tools

📈 BI & Analytics Integration

Power BI connects directly to PostgreSQL

Gold-layer tables are used for dashboards and reporting

Access is automatically granted after successful ETL execution via grant_powerbi_access

🧪 Data Generation

Sales data is synthetically generated using a Python script for reproducible testing:

data/raw/generate_data.py
