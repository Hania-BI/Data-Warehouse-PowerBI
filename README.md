# 🏬 Retail Data Warehouse & Power BI Dashboards

An end-to-end **Business Intelligence** project: a SQL Server data warehouse built on the **Medallion Architecture** (Bronze → Silver → Gold), modeled as a **star schema**, and visualized in **three interactive Power BI dashboards** for different business users.

![SQL Server](https://img.shields.io/badge/SQL%20Server-CC2927?style=flat&logo=microsoftsqlserver&logoColor=white)
![T-SQL](https://img.shields.io/badge/T--SQL-0078D4?style=flat)
![Power BI](https://img.shields.io/badge/Power%20BI-F2C811?style=flat&logo=powerbi&logoColor=black)
![ETL](https://img.shields.io/badge/ETL-Pipeline-2E8B57?style=flat)

---

## 🧠 Skills Demonstrated

- **Data Warehousing:** Medallion architecture, star schema design, fact and dimension tables, surrogate keys
- **ETL Development:** Automated stored procedures, `BULK INSERT` loading from CSV, full-refresh (truncate & insert) strategy
- **Data Cleaning (T-SQL):** Handling NULLs, trimming whitespace, removing duplicates, standardizing text, derived columns
- **Data Quality & Reliability:** `TRY…CATCH` error handling, load logging tables, row-count validation, referential integrity with foreign keys
- **BI & Visualization:** Power BI dashboards, KPI cards, map visuals, time-intelligence slicers (MTD, Rolling 3M, YTD)
- **Business Analysis:** Defining user personas and mapping every visual to a business question

---

## 🏗️ Architecture

| Layer | Purpose | What was done |
|---|---|---|
| 🥉 **Bronze** | Raw data | Loaded multi-source retail CSVs (customers, products, POS transactions, inventory, stores, employees, suppliers…) with `bronze.load_bronze`, logging and error handling |
| 🥈 **Silver** | Clean data | Cleaned and standardized data with `silver.load_silver`: NULL handling, `TRIM`, `DISTINCT`, lowercase emails, uppercase promo types, derived date columns, `dwh_create_date` audit column |
| 🥇 **Gold** | Analytics | Built a star schema with `gold.load_gold`: 6 dimensions, 2 fact tables, surrogate keys via `ROW_NUMBER()`, default "unknown" records, FK constraints |

### ⭐ Star Schema (Gold Layer)

**Dimensions:** `dim_date`, `dim_product`, `dim_store`, `dim_customer`, `dim_employee`, `dim_promotion`
**Facts:** `fact_store_sales` (line-item sales with a persisted `total_sales_amount` column) and `fact_inventory` (stock snapshots)

<p align="center">
  <img src="images/schema_fact_store_sales.png" width="48%" alt="Sales star schema"/>
  <img src="images/schema_fact_inventory.png" width="48%" alt="Inventory star schema"/>
</p>

---

## 📊 Power BI Dashboards

### 1. Store Sales vs Inventory Performance
*For store managers and executives:* monthly KPIs, an inventory-coverage gauge (153 vs 305-day target), average daily sales by city on a map, and top customers by loyalty tier.

![Store Sales vs Inventory Performance](images/dashboard_store_sales_inventory.png)

### 2. Sales Performance
*For sales analysts and executives:* **$2.88M total sales**, 15K orders, top 5 stores, monthly sales vs orders trend, sales by department, and time-intelligence slicers.

![Sales Performance Dashboard](images/dashboard_sales_performance.png)

### 3. Inventory Performance & Stock Optimization
*For supply chain planners:* 600 products, 600K units in stock, monthly inventory trend, inventory by department, and a store-by-department breakdown for the top 5 stores.

![Inventory Performance Dashboard](images/dashboard_inventory_optimization.png)

---


## 👥 Team

University group project (Faculty of Informatics and Computer Science) by Nadine Mohsen, Hania Mohsen, Maryam Nasser, Nada Ehab and Malak Madyan.
