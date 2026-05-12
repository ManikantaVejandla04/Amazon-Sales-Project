# 📦 Amazon Sales Performance Analysis — 2025

> A structured sales data project analyzing **250 orders** across product categories, customer locations, and payment methods on the Amazon platform — covering **February through April 2025**.

---

## 📋 Table of Contents

- [Project Overview](#project-overview)
- [Dataset Description](#dataset-description)
- [Workbook Structure](#workbook-structure)
- [Key Metrics & Insights](#key-metrics--insights)
- [Data Schema](#data-schema)
- [Pivot Table Summaries](#pivot-table-summaries)
- [How to Use](#how-to-use)
- [Technologies](#technologies)
- [License](#license)

---

## Project Overview

This project contains a cleaned and structured Amazon sales dataset used for business intelligence and sales performance reporting. The workbook provides raw transactional data, pre-built pivot table analyses, and a summary dashboard — making it suitable for exploratory data analysis, dashboard building, or academic/portfolio use.

**Scope:**
- 📅 Date Range: February 2, 2025 – April 2, 2025
- 🛒 Total Orders: 250
- 💰 Total Revenue: $243,845
- 📊 Average Order Value: $975.38

---

## Dataset Description

The dataset captures end-to-end order-level sales activity, including product details, customer demographics, payment behavior, and fulfillment status. It is designed to support multi-dimensional analysis across categories, geographies, and time periods.

**Products Covered (10 SKUs):**

| Category | Products |
|---|---|
| Electronics | Laptop, Smartphone, Smartwatch, Headphones |
| Home Appliances | Refrigerator, Washing Machine |
| Footwear | Running Shoes |
| Clothing | Jeans, T-Shirt |
| Books | Book |

**Customer Locations (11 Cities):**
Boston · Chicago · Dallas · Denver · Houston · Los Angeles · Miami · New York · San Francisco · Seattle · (unspecified)

---

## Workbook Structure

The Excel file (`Amazon_Sales_Project.xlsx`) contains **3 sheets**:

```
Amazon_Sales_Project.xlsx
├── amazon_sales_data 2025   ← Raw transactional data (250 rows)
├── Pivot tables              ← 6 pre-built pivot table analyses
└── Dashboard                 ← Visual summary of key performance metrics
```

### Sheet 1 — `amazon_sales_data 2025`
The primary data table with one row per order. Contains all fields needed to reproduce the pivot tables and dashboard independently.

### Sheet 2 — `Pivot tables`
Six pivot analyses built from the raw data:
1. Top Sales by Category
2. Top Sales by Product
3. Sales by Customer Location
4. Payment Method Usage
5. Order Status Distribution
6. Top Customers by Total Spending

### Sheet 3 — `Dashboard`
A visual summary panel titled **"Amazon Sales Performance Analysis"** providing an at-a-glance view of the business metrics.

---

## Key Metrics & Insights

### Revenue by Category

| Category | Revenue | Share |
|---|---|---|
| Electronics | $129,950 | 53.3% |
| Home Appliances | $105,000 | 43.1% |
| Footwear | $4,320 | 1.8% |
| Clothing | $3,540 | 1.5% |
| Books | $1,035 | 0.4% |
| **Total** | **$243,845** | **100%** |

### Order Status Distribution

| Status | Count | Percentage |
|---|---|---|
| Completed | 88 | 35.2% |
| Pending | 85 | 34.0% |
| Cancelled | 77 | 30.8% |

> ⚠️ A combined **64.8% of orders are unresolved** (Pending or Cancelled), suggesting potential opportunities to improve fulfillment rates and reduce cart abandonment.

### Payment Method Breakdown

| Method | Orders |
|---|---|
| PayPal | 60 |
| Credit Card | 54 |
| Debit Card | 53 |
| Gift Card | 42 |
| Amazon Pay | 41 |

### Top Customers by Revenue

| Rank | Customer | Total Spent |
|---|---|---|
| 1 | Olivia Wilson | $36,170 |
| 2 | Jane Smith | $31,185 |
| 3 | Emma Clark | $29,700 |
| 4 | Emily Johnson | $23,475 |
| 5 | David Lee | $22,665 |

### Top Cities by Revenue

| Rank | City | Revenue |
|---|---|---|
| 1 | Miami | $31,700 |
| 2 | Denver | $29,785 |
| 3 | Houston | $28,390 |
| 4 | Dallas | $27,145 |
| 5 | Boston | $26,170 |

---

## Data Schema

### `amazon_sales_data 2025` — Column Reference

| Column | Type | Description |
|---|---|---|
| `Order ID` | String | Unique order identifier (e.g., `ORD0001`) |
| `Date` | Date (serial) | Order date as Excel serial number |
| `Product` | String | Product name |
| `Category` | String | Product category |
| `Price` | Number | Unit price in USD |
| `Quantity` | Integer | Number of units ordered |
| `Total Sales` | Number | Computed as `Price × Quantity` |
| `Customer Name` | String | Full name of the customer |
| `Customer Location` | String | City of the customer |
| `Payment Method` | String | One of: Credit Card, Debit Card, PayPal, Amazon Pay, Gift Card |
| `Status` | String | One of: Completed, Pending, Cancelled |
| `month` | Integer | Extracted month (2 = Feb, 3 = Mar, 4 = Apr) |
| `Day` | Integer | Day of the month |
| `Year` | Integer | Year (2025) |

> **Note:** The `Date` column stores values as Excel date serial numbers (e.g., `45730`). To display correctly, format the column as `Date` in Excel or parse with `pd.to_datetime(df['Date'], origin='1899-12-30', unit='D')` in Python.

---

## Pivot Table Summaries

All six pivot tables on the `Pivot tables` sheet are derived from the raw data and can be refreshed automatically in Excel via **Data → Refresh All**.

| Pivot Table | Metric | Dimension |
|---|---|---|
| Top sales by category | Sum of Total Sales | Category |
| Top sales by product | Sum of Total Sales | Product |
| Sales by customer location | Sum of Total Sales | City |
| Payment method usage | Count of Order ID | Payment Method |
| Order status distribution | Count of Order ID | Status |
| Top customers by total spending | Sum of Total Sales | Customer Name |

---

## How to Use

### Option 1 — Excel / Google Sheets
1. Download `Amazon_Sales_Project.xlsx`
2. Open in Microsoft Excel or import into Google Sheets
3. Use the `Pivot tables` sheet for pre-built summaries, or create your own from `amazon_sales_data 2025`
4. The `Dashboard` sheet provides a ready-to-present visual overview

### Option 2 — Python (pandas)

```python
import pandas as pd

df = pd.read_excel("Amazon_Sales_Project.xlsx", sheet_name="amazon_sales_data 2025")

# Fix date column
df["Date"] = pd.to_datetime(df["Date"], origin="1899-12-30", unit="D")

# Revenue by category
print(df.groupby("Category")["Total Sales"].sum().sort_values(ascending=False))

# Order status distribution
print(df["Status"].value_counts())
```

### Option 3 — Power BI / Tableau
Connect directly to the `.xlsx` file. Use the `amazon_sales_data 2025` sheet as the data source and build custom visuals on top of it.

---

## Technologies

- **Microsoft Excel** — Data storage, pivot tables, and dashboard
- **Python / pandas** *(optional)* — Programmatic data analysis
- **Power BI / Tableau** *(optional)* — Advanced visualization

---

## License

This dataset is provided for **educational and portfolio purposes only**. Customer names and order data are synthetic/anonymized. Not intended for commercial use.

---

> **Questions or contributions?** Feel free to open an issue or submit a pull request.
