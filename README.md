# Case Study #2 - 🍕 Pizza Runner Operational Analytics

## 📌 Project Overview
Danny was scrolling through his Instagram feed when he caught a brilliant idea: "80s Retro Styling and Pizza Is The Future!" So, he recruited runners to deliver fresh pizzas from his apartment, building a database capturing operations, customer transactions, and courier metrics. 

However, the operational data was captured with substantial inconsistencies, raw text formatting issues, and structural noise. This project showcases the end-to-end **Data Cleaning (ETL), Database Schema Optimization, and Operational Analysis** required to turn raw transactional logs into high-value business metrics using **Microsoft SQL Server**.

---

## 🛠️ Tech Stack & Advanced SQL Pillars
* **Database Engine:** Microsoft SQL Server (SSMS)
* **Data Transformation & Cleaning:** `CASE WHEN`, `TRIM`, `REPLACE`, Type Casting (`CAST`/`CONVERT`)
* **Advanced Query Structures:** Common Table Expressions (CTEs), Subqueries, Window Functions (`DENSE_RANK()`, `PARTITION BY`)
* **Core Analytics Functions:** `DATEDIFF`, `DATEPART`, `DATENAME`, `STRING_AGG`, `STRING_SPLIT`, `CROSS APPLY`
* **Database Management:** Schema DML/DDL generation, relational table design, Data Manipulation Language (DML) challenges

---

# 🧹 Enterprise Data Cleaning Stage (The ETL Pipeline)
Real-world data is inherently messy. Before running corporate analytics, I isolated the staging architecture and built data cleaning filters to transform the core operational tables:

### 1. `customer_orders` Stabilization
* **Issue:** The `exclusions` and `extras` columns contained irregular combinations of blank spaces `''`, structural text `'null'` placeholders, and system `'NaN'` strings.
* **Resolution:** Implemented conditional logic filters to cleanly map irregular strings into structured `NULL` values across the schema.

### 2. `runner_orders` Normalization
* **Issue:** Core logistical tracking columns contained a mix of mixed-text metadata. Distances were recorded as both `20km` and `23.4 km`; durations included text elements like `32minutes`, `20mins`, or `15 minute`. 
* **Resolution:** Built text-parsing filters leveraging `REPLACE` and `TRIM` strings, then safely cast the objects to structured types (`DECIMAL` and `INT`) to ensure mathematical operations could be calculated properly.

---

## 📊 Business Performance Metrics Solved

### 📋 Section A: Pizza Volume Metrics
* Evaluated global order traffic counts, distinct checkout cohorts, and peak demand hours.
* Modeled order volume distribution using date aggregation logic (`DATEPART`, `DATENAME`) to isolate day-of-week and hourly operational shifts.

### 🚴 Section B: Logistics & Courier Optimization
* Calculated preparation velocity and transit lag milestones by evaluating duration variance (`DATEDIFF`) between customer order creation and courier pickups.
* Isolated statistical correlations proving that larger order volumes exponentially scale corporate kitchen prep bottlenecks.
* Analyzed courier metrics by tracking average velocities ($KM/H$) per transit routing and processing individual operational success percentages.

### 🍕 Section C: Ingredient Optimization
* Flattened nested relational items via cross-applied arrays (`STRING_SPLIT` combined with `CROSS APPLY`) to map individual ingredient configurations out of multi-variable arrays.
* Aggregated global preference matrices to determine the most common client extras and production modifications.

### 💰 Section D: Pricing & Financial Accountability
* Designed multi-variable cost allocation functions tracking gross revenue margins based on product groupings ($12 for Meatlovers, $10 for Vegetarian).
* Dynamic pricing models calculating upsell premiums for custom ingredient add-ons ($1 extra per added topping).
* Generated dynamic data warehouse mock architecture, initializing `pizza_runner.runner_ratings` schema tables to track customer feedback fields.

### 🏆 Section E: Unified Analytical Reporting
* Formulated a centralized denormalized reporting master query combining client records, order timestamps, courier IDs, transit runtimes, and user feedback evaluations into a flat analytical framework for business stakeholders.

---
*Developed as a portfolio component highlighting core competency in business systems modeling, relational mapping, and intermediate-to-advanced SQL querying workflows.*
