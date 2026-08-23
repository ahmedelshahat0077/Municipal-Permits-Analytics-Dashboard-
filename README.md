
# 🏛️ Municipal Permit Analytics | End-to-End BI Project

An end-to-end Data Analytics project designed to optimize municipal operations, evaluate digital transformation efficiency, and monitor Service Level Agreement (SLA) compliance. This project covers relational database schema implementation in **Microsoft SQL Server**, complex ETL/DAX calculations, and an interactive executive dashboard in **Power BI**.


<img width="1132" height="636" alt="20-39-37" src="https://github.com/user-attachments/assets/76f062c1-8cc1-42c7-9b21-0a189be67441" />



## 🛠️ Tech Stack & Workflow

* **Database & Data Modeling:** Microsoft SQL Server (Relational Schema, Star Schema, Aggregations)
* **Business Intelligence & Visualization:** Power BI Desktop
* **Data Transformation:** Power Query (M Code)
* **Analytics & Calculations:** Advanced DAX (Measures, CALCULATE, Dynamic Ranks)

---

## 🗄️ Database Architecture & SQL Engineering

Before visualizing the metrics, the raw operational data was structured and loaded into **SQL Server** to build a robust **Star Schema** optimized for high-performance BI reporting.

### SQL Implementation Steps:
1. **Schema Design & Data Ingestion:** Formatted raw transaction logs into structured Fact (`fact_permits`) and Dimension tables (`dim_service`, `dim_channel`, `dim_region`).
2. **Data Integrity & Transformations:**
   * Calculated operational durations: `Processing_Days = DATEDIFF(day, Application_Date, Completion_Date)`.
   * Enforced SLA flags: Derived `Overdue_Status` by comparing actual processing time against SLA targets (`Target_SLA_Days`).

---

## 📊 Business Story & Analytics Findings

### 1. Overall Workload & SLA Performance
* **Total Volume:** Processed **2,500 applications** with an **81.8% completion rate** and a low **7.2% rejection rate**.
* **SLA Breaches:** **80% SLA compliance rate**, leaving **20% (512 cases)** overdue.
* **Geographic Focus:** Demand is heavily concentrated in **Los Angeles**, followed by **San Diego** and **San Jose**.

### 2. Digital vs. Traditional Channel Efficiency
* **Digital Superiority (`Online Portal` & `Mobile App`):** Achieved near-zero rejection rates and rapid turnaround times. Embedded form validations prevent incomplete user submissions.
* **Service Counter Bottlenecks (`Service Center` & `Kiosk`):** Account for almost all pending cases (`Under Review`) and registered **95 rejected applications** due to manual entry errors and missing physical paperwork.

### 3. Critical SLA Bottlenecks
* **Infrastructure Compliance Inspection:** Severe delay averaging **12 processing days** against a target of **7 days** (+5 days breach).
* **Commercial Lease Registration:** Averages **5 processing days** against a target of **2 days** (+3 days breach).
* **Public Road Occupancy Permit:** Averages **4.5 processing days** against a target of **3 days** (+1.5 days breach).
* *Positive SLA Highlight:* `Zoning Variance Request` and `Residential Building Permit` process well within SLA targets.

### 4. Departmental Demand Imbalance
* **High-Volume Divisions:** `Real Estate & Land Use` and `Building & Safety` handle **over 1,800 applications** (>70% of total municipal volume).
* **Low-Volume Division:** `Urban Planning` processes under **200 applications** (<8% of total volume) due to the complex, long-term nature of urban requests.

---

## 💡 Strategic Recommendations

* **Automate Inspection Workflows:** Streamline field inspection procedures for **Infrastructure Compliance Inspection** to bring turnaround time down from 12 to 7 days.
* **Mandate Digital Channel Shift:** Force high-volume requests (such as `Commercial Leases`) to the **Online Portal** to leverage pre-validation rules and reduce counter foot traffic.
* **Reallocate Staff:** Shift administrative personnel from low-volume divisions (`Urban Planning`) to high-demand departments (`Real Estate` & `Building & Safety`) to clear backlogs.
* **Standardize Front-Desk Intakes:** Implement mandatory checklists at physical `Service Centers` to eliminate the 95 counter-level rejections.

---

## 🎨 Dashboard Design

* **Executive vs. Operational Views:** Structured two-page navigational reporting (Executive Summary & Operational Overview).

