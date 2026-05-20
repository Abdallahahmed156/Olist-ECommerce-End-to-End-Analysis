# 🛒 Olist E-Commerce — End-to-End Analysis

> A full data analysis pipeline on the Brazilian E-Commerce Public Dataset by Olist — from raw data to business insights, using Python and Power BI.

---

## 📌 Project Overview

This project transforms raw transactional data from 9 relational tables into actionable business insights across two tools, each handling a different layer of the analysis pipeline.

| Layer | Tool | Role |
|---|---|---|
| Data Cleaning & EDA | Python (Kaggle) | Merging, cleaning, feature engineering, RFM segmentation |
| Data Modeling & BI | Power BI | Star schema, DAX measures, interactive dashboards |

---

## 🔄 Workflow

```
Raw Data (9 CSV files)
        ↓
  Python — Cleaning, EDA & RFM
        ↓
  9 Clean CSVs exported
        ↓
  Power BI — Star Schema + DAX + 5-Page Dashboard
```

---

## 🐍 Python — What Was Done

### 1. Data Integration
- Merged 6 datasets using **Left Joins** to preserve all orders, including those with missing details
- Used `customer_unique_id` instead of `customer_id` to correctly identify returning customers

### 2. Data Cleaning
- Converted all date columns from `object` to `datetime`
- Distinguished between **data errors** (dropped) and **logical gaps** (filled with business logic)
- Filled missing product dimensions with median values
- Flagged **Business Anomalies**: orders where freight cost exceeds product price

### 3. Outlier Detection
- Applied **IQR method** to detect extreme price values
- Investigated high-freight anomalies as potential logistics or data entry issues

### 4. Feature Engineering
- `delivery_time_days` — actual delivery duration
- `delivery_diff_days` — deviation from estimated delivery date (negative = early)
- `purchase_hour`, `purchase_day_name`, `purchase_month` — shopping behavior features

### 5. EDA — Key Insights
- **Peak shopping hours:** 10 AM – 4 PM, with absolute peak at 4 PM
- **Top revenue categories:** Health & Beauty, Watches & Gifts (R$1.2M+ each)
- **Geographic dominance:** São Paulo (SP) accounts for ~40% of all orders
- **Logistics efficiency:** Majority of orders delivered before estimated deadline

### 6. RFM Customer Segmentation

Segmented customers into 6 behavioral groups using Recency, Frequency, and Monetary scores:

| Segment | Count | Strategy |
|---|---|---|
| Lost | 23,748 | Low win-back investment |
| At Risk | 17,929 | Re-engagement campaign |
| Loyal Customer | 17,906 | Retention rewards |
| Potential Loyalist | 17,841 | Convert with personalization |
| Recent Customer | 11,920 | Nurture early relationship |
| Champion | 6,075 | Loyalty programs & exclusives |

### 7. Monthly Revenue Trend
- Revenue grew ~10x from Jan 2017 to Jan 2018
- Peak in **November 2017** — driven by Black Friday
- Plateau phase at ~R$900K–R$1M (Mar–Aug 2018)
- Drop in final months is a **data artifact** — incomplete records near dataset cutoff

---

## 📊 Power BI — Dashboard

A 5-page interactive dashboard built on a **Star Schema** data model with custom DAX measures.

### Data Model
- **Fact tables:** `orders`, `order_items`, `payments`
- **Dimension tables:** `customers`, `products`, `reviews`, `rfm_segments`
- **Relationships:** One-to-Many with bidirectional cross-filtering where needed

### DAX Measures
- `Total Revenue` — sum of price + freight across all order items
- `Total Orders` — distinct count of order IDs
- `AOV` — average order value
- `Delivery Rate %` — % of orders with status "delivered"
- `Late Deliveries %` — % of orders delivered after estimated date
- `Avg Delivery Time` — average days from purchase to delivery
- `Rolling Avg 3M` — 3-month rolling average revenue
- `Avg Review Score` — average review score across all orders
- RFM segment counts: `Champions`, `Loyal Customers`, `At Risk`, `Lost`

### Dashboard Pages

#### 🏠 Home
Landing page with navigation cards to all 4 analysis pages.

#### 📈 Sales
- **KPIs:** Total Revenue · Total Orders · AOV · Total Customers
- **Visuals:** Monthly Revenue Trend · Top Categories by Revenue · Orders by Day · Orders by Hour · Payment Methods
- **Slicers:** Date Range · Category · State · Payment Type

#### 🚚 Shipping
- **KPIs:** Delivery Rate · Late Deliveries % · Avg Delivery Time · Avg Freight Value
- **Visuals:** Orders by State (Map) · Delivery Time Distribution · On-time vs Late by State · Delivery Rate Gauge
- **Slicers:** Date Range · State · Order Status · Delivery Type

#### ⭐ Customer Experience
- **KPIs:** Avg Review Score · 5-Star % · 1-Star % · Total Reviews
- **Visuals:** Review Score Distribution · Avg Score by Category · Avg Delivery Time by Review Score · Review Score Gauge
- **Slicers:** Date Range · Review Score · Category

#### 🎯 RFM Segmentation
- **KPIs:** Champions · Loyal Customers · At Risk · Lost
- **Visuals:** Customers per Segment · Segment Distribution (Donut) · Avg Monetary per Segment · Avg Recency per Segment
- **Slicers:** Segment · Recency Range · Monetary Range

### Features
- ✅ Custom Tooltips on key visuals
- ✅ Drill-through on Categories, Segments, and States
- ✅ Bookmark-based navigation between pages
- ✅ Cross-page filtering via slicers
- ✅ Consistent color palette across all pages

---

## 🎨 Design

Custom color palette applied consistently across all pages:

| Color | Hex | Usage |
|---|---|---|
| Olive Dark | `#283618` | Nav bar, primary bars |
| Olive Mid | `#606C38` | Secondary elements |
| Cream | `#FEFAE0` | Background |
| Orange Light | `#DDA15E` | Accent, active states |
| Orange Dark | `#BC6C25` | Alerts, negative KPIs |

---

## 📥 Download Dashboard

> The Power BI file (.pbix) is hosted on Google Drive due to file size.

[⬇️ Download Power BI Dashboard (.pbix)](https://drive.google.com/file/d/1Vmp7xYnGCdwGosZe99vaBHHg1WMbbOxW/view?usp=sharing)

---

## 📁 Repository Structure

```
├── Olist-ECommerce-End-to-End-Analysis.ipynb   # Python notebook (Kaggle)
├── Olist-Dashboard.pbix                         # Power BI dashboard
├── README.md
└── .gitignore
```

---

## 🛠️ Built With

- **Python** — Pandas, NumPy, Plotly
- **Power BI** — Star Schema, DAX, Interactive Dashboards

---

## 🔗 Links

- 📓 **Kaggle Notebook:** [Open in Kaggle](https://www.kaggle.com/code/abdallahahmed701/olist-ecommerce-end-to-end-analysis)
- 💼 **LinkedIn:** [Abdallah Ahmed](https://www.linkedin.com/in/abdallah-ahmed-16aa50290)
