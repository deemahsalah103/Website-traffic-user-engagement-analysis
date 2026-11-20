# 📊 Website Traffic & User Engagement Analysis

Business Intelligence project analyzing website traffic, user engagement and marketing campaign performance — data cleaning and analysis in **SQL Server**, with interactive dashboards built in **Power BI**.

> **Course:** Data Warehouse (DS339) — Al-Balqa Applied University, Faculty of Artificial Intelligence  
> **Instructor:** Dr. Jaffar M. Atwan

---

## 🎯 Business Questions
- How many website sessions are recorded each day?
- Which traffic source generates the highest number of visitors?
- Which webpage receives the most page views?
- What is the average number of page views per session?
- Which marketing campaign generates the highest number of visits?
- How many visits come from mobile devices compared to desktop devices?

---

## 📈 Key Performance Indicators (KPIs)

| KPI | Description |
|---|---|
| Total Visitors | Number of unique visitors |
| Total Sessions | Number of website visits |
| Total Page Views | Number of pages viewed across all sessions |
| Average Page Views per Session | Total page views ÷ total sessions |
| Top Traffic Source | Source with the highest number of sessions |
| Top Performing Campaign | Campaign with the highest number of sessions |
| Mobile vs Desktop Traffic | Share of sessions by device type |
| Returning Visitors Rate | % of visitors with more than one session |

### Problems, Goals and KPIs

| Current Problem | Business Goal | Primary KPI |
|---|---|---|
| Website traffic source performance is unclear | Identify the most effective traffic sources | Sessions by Traffic Source |
| User engagement with website pages is unknown | Improve user engagement | Average Pageviews per Session |
| High number of visits but low page interaction | Increase engagement with website content | Pages Viewed per Session |
| Marketing campaign effectiveness is difficult to evaluate | Measure campaign performance | Sessions by Campaign |
| Most visited pages are not identified | Optimize website content and navigation | Top Pages by Pageviews |
| Device usage patterns are unclear | Improve user experience across devices | Sessions by Device Type |
| Visitor retention and return visits are unknown | Increase visitor loyalty | Returning Visitors Rate |

---

## 🗂️ Dataset
- **Source:** [Web Analytics Dataset – Sessions, Pageviews and Sources](https://databasesample.com/datasets/web-analytics-dataset-sessions-pageviews-and-sources)
- **Period:** March – May 2025 (synthetic data)
- **Size:** 6 tables, 1,132 rows

---

## ⭐ Data Model — Star Schema

### 🟦 Fact Tables

#### `sessions` — Main Fact Table (Fact_Sessions)
One row per visit. Links visitors, traffic sources, campaigns and dates.

<img width="681" height="569" alt="image" src="https://github.com/user-attachments/assets/c46b88f2-69ce-42ed-8701-f319603f31d0" />

#### `pageviews` — Fact Table (page level)
One row per page viewed inside a session. Contains the measure `seconds_on_page`.

<img width="644" height="571" alt="image" src="https://github.com/user-attachments/assets/24c5c9cc-0956-4f41-896b-c7b8cd7ca81a" />


### 🟩 Dimension Tables

#### `visitors` — Dim_Visitor
Visitor device, browser and country.

<img width="625" height="574" alt="image" src="https://github.com/user-attachments/assets/8db2e9f5-427d-43a4-9a47-79e7722ab5ba" />


#### `traffic_sources` — Dim_TrafficSource
How a visit arrives (organic, paid, social, email…).

<img width="512" height="375" alt="image" src="https://github.com/user-attachments/assets/aaf9ffb3-40af-49c7-a67a-fea1bbdb6b49" />


#### `campaigns` — Dim_Campaign
Marketing campaigns with objective and daily budget.

<img width="600" height="213" alt="image" src="https://github.com/user-attachments/assets/611d4d20-c8b7-477c-8a46-e281b7c82667" />


#### `pages` — Dim_Page
Website pages and their types.

<img width="369" height="232" alt="image" src="https://github.com/user-attachments/assets/a2d732f4-bb5b-48e6-9fc6-e3e9ac6cd4a3" />

#### `Dim_Date`
Created in Power BI for time analysis (Date, Month, Quarter, Year).

### 🔗 Relationships
```
Dim_Visitor        1 ── N  sessions
Dim_TrafficSource  1 ── N  sessions
Dim_Campaign       1 ── N  sessions   (optional — campaign_id can be NULL)
Dim_Date           1 ── N  sessions
sessions           1 ── N  pageviews
Dim_Page           1 ── N  pageviews
```

---

## 🔄 BI Architecture Flow
```
CSV Files → SQL Server → Power Query → Data Model → DAX Measures → Power BI Dashboard → Business Insights
```

### Data Cleaning & Transformation
- Checked for missing values and duplicate records
- Standardized data types for IDs, dates and numeric measures
- Verified relationships between tables
- Renamed columns for readability
- Created a Date dimension for time-based analysis

---

## 🧾 SQL Queries
All queries are in [`website_analysis_queries.sql`](website_analysis_queries.sql).

| # | Query | Business Question |
|---|---|---|
| 0 | Duplicate IDs | Is the data clean? |
| 1 | Sessions by traffic source | Which channel brings the most visits? |
| 2 | Monthly traffic trend | Is traffic growing? |
| 3 | Sessions by day of week | What are the busiest days? |
| 4 | Sessions by device | Mobile or desktop? |
| 5 | Top countries | Where do visitors come from? |
| 6 | Most viewed pages | Which pages are most popular? |
| 7 | Conversion rate by source | Which channel brings sign-ups? |
| 8 | Conversion rate by device | Does sign-up work on every device? |
| 9 | Campaign performance | Which campaign is worth the budget? |
| 10 | Bounce rate by landing page | Where do visitors leave immediately? |

---

## 🛠️ Tools
| Tool | Purpose |
|---|---|
| Microsoft SQL Server / SSMS | Data storage, cleaning and SQL analysis |
| Power Query | Data transformation (ETL) |
| DAX | KPI measures |
| Microsoft Power BI | Dashboard and visualization |
| Excel | Data review |

---

## 👥 Team
- **Deemah Salah Al-Daqs** — Team Leader
- Aisha Talal Khraisat
- Alaa Mohammad Ismail
- Noor Nabil Al-Natsheh
- Yumna Mohammad Al-Kalloub

