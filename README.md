
# 📊 Sales Performance Dashboard — Power BI

## Author
Amantha Bhaskarabhatla
LinkedIn: https://www.linkedin.com/in/amantha-bhaskarabhatla/


## Overview
An interactive multi-page Sales Performance Dashboard built in Power BI using the Superstore retail dataset. The dashboard analyzes sales trends, product performance, and customer behavior across 2015–2019, with a focus on Year-over-Year growth comparison.

---

## Dataset
- **Source:** Superstore Sales Dataset (public retail dataset)
- **Tool:** Microsoft Power BI Desktop
- **Records:** ~10,000 rows
- **Date Range:** 2015 – 2019
- **Columns:** Order ID, Order Date, Ship Date, Ship Mode, Customer ID, Customer Name, Segment, City, State, Region, Product ID, Category, Sub-Category, Product Name, Sales

---

## Data Model
- Built a **Star Schema** with `train` as the fact table
- Created a custom **Calendar Table** in Power Query (M language) with:
  - Date, Year, Month Number, Month Name
  - Month Year (display label)
  - Month Year Sort (chronological sort column)
- Established relationships:
  - `Calendar[Date]` → `train[Order Date]` (Many to One)
- Set Data Categories for map visuals:
  - Country, State, City

---

## Data Preparation (Power Query)
- Created Calendar Table from scratch using M language
- Added Month Year display column (`MMM yyyy` format)
- Added Month Year Sort column for correct chronological ordering
- Set correct data types for all columns

---

## DAX Measures Created
| Measure | Formula Summary |
|---|---|
| `Total Sales` | `SUM(train[Sales])` |
| `Total Orders` | `DISTINCTCOUNT(train[Order ID])` |
| `Sales Last Year` | `CALCULATE([Total Sales], SAMEPERIODLASTYEAR('Calendar'[Date]))` |
| `YoY Growth %` | `DIVIDE([Total Sales] - [Sales Last Year], [Sales Last Year], 0) * 100` |
| `Avg Order Value` | `DIVIDE([Total Sales], [Total Orders], 0)` |

---

## Dashboard Pages

### Page 1 — Executive Summary
- **KPI Cards:** Total Sales, Total Orders, YoY Growth %
- **Line Chart:** Current year vs Prior year sales by month
- **Bar Chart:** Top 15 Products by Sales
- **Map:** Sales by Location (bubble size = Sales)

### Page 2 — Product Performance
- **Bar Chart:** Top 10 Products by Sales
- **Bar Chart:** Bottom 10 Products by Sales
- **Donut Chart:** Sales by Category (Technology, Furniture, Office Supplies)
- **Treemap:** Sales by Sub-Category
- **Pie Chart:** Sales by Segment (Consumer, Corporate, Home Office)

### Page 3 — Customer & Regional Performance
- **Bar Chart:** Top 10 Customers by Sales
- **Bar Chart:** Sales by State (Top states)
- **Pie Chart:** Sales by Region (West, East, Central, South)
- **Pie Chart:** Sales by Ship Mode
- **Donut Chart:** Average Order Value by Segment

---

## Key Insights
- **Technology** is the highest revenue category at 36.59% of total sales
- **California** is the top performing state by sales
- **Consumer segment** accounts for over 50% of total sales
- **Standard Class** is the most used shipping mode at 59.29%
- **West region** leads in total sales at 31.4%
- YoY Growth of **24.78%** from 2017 to 2018

---

## Design Decisions
- Consistent blue color theme (`#2F5597` primary, `#F4A460` accent)
- Segoe UI font throughout
- Sentiment colors for positive/negative KPI indicators
- Removed gridlines for cleaner visual presentation

---

## Skills Demonstrated
- Data modeling (Star Schema)
- Power Query / M language
- DAX — time intelligence, KPI measures
- Year-over-Year analysis using `SAMEPERIODLASTYEAR`
- Multi-page dashboard design
- Map visuals with Data Categories
- Custom Calendar Table creation
- Top N filtering

---

## How To Use
1. Download the `.pbix` file
2. Open in **Power BI Desktop** (free)
3. Use the **Year slicer** on Page 1 to filter by year
4. Navigate between pages using the tabs at the bottom
5. Hover over visuals for detailed tooltips

---

## Tools Used
- Microsoft Power BI Desktop
- Power Query (M Language)
- DAX (Data Analysis Expressions)

