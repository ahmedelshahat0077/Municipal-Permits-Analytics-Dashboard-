# 📑 End-to-End Permit & SLA Performance Analytics

![Permit Analytics Demo](./assets/permit-demo.gif)
> 💡 *Interactive Power BI Dashboard backed by an SQL Server database pipeline, highlighting SLA performance, bottlenecks, and channel distribution.*

---

## 📌 Executive Summary
This project presents an end-to-end data pipeline designed to analyze permit application workflows and SLA compliance. The process covers database architecture setup, CSV data ingestion, quality validation in SQL Server, dynamic data modeling, and interactive visualization in Power BI. 

The goal is to translate raw transactional data into actionable operational strategies—identifying delay root causes and optimizing resource distribution.

---

## 🛠️ End-to-End Technical Architecture

### 1. Database Creation & Data Ingestion (SQL Server)
* **Server Setup:** Configured a dedicated database instance on SQL Server to process high-volume operational records.
* **ETL & Data Loading:** Bulk-loaded raw CSV files into staging tables, enforcing strict data types for dates, IDs, and numeric metrics.
* **Data Quality Checks & Validation:** Executed SQL validation scripts to audit:
  * Null/Missing values in critical fields (`Application_number`, `Target_SLA_Days`).
  * Date integrity checks (ensuring `Processing_Days` >= 0 and submission dates precede completion dates).
  * Duplicate identification across permit applications.

### 2. Power BI Import & Data Modeling
* **SQL Integration:** Imported clean relational Tables directly from SQL Server into Power BI.
* **Data Modeling:** Built a clean **Star Schema** connecting core Facts (Permit Transactions) with Dimensions (date, Services, Region).
* **DAX Formulas:** Developed custom measures for business metrics like:
  * `SLA Compliance Rate %`
  * `Overdue Rate %`

---

## 🔍 Key Findings & Root Cause Analysis

* **Finding 1: High Overdue Rate (20.5%):** Out of 2,500 applications, 512 applications breached target SLAs.
* **Finding 2: Service Bottlenecks:** Technical categories like *Infrastructure Compliance & Inspection* showed actual processing times significantly exceeding target SLA days.
* **Finding 3: Seasonal Spikes:** Application submissions peak sharply in **Q3** (~640 applications), causing seasonal backlog accumulation.
* **Finding 4: Channel Disparity:** While the **Online Portal** handles over 80% of application volume, physical **Service Centers** experience higher relative delay rates per application processed.

---

## 💡 Recommended Business Solutions & Action Plan

| Problem Identified | Root Cause | Proposed Solution / Action |
| :--- | :--- | :--- |
| **SLA Breaches in Infrastructure** | Complex technical review steps & manual inspection processes. | **Fast-Track Routing:** Implement automated preliminary approvals for low-risk infrastructure permits. |
| **Q3 Application Backlog** | Fixed staffing levels during high-demand seasonal peaks. | **Dynamic Capacity Allocation:** Reallocate staff from low-volume quarters (Q1/Q2) to assist technical review teams during Q3. |
| **Service Center Delays** | High manual data entry load and paper-based processing steps. | **Digital Migration Strategy:** Incentivize users toward the Online Portal and Mobile App via automated status updates. |

---

## ⚙️ Dashboard Structure

* **Executive Overview:** High-level executive KPIs (Total Applications, SLA Compliance %, Overdue Rate, Geographic Map, Quarterly Trends).
* **Operational Overview:** Granular breakdown by application channel, target vs. actual processing days per service, and status tracking (Completed, Under Review, Rejected).

---

## 📂 Project Structure
```text
├── sql/
│   ├── 01_schema_setup.sql          # Database creation scripts
│   ├── 02_data_ingestion.sql        # Bulk load & staging
│   └── 03_data_quality_checks.sql   # Data validation scripts
├── data/
│   └── raw_permits.csv              # Source CSV datasets
├── assets/
│   └── permit-demo.gif              # Walkthrough video clip
├── Permit_Analytics_Dashboard.pbix  # Main Power BI dashboard
└── README.md                        # Project documentation
