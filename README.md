# End-to-End Data Engineering & Business Intelligence Solution  

This repository showcases a complete data solution for **Adventure Works Cycles**, combining **Data Engineering** (ETL pipelines and Data Warehouse design) and **Business Intelligence** (interactive Power BI dashboards).  

---

## 🚀 Project Overview  
- **Objective**: Deliver a robust analytics platform to enable fast, reliable decision-making.  
- **Scope**:  
  - Design and implement a **star-schema Data Warehouse** optimized with **columnstore indexes**.  
  - Automate **initial and incremental data loads** using **SSIS pipelines** with a staging layer for quality control.  
  - Apply **Slowly Changing Dimensions (SCD)** to track historical changes.  
  - Develop **Power BI dashboards** with KPIs, filters, maps, and customer/product insights.  

---

## 🏗 Data Engineering (ETL & Data Warehouse)  
### Key Features  
- **Source System**: OLTP database (AdventureWorks)  
- **ETL Tool**: SQL Server Integration Services (SSIS)  
- **Architecture**:  
  - **Staging layer** to buffer and validate incoming data  
  - **Star-schema DW** using **columnstore indexes** for high performance  
  - **Dynamic pipelines** handling:  
    - **Initial Load** (full data reset)  
    - **Incremental Load** (delta data using watermark variables)  
- **Data Handling**:  
  - **Orders** → Append-only  
  - **Customer data** → Overwrite (no historical tracking)  
  - **Product cost/price** → Historical tracking using SCD logic  

### Deliverables  
- SSIS project (`AdventureWorks_OLAP`) with one unified package  
- Data Warehouse backup file  
- Implementation presentation showing pipelines, transformations, and performance validation  

---

## 📊 Business Intelligence (Analytics & Reporting)  
### Key Features  
- **Tool**: Microsoft Power BI  
- **Data Model**: Based on the star-schema DW built in the ETL phase  
- **Dashboard Highlights**:  
  - **KPIs**: Orders, products, customers, active customer ratio, avg. shipping time  
  - **Filters & Slicers**: Date and location filters with map visuals  
  - **Customer Insights**: Active customers by location, shipping patterns  
  - **Product Insights**: Quantities by category, top-performing models  
- **Outcome**: Clear, structured reporting to support business decisions  

### Deliverables  
- Power BI `.pbix` report file with interactive pages  
- Updated project presentation including visuals and workflows  

---

## 🛠 Tools & Technologies  
- **Database**: Microsoft SQL Server  
- **ETL**: SSIS (SQL Server Integration Services)  
- **Modeling**: Star Schema, Columnstore Indexing  
- **Reporting**: Microsoft Power BI  
- **Languages**: SQL, DAX, M  


