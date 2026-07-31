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
