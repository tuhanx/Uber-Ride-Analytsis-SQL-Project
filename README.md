# 🚖 Uber Ride Analytics - SQL Project

![SQL](https://img.shields.io/badge/Language-SQL-orange) ![ETL](https://img.shields.io/badge/Process-ETL-blue) ![Data Cleaning](https://img.shields.io/badge/Focus-Data%20Cleaning-green)

## 📌 Project Overview
This project focuses on analyzing **Uber's operational data** to uncover insights related to ride volume, revenue streams, and cancellation patterns. By utilizing advanced SQL techniques, raw dirty data was transformed into actionable business intelligence.

The primary goal is to demonstrate the **End-to-End Data Analysis** process: from raw data to structured insights.

---

## 🛠️ The Process

### 1. Data Cleaning & Schema Design
The raw dataset contained unformatted columns (`c1`, `c2`...) and mixed data types.
* **Schema Mapping:** Renamed cryptic columns to meaningful names (e.g., `c16` → `incomplete_reason`).
* **Data Type Conversion:** Converted `string` values to `DECIMAL` for calculations and `DATE/TIME` for analysis.
* **Handling Nulls:** Cleaned `NaN` values in financial columns using `NULLIF`.

### 2. Feature Engineering
New variables were created to enable deeper analysis:
* `time_of_day`: Segmented rides into Morning, Afternoon, Evening, and Night.
* `day_name`: Extracted day names (Mon, Tue...) to analyze weekly trends.
* `month_name`: Extracted month names for seasonal analysis.

---

## 🔍 Key Business Questions Answered

### 📊 Generic & Operational Analysis
1.  **Cancellation Rate:** What is the ratio of completed vs. cancelled rides?
2.  **Root Cause:** What are the primary reasons for incomplete rides (Driver vs. Customer)?
3.  **Peak Days:** Which day of the week sees the highest demand?

### 💰 Revenue & Product Analysis
1.  **Top Earners:** Which vehicle type (e.g., UberXL, Premier) generates the highest revenue?
2.  **Efficiency:** What is the average price-per-km for each vehicle category?
3.  **Lost Revenue:** How much revenue is potentially lost due to high cancellation rates?

### ⏳ Time-Based Analysis
1.  **Peak Hours:** At what time of day do customers book the most rides?
2.  **Pricing Dynamics:** Does the average fare increase during night hours (Surge Pricing)?

---

## Analysis based on Domain Expertise & Operational Experience

During the exploratory analysis, distinct patterns indicated that this dataset is synthetic. Comparing the data trends against real-world logistics experience (e.g., Chicago ride-share dynamics), the following discrepancies were identified:

1. The "Human Factor" in Cancellations

Real-World Reality: Cancellations are driven by complex variables. Based on field experience, drivers often cancel due to safety concerns (e.g., dangerous neighborhoods, masked individuals), customer condition (intoxicated/hygiene issues), or unprofitable pickups (long pickup distance for a short trip).

Dataset Pattern: The data shows a uniform cancellation distribution across reasons (~33% split), failing to capture these behavioral and environmental triggers.

2. Economic Discrepancies (Vehicle Types)

Real-World Reality: The operating costs (fuel, maintenance) of an UberXL are significantly higher than an eBike. Therefore, the pricing model must reflect this difference.

Dataset Pattern: The analysis revealed near-identical Average Fare and Price per KM metrics across all vehicle types (e.g., eBike vs. Premier), which contradicts basic logistics economics.

## 📂 Repository Structure

```text
├── ride_bookings_raw.csv       -- The original dataset (dirty data with c1, c2 headers)
├── 1_schema_setup.sql          -- Database creation & table definition
├── 2_etl_data_cleaning.sql     -- ETL process: Cleaning raw data & Feature Engineering
└── 3_business_analysis.sql     -- SQL queries for KPIs and Business Insights
