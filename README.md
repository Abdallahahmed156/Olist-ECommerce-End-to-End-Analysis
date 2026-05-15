#  Olist E-Commerce — End-to-End Analysis

> A full data analysis pipeline on the Brazilian E-Commerce Public Dataset by Olist — from raw data to business insights, using Python, Power BI, and Excel.

---

##  Project Overview

This project transforms raw transactional data from 9 relational tables into actionable business insights across three tools, each handling a different layer of the analysis pipeline.

| Layer | Tool | Role |
|---|---|---|
| Data Cleaning & EDA | Python (Kaggle) | Merging, cleaning, feature engineering, visualization |
| Data Modeling & BI | Power BI | Star schema, DAX measures, interactive dashboards |
| Reporting | Excel | Executive summary & static reporting |

---

##  Workflow

```
Raw Data (9 CSV files)
        ↓
  Python — Cleaning & EDA
        ↓
  9 Clean CSVs exported
        ↓
  Power BI — Star Schema + DAX + Dashboards
        ↓
  Excel — Final Report
```

---

##  Python — What Was Done

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

##  Power BI — Coming Soon

- Star Schema data model (Facts + 6 Dimension tables)
- DAX measures for Revenue, AOV, Delivery Rate, Customer LTV
- Interactive dashboards: Sales Performance, Logistics, Customer Segments

---

##  Repository Structure

```
├── Olist-ECommerce-End-to-End-Analysis.ipynb   # Python notebook (Kaggle)
├── README.md
└── .gitignore
```

> Power BI (.pbix) and Excel files will be added upon completion.

---

##  Built With

- **Python** — Pandas, NumPy, Plotly
- **Power BI** — Data Modeling, DAX, Dashboards *(in progress)*
- **Excel** — Reporting *(in progress)*

---

## 🔗 Links

- 📓 **Kaggle Notebook:** [Open in Kaggle](https://www.kaggle.com/code/abdallahahmed701/olist-ecommerce-end-to-end-analysis)
- 💼 **LinkedIn:** [Abdallah Ahmed](https://www.linkedin.com/in/abdallah-ahmed-16aa50290)
