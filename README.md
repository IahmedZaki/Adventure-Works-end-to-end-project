# End-to-End Data Engineering & Business Intelligence Solution  

This repository showcases a complete data solution for **Adventure Works Cycles**, combining **Data Engineering** (ETL pipelines and Data Warehouse design) and **Business Intelligence** (interactive Power BI dashboards).  

---

## 📌 Project Summary

- **Goal** → Build a reliable data platform from OLTP source to BI reporting.  
- **Approach** →  
  - Designed a **star-schema data warehouse** with columnstore indexing for high performance.  
  - Automated **ETL workflows** using SSIS with both **initial** and **incremental** loads.  
  - Applied **Slowly Changing Dimensions (SCD)** to preserve historical product data.  
  - Developed **Power BI dashboards** with KPIs, filters, maps, and deep customer/product insights.  

---

## 🏗 Data Engineering

### Architecture & Process
- **Source** → AdventureWorks OLTP database  
- **Staging Layer** → Ensures data quality and reduces source load  
- **Data Warehouse** → Star schema with optimized columnstore indexes  
- **ETL Automation** → SSIS package with dynamic variables and control flow  
  - **Initial Load** → Full reset and population  
  - **Incremental Load** → Delta extraction using watermark timestamps  
- **Data Logic** →  
  - Orders → Append-only  
  - Customers → Overwrite (no history)  
  - Products → Track price/cost changes using SCD  

## 📊 Business Intelligence

### Dashboard Highlights
- **Tool** → Microsoft Power BI  
- **Data Model** → Built on the DW created in the ETL phase  
- **Features** →  
  - Core KPIs (orders, products, customers, active customer ratio, shipping time)  
  - Date & location filters with interactive map visuals  
  - Customer insights (active customers by region, shipping patterns)  
  - Product insights (quantities by category, top models)  
- **Outcome** → Data is presented in a structured, visual format for faster decisions  


## 🛠 Tech Stack

- **Database** → Microsoft SQL Server  
- **ETL** → SQL Server Integration Services (SSIS)  
- **Data Modeling** → Star Schema, Columnstore Indexes, SCD  
- **Analytics & Reporting** → Microsoft Power BI  
- **Languages** → SQL, DAX, M  
---
### 🔹 SSIS Setup  

- Open the SSIS project in **Visual Studio (SQL Server Data Tools)**.  
- Update the **connection manager** with your SQL Server instance.  
- Configure project parameters:  
  - `InitialLoad = True` → for the first bulk load.  
  - `InitialLoad = False` → for incremental loads.  
- Deploy the package to **SSIS Catalog** or run locally.  

---

### 🔹 Initial Load  
- Open ssms restore only v1 of db
- Set project parameter `InitialLoad = True`.  
- The pipeline will:  
  - **Truncate** all DW tables.  
  - **Bulk load** dimensions and facts from the source OLTP.  
  - **Rebuild constraints and indexes** after loading.  
- After completion, reset `InitialLoad = False` to switch to incremental mode.  

---

### 🔹 Incremental Load  
- Open ssms Delete the v1 of database and restore the full db v1+v1
- Ensure a `Watermark` table exists in the **DW**.  
- Each run fetches only new/updated data since the last `LastJobTime`.  
- After the run, the `LastJobTime` is updated automatically.  

