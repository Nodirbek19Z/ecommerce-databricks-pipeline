# 🚀 End-to-End E-Commerce Data Pipeline

An end-to-end Data Engineering pipeline built with **Databricks**, **PySpark**, and **Delta Lake**. This project demonstrates the implementation of the **Medallion Architecture (Bronze → Silver → Gold)** to process raw e-commerce transaction data into clean, business-ready analytical datasets.

---

## 📌 Project Overview

The primary goal of this project is to process and transform messy, raw e-commerce sales data into a reliable, structured "Single Source of Truth." 

Key features of the pipeline:
- **Data Ingestion:** Batch processing of raw transactional data into Delta tables.
- **Data Quality & Validation:** Schema enforcement, null handling, duplicate removal, and constraint checking.
- **Medallion Architecture:** Clear separation between raw storage, cleaned tables, and analytical aggregates.
- **Data Governance:** Organized schemas, catalogs, and table definitions using **Databricks Unity Catalog**.

---

## 🏗️ Architecture Diagram

```text
  [ Raw Sales Data (.csv) ]
             |
             v
+--------------------------+
|       BRONZE LAYER       |  <-- Raw Data Ingestion (Delta Format)
|   (default.bronze_sales) |
+--------------------------+
             |
             v
+--------------------------+
|       SILVER LAYER       |  <-- Cleaning, Deduplication, Filtering
| (default.silver_orders,  |      & Schema Enforcement
|  silver_customers, etc.) |
+--------------------------+
             |
             v
+--------------------------+
|        GOLD LAYER        |  <-- Business Aggregations & Analytics
|  (gold_sales_summary,    |      (Ready for Dashboards / BI Tools)
|   gold_product_perf)     |
+--------------------------+

```
## 🛠️ Tech Stack & Tools
Platform: Databricks (Serverless Compute)

Processing Engine: Apache Spark (PySpark)

Storage & Format: Delta Lake

Governance: Databricks Unity Catalog

Language: Python, SQL

Data Source: E-Commerce Dataset on Kaggle
---
## 📊 Medallion Architecture Breakdown
##🥉 1. Bronze Layer (Raw Data Ingestion)
Ingests raw sales .csv files from Kaggle.

Stores raw data in Delta format (default.bronze_sales) without altering original records to preserve auditability.
---
## 🥈 2. Silver Layer (Data Cleaning & Transformation)
Cleans and normalizes customer, product, and order records.

Drops null values in critical fields (CustomerID, StockCode, InvoiceNo).

Removes duplicated rows using PySpark dropDuplicates().

Enforces data integrity rules (e.g., CHECK (Quantity > 0) constraint validation via SQL).
---
## 🥇 3. Gold Layer (Business Aggregations)
Constructs business-focused datasets for reporting and visualization:

Revenue Analysis by Country: Aggregates total sales per region.

Product Performance: Ranks top-selling items and revenue drivers.

Customer Insights: Analyzes purchasing frequency and order values.
---
## 🔍 Data Governance (Unity Catalog)
All layers and tables are organized under Databricks Unity Catalog:

workspace.default.bronze_sales

workspace.default.silver_customers

workspace.default.silver_orders

workspace.default.silver_products

workspace.default.gold_sales_summary

workspace.default.gold_product_performance
---
## 🎯 Key Takeaways & Business Value
Data Integrity: Ensures high-quality data through strict cleaning and validation checks in the Silver layer.

Scalability: Built on Delta Lake and PySpark, allowing the pipeline to scale seamlessly from MBs to TBs of data.

Business Readiness: Provides fast, pre-aggregated Gold tables that enable immediate data-driven decision-making for business analysts.
