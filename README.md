# Bike Sales Performance Report
**By Osekhuemen Peter-Imoisili**

![Bike Sales Overview](images/overview.png)

---

## Project Story

This project didn't start the way I planned.

When I first loaded the dataset into Power BI, I immediately tried to structure it into a proper star schema — separating Customers, Geography, and Products into dimension tables. Then I realised something: it's just a flat dataset.

And there was no CustomerID. No unique identifier. Just Age, Age Group, and Gender.

At that point I had two choices:
- Force a model that *looked* correct by creating fake surrogate keys
- Or step back, accept what the data actually was, and work with it honestly

I chose the second option. I shifted to segment-level analysis — and that decision changed the entire direction of the report.

That's the real lesson here: knowing when *not* to force a model is just as important as knowing how to build one.

---

## Objective

Analyse bike sales performance across products, geographies, and customer segments to surface actionable business insights — not just charts.

---

# 📂 Dataset Information

The dataset contains sales-related information including:

* Revenue
* Profit
* Order Quantity
* Product Information
* Product Categories
* Customer Age
* Customer Age Group
* Gender
* Country
* Date

---

# Data Preparation Process

## 1️⃣ Data Cleaning

* Removed unnecessary fields
* Verified numeric columns
* Standardized date formatting
* Checked for duplicate and blank values

---

## 2️⃣ Data Modeling Attempts

Initially, I attempted to normalize the dataset into a star schema by creating:

* Customer dimension
* Geography dimension
* Product dimension

However, during the modeling process, I discovered that the dataset lacked:

* Customer IDs
* Product IDs
* Other unique identifiers

This created aggregation inconsistencies and incorrect revenue totals.

### Key Learning:

Instead of forcing a star schema structure, I reverted to using a clean flat-table model while maintaining a proper Date dimension for time intelligence calculations.

This improved:

* Data accuracy
* Aggregation consistency
* Simplicity of analysis

---

## 3️⃣ Date Table Creation

A dedicated Date table was created using DAX to support:

* Year-over-Year analysis
* Time intelligence calculations
* Trend analysis

Relationship:
`DimDate[Date] → Sales[OrderDate]`

---


## 📊 Report Pages

The report has 3 pages:

---

### Page 1 — Bike Sales Performance (Executive Overview)
The top-level summary for decision makers.

Key metrics:
- **85M** Total Revenue
- **32M** Total Profit
- **37.8%** Profit Margin
- **30M** Total Unit Cost
- **1M** Total Orders

### Purpose:

Designed for executives and stakeholders to quickly assess business health and growth.

---

### Page 2 — Product (Bike) Report
Focused on product-level performance analysis:

* Top-performing products
* Product profitability
* Product revenue contribution
* Revenue vs Profit scatter analysis
* Top 5 products over time

### Key Insight:

Bikes generated the majority of the company’s profit while Clothing underperformed.

---

### Page 3 — Customer Insight Report
Focused on demographic segmentation analysis:

* Revenue by Age Group
* Profit by Gender
* Customer segment trends
* Revenue contribution by demographic segment

### Important Note:

Since the dataset lacked Customer IDs, the analysis was performed at the demographic segment level rather than individual customer level.
---

## 💡 Key Insights

**1. The business is scalable, not just growing**
Profit margins remain stable as revenue grows (37.8% consistently) — this signals strong operational control, not just top-line expansion.

**2. Geographic concentration is a risk**
The US market dominates revenue. Heavy dependence on one market is a strategic vulnerability — geographic diversification should be a priority.

**3. Bikes carry the business**
Profit is heavily concentrated in the Bikes category. Accessories contribute moderately; Clothing underperforms relative to its presence in the portfolio.

**4. Some products drive volume but not margin**
The scatter chart reveals products with high order quantities but thin margins — a pricing or cost structure conversation worth having.

**5. The Adult segment (35–64) is the core customer**
This age group generates the most revenue across both genders. Marketing and product decisions should be anchored here.

---

## ⚠️ Challenges & Solutions

**No CustomerID in the dataset**
Rather than creating fake surrogate keys to force a star schema, I pivoted to segment-level analysis using Age Group and Gender. This kept the model honest and the insights meaningful.

**Building time intelligence on a flat dataset**
Created a proper Date table and built DAX measures for Year-over-Year growth and Revenue LY — enabling meaningful trend comparisons despite the flat structure.

**Designing for business conversations, not just visuals**
Shifted from "what chart fits here" to "what decision does this page support" — resulting in three distinct pages each serving a different stakeholder need.

---

# 🎨 Data Storytelling Features Implemented

* Drillthrough pages
* Custom tooltips
* KPI cards
* Time intelligence visuals
* Interactive filtering
* Executive-style report structure

---

## What I Learned

- When to abandon a data model that looks right but isn't supported by the data
- How to build time intelligence (YoY, Revenue LY) using DAX and a proper Date table
- Designing drill-through and tooltip pages for deeper product exploration
- Thinking like a business analyst translating visuals into business recommendations
, not just a dashboard builder 

Most importantly, I learned that:

> Good dashboards display data.
> Great dashboards drive decisions.


---

## 🛠 Tools & Technologies

| Tool | Purpose |
|------|---------|
| Excel | Source data |
| Power BI Desktop | Data modelling, DAX, interactive report |
| DAX | Time intelligence, custom measures |

---

## 📁 Repository Structure

```
bike-sales-analytics/
├── data/
│   └── bike_sales.xlsx         # Original source data
├── powerbi/
│   └── bike_sales_report.pbix  # Full Power BI report
├── images/
│   ├── overview.png
│   ├── product_report.png
│   └── customer_insight.png
└── README.md
```

---

## Dashboard Preview

![Bike Sales Performance](images/overview.png)
![Product Report](images/product_report.png)
![Customer Insight](images/customer_insight.png)

---

## Strategic Recommendations

Based on the analysis, the three moves I'd prioritise:

1. **Double down on high-margin products** — Bikes are the profit engine; protect and grow this category
2. **Reduce geographic dependency** — US concentration is a risk; expand into underpenetrated markets
3. **Reaccess Clothing strategy** — Reassessing the clothing category strategy.

---

## 🔗 Data Source [kaggle]

Dataset sourced from a publicly available bike sales Excel file commonly used for business intelligence practice projects.
