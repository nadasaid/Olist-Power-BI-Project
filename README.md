# 📊 Olist E-Commerce Analytics — End-to-End Power BI Dashboard

![Power BI](https://img.shields.io/badge/Power_BI-F2C811?style=for-the-badge&logo=powerbi&logoColor=black)
![DAX](https://img.shields.io/badge/DAX-Data_Analysis_Expressions-blue?style=for-the-badge)
![Power Query](https://img.shields.io/badge/Power_Query-ETL-green?style=for-the-badge)
![License](https://img.shields.io/badge/License-MIT-green?style=for-the-badge)

An interactive, enterprise-grade business intelligence solution analyzing **~100K orders** across the Brazilian marketplace **Olist** (Sep 2016 – Aug 2018). The project tracks the entire commerce journey—from revenue generation and customer retention to logistics bottlenecks and multi-criteria seller performance.

---

## 📌 Executive Summary & Core KPIs

| Metric | Value | Operational Insight |
| :--- | :--- | :--- |
| **Total Revenue** | **$15.84M** | Peak run-rate in late 2017 / early 2018; heavily concentrated in Southeast Brazil. |
| **Total Orders** | **99K** | Driven primarily by single-order buyers across 27 federative units. |
| **Average Order Value (AOV)** | **$159.33** | Strong basket size with key drivers in Computers, Health & Beauty, and Furniture. |
| **Customer Retention Rate** | **3.12%** | High acquisition model (96K unique vs. 3K repeat customers); retention remains an untapped lever. |
| **Average Delivery Time** | **12.52 Days** | Continental logistics footprint across Brazil creates large regional delivery variances. |
| **Late Delivery Rate** | **7.69%** | Average delay when late spikes to **9.95 days**, severely degrading customer sentiment. |
| **Average Review Score** | **4.09 / 5.0** | Drops from **4.2** on on-time orders down to **1.7** when delays cross the 1-week mark. |
| **Active Sellers Tracked** | **3K** | Evaluated on an 89.33% average seller on-time dispatch rate using a composite score. |

---

## 🖥️ Dashboard Architecture & Report Pages

### 1. 🏠 Home Page (Navigation Hub)
* **Design & UX:** Modern navigation interface with icon-based routing across all strategic and operational modules.
* **Coverage Scope:** Sept 2016 through August 2018.

### 2. 📈 Executive Overview
* **Revenue Trajectory:** Monthly revenue trend revealing massive post-2016 growth, stabilization above $1.0M/month in 2018, and seasonality.
* **Geographic Distribution:** State-by-state breakdown showing severe concentration in **São Paulo (SP)** (> $5.8M), followed by **Rio de Janeiro (RJ)** and **Minas Gerais (MG)**.
* **Executive Metrics:** High-level cards tracking Total Revenue ($15.84M), Volume (99K Orders), AOV ($159.33), and MoM % variance.

### 3. 👥 Customer & Product Growth
* **Retention Dynamics:** Donut visualization identifying **96.88% (93K) New Customers** vs. **3.12% (3K) Repeat Customers**, reflecting a high customer acquisition cost (CAC) dependency.
* **Category Contribution:** Revenue ranking led by *Health & Beauty*, *Watches & Gifts*, *Bed, Bath & Table*, *Sports & Leisure*, and *Computers & Accessories*.
* **Top 10 Product Matrix:** Granular SKU-level performance table detailing Units Sold, Total Revenue, and Average Unit Price.

### 4. 🚚 Delivery Performance & Customer Satisfaction
* **Logistical Disparities:** Delivery delay ranking across Brazilian states highlighting severe operational drag in northern and northeastern regions (**AL: 22.76%**, **MA: 16.34%**, **PI: 14.95%** vs. **SP: 5.52%**).
* **Delay Bucketing:** Volume categorization across *On-Time / Early* (~92K), *1–7 Days Late* (~4K), *8–15 Days Late* (~2K), and *>15 Days Late* (~1K).
* **Correlation Analysis:** Direct correlation showing review ratings cratering from **4.2 (On-Time)** down to **1.7 (Late Buckets)**.

### 5. 🏪 Seller Management & Performance Ranking
* **Seller Composite Scoring:** Normalized multi-criteria matrix evaluating merchants across revenue, average rating, and dispatch punctuality.
* **Revenue vs. Rating Dual-Axis:** Identifies high-volume sellers at risk of churn or platform suspension due to slipping quality ratings.

---

## 🧠 Core DAX Measures & Logic

### 1. Retention Rate %
```dax
Customer Retention Rate % = 
VAR TotalCust = DISTINCTCOUNT(fact_orders[customer_unique_id])
VAR RepeatCust = 
    CALCULATE(
        DISTINCTCOUNT(fact_orders[customer_unique_id]),
        FILTER(
            VALUES(fact_orders[customer_unique_id]),
            CALCULATE(COUNTROWS(fact_orders)) > 1
        )
    )
RETURN 
    DIVIDE(RepeatCust, TotalCust, 0)](https://drive.google.com/drive/folders/1EMipeYHlTYeePiVJT8c29KrKfFeHRqVa?usp=sharing)
