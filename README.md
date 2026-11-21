# Fujifilm Instax Sales & Business Performance Analysis (2022–2025)

## Overview
An interactive, multi-page (*5 pages*) analytical *dashboard* designed to examine Fujifilm Instax product sales performance from 2022 to 2025. This project transforms raw transactional data into strategic visual insights to monitor revenue growth, monthly and daily sales trends, product performance rankings by category, sales channel effectiveness (*Online* vs *Offline*), and payment method distribution using **Power BI Desktop** and **Python (Pillow)**.



---

## Business Questions Framework
The following table outlines the primary business and analytical questions answered through the *dashboard* visualizations:

| Analysis Dimension | Key Business Questions |
| :--- | :--- |
| **Sales Performance & Growth** | • How have *Total Revenue*, *Total Orders*, *Products Sold*, and *Average Order Value* (AOV) grown across the 2022–2025 period |
| **Temporal & Seasonal Patterns** | • Which days of the week (*Day of Week*) and months consistently record the highest sales peaks |
| **Product & Category Contribution** | • Which product category (*Camera*, *Film*, *Accessories*) dominates revenue compared to total units sold |
| **Channel & Promo Effectiveness** | • How do *Online* and *Offline* channels compare in transaction contribution, and how significantly do promotions drive orders |
| **Payment Method Preferences** | • How is revenue distributed across all payment methods (*Credit Card*, *Bank Transfer*, *PayLater*, and *E-Wallet*) |

---

## Data Preparation & DAX Modeling (Power BI)
- **Relational Data Modeling (`Fact_Sales` & `Dim_Date`):** Structured a star schema and performed data type standardization in **Power Query** to ensure accurate *cross-filtering* and synced *slicers* (`Year`, `Month`, `Store / Channel`) across all 5 report pages.
- **Dynamic KPI & Growth Calculations (DAX):** Authored dynamic *measures* for core metrics (*Total Revenue*, *Total Orders*, *Products Sold*, and *Average Order Value*) alongside period-over-period variance comparisons (*vs 1st half period*).
- **Chronological Day Sorting (`Day_Num`):** Implemented a sort-key column using `WEEKDAY(Fact_Sales[Tanggal], 2)` paired with *Sort by Column* to enforce chronological *Monday*–*Sunday* ordering without triggering *circular dependencies*.
- **Programmatic UI/UX Design (*Custom Backgrounds*):** Used a **Python (`Pillow`)** script rendered at *high-DPI* (2x *scale* with *LANCZOS resampling*) to generate sharp, lightweight, and uniform *canvas backgrounds*, eliminating the performance overhead of stacked *native shapes* in Power BI.

---

## Visualizations & Dashboard Layout (Power BI)
- **Overview Page (Executive Summary):** Displays 4 dynamic KPI cards with *sparklines*, a monthly trend visual (*Area Chart* — *Sales Trend* 2022–2025), *Top 5 Best-Selling Products* (*Bar Chart*), a *Key Insights* panel, *Sales by Category* (*Donut Chart*), *Channel & Promo Analysis* (*Online vs Offline* & *Promo vs Regular*), and a *Payment Methods* summary.
- **Sales Page (Temporal & Category Trends):** Features two symmetrical *Clustered Column Charts* breaking down *Revenue by Day of Week* (Monday–Sunday) and *Annual Revenue by Category* from 2022 to 2025.
- **Products Page (Full SKU Performance):** A horizontal *Stacked Bar Chart* mapping the *Full Product Revenue Ranking* across all product SKUs, segmented by category (*Camera*, *Film*, *Accessories*).
- **Channels Page (Store & Platform Breakdown):** A vertical *Stacked Column Chart* comparing *Revenue by Store / Platform* (*Website*, *Tokopedia Official*, *Surabaya Branch*, *Shopee Mall*, and *Jakarta Official Store*) with color coding distinguishing *Online* and *Offline* channels.
- **Payments Page (Payment Method Distribution):** A vertical *Column Chart* with integrated data labels showcasing *Total Revenue by Payment Method* across *Credit Card*, *Bank Transfer*, *PayLater*, and *E-Wallet (GoPay/OVO)*.
- **Interactive Sidebar Navigation:** Utilizes custom *Page Navigation* buttons on the left sidebar with hidden bottom report tabs (*Hidden Pages*) to deliver a clean, *app-like UX*.

---

## Key Business Insights
- **Strong Revenue Growth:** Total revenue reached **IDR 6.42B** across **12.3K orders** (AOV: **IDR 520.6K**), recording a **+47.6%** growth surge compared to the first half period.
- **Revenue vs. Volume Dynamics:** The **Camera** category dominated revenue at **56.8%** (led by *Instax Mini Evo*), whereas unit volume was led by consumables: **Instax Square Film (10s)** with **5,291 units** and **Instax Mini Film (20s)** with **5,275 units** sold.
- **Online Channel Dominance & Weekend Peaks:** **Online** channels drove **59.9%** of total orders (led by *Website* and *Tokopedia Official*) with a **29.1%** promo utilization rate, while revenue consistently peaked on weekends (**Friday through Sunday**).
- **Balanced Payment Distribution:** Revenue was evenly distributed across all major payment methods—**Credit Card (IDR 1.64B)**, **Bank Transfer (IDR 1.64B)**, **PayLater (IDR 1.61B)**, and **E-Wallet (IDR 1.53B)**—highlighting broad consumer payment flexibility.

---

## Strategic Recommendations
- **Camera & Film Bundling Strategy:** Capitalize on the high repeat demand for *Instax Square Film* and *Instax Mini Film* by introducing *bundling* packages (Camera + Film + Accessories) to lift *Average Order Value* (AOV), which experienced a slight dip (-2.1%).
- **Weekend Campaign Optimization (*Weekend Flash Sales*):** Concentrate digital ad spend and limited-time promotions on **Friday–Sunday** across *Website*, *Tokopedia Official*, and *Shopee Mall* to maximize conversion during peak shopping traffic.
- **Omnichannel Experience at Physical Stores:** Strengthen *in-store experience* and *pickup-in-store* programs at *Surabaya Branch* and *Jakarta Official Store* to boost *Offline* channel competitiveness alongside *Online* growth.

---

## Tools Used
- **Power BI Desktop:** Primary platform for relational *Data Modeling*, *Power Query* transformations, **DAX** formula authoring, interactive visualization design, and multi-page navigation setup.
- **Google Colab (Python / Pillow):** Cloud-based environment used to programmatically design and export *high-DPI custom canvas backgrounds*, card grids, and vector icons.
- **Dataset:** Fujifilm Instax sales transaction dataset covering 2022–2025 (`Fact_Sales` & `Dim_Date`).
