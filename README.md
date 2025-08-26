# Snitch Clothing Sales Data Cleaning & EDA

This repository contains a synthetic dataset of sales transactions from Snitch, a fictional Indian clothing brand. It’s crafted to mirror real-world retail data with intentionally uncleaned records, making it perfect for practicing data cleaning, exploratory data analysis (EDA), and dashboard development using Python, Power BI, or Excel.

## Table of Contents

- [Dataset Overview](#dataset-overview)  
- [Project Objectives](#project-objectives)  
- [Data Cleaning Tasks](#data-cleaning-tasks)  
- [Exploratory Data Analysis](#exploratory-data-analysis)  
- [Dashboard & Reporting](#dashboard--reporting)  
- [Tech Stack](#tech-stack)  
- [Key Findings from Snitch Fashion Sales Visualizations](#Key-Findings-from-Snitch-Fashion-Sales-Visualizations)  
- [Getting Started](#getting-started)  
- [Usage Examples](#usage-examples)  
- [Contributing](#contributing)  
- [License](#license)  

---

## Dataset Overview

The dataset simulates retail sales transactions, including fields such as:

- Order_ID  
- Customer_Name  
- Product_Category  
- Units_Sold  
- Sale_Date  
- City  
- Discount  

It intentionally includes inconsistencies (typos, nulls, negative values) to challenge data-cleaning workflows.

---

## Project Objectives

1. Clean and standardize key columns (e.g., remove typos, handle nulls).  
2. Perform EDA to uncover sales trends, top products, and regional performance.  
3. Build interactive dashboards for stakeholder reporting.  
4. Document the process so others can replicate and learn.

---

## Data Cleaning Tasks

- Standardize `Customer_Name` (trim spaces, unify casing).  
- Correct `Product_Category` typos using mapping or fuzzy matching.  
- Convert `Units_Sold` to numeric, remove negatives, impute missing.  
- Normalize `Sale_Date` formats and extract time-based features.  
- Clean `City` entries and consolidate similar locations.  

```python
import pandas as pd

df = pd.read_csv("data/snitch_sales_raw.csv")

# Example: Clean Units_Sold
df["Units_Sold"] = pd.to_numeric(df["Units_Sold"], errors="coerce")
df["Units_Sold"] = df["Units_Sold"].apply(lambda x: x if x >= 0 else pd.NA)
df["Units_Sold"].fillna(df["Units_Sold"].median(), inplace=True)
```

---

## Exploratory Data Analysis

- Monthly and yearly sales trends  
- Top 10 products by revenue  
- Customer purchasing frequency  
- Regional sales heatmap  

Visualizations can be created with libraries like Matplotlib, Seaborn, or Plotly.


<img width="984" height="484" alt="MonthlySalesTrends" src="https://github.com/user-attachments/assets/a1b6b583-c53d-4cb7-b87b-224b53da41a4" />


<img width="784" height="584" alt="TSalesbyProduct" src="https://github.com/user-attachments/assets/a0e3c4ed-b82c-4a9f-bcb1-3f9f268e63ed" />


<img width="661" height="684" alt="SalesDisbySeg" src="https://github.com/user-attachments/assets/edaec32b-ce50-4d7b-9d0e-77687ec9202a" />


---

## Dashboard & Reporting

Use Power BI or Excel to build:

- Sales overview with slicers for date range  
- Drill-down by product category and city  
- Monthly vs. target performance gauges  
- Customer segmentation charts


![SnitchClothings](https://github.com/user-attachments/assets/2807f482-1659-4e9d-9d5a-ce471872c9f1)


---

## Tech Stack

- Python 3.8+  [Download Here](https://anaconda.org/anaconda/jupyter)
- pandas, NumPy  
- Matplotlib, Seaborn, Plotly  
- Power BI Desktop or Excel [Download Here](https://powerbi.microsoft.com/en-us/blog/power-bi-may-2025-feature-summary/) 

---

# Key Findings from Snitch Fashion Sales Visualizations

Below are the main insights drawn from each of the seven charts.

---

## 1. Distribution of Discount Percentages

- The vast majority of orders receive relatively small discounts: over 60% of orders have discounts under 5%.  
- There is a long right tail, with ~5% of orders enjoying discounts above 20%.  
- This skew suggests most customers pay near full price, while a minority benefit from heavy promotions.

---

## 2. Unit Price vs. Profit Scatter

- Higher‐priced items (Unit Price > $3,000) generally yield higher absolute profits, clustering in the $1,000–$2,500 range.  
- A few high‐price outliers still show low or negative profit, indicating steep discounting or potential data issues (returns, cost mismatches).  
- Mid‐price segments (Unit Price $500–$2,000) display the greatest variability in profit, suggesting these items merit closer margin monitoring.

---

## 3. Profit by Product Category

- Jackets and Shoes lead in median profit, with typical profits around $1,200–$1,500 per order.  
- Jeans and T-Shirts sit in the middle tier, median profits roughly $400–$800.  
- Accessories and Dresses have the lowest median profits (sub-$300), and Dresses show the widest range—even some negative margins.

---

## 4. Top 10 Cities by Total Sales

- Mumbai emerges as the top market, capturing over 15% of all sales revenue.  
- Delhi and Bengaluru (counting both “bengaluru” and “Bangalore” entries) occupy the next two spots, each with 10–12%.  
- Ahmedabad, Pune, and Hyderabad also rank in the leading ten, indicating strong regional hubs beyond the metros.

---

## 5. Monthly Sales Trend by Customer Segment

- B2C sales climb steadily month over month, peaking around year-end holiday promotions.  
- B2B sales are more lumpy, with pronounced spikes at quarter-end months—likely driven by corporate procurement cycles.  
- Overall, B2C contributes around 60% of monthly revenue, while B2B’s share fluctuates between 30–40%.

---

## 6. Correlation Matrix of Key Metrics

- Sales_Amount correlates very strongly with Units_Sold (≈ 0.90) and Profit (≈ 0.92), as expected.  
- Unit_Price also shows a moderate positive correlation with Profit (≈ 0.60), reinforcing that upselling higher-priced items boosts margins.  
- Discount_% has a modest negative correlation with Profit (≈ –0.40), highlighting that deeper discounts erode profitability.

---

## 7. Discount % by Customer Segment

- B2B orders enjoy higher median discounts (~8%) than B2C orders (~4%).  
- B2B discounts also exhibit a wider spread: some corporate accounts receive over 20% off.  
- B2C discounts are more tightly clustered, rarely exceeding 15%.

---

# Strategic Implications

- **Optimize Discounting**: Most discounts are shallow; consider targeted promotions for underperforming segments (e.g., Dresses, Accessories).  
- **Product Focus**: Continue prioritizing Jackets and Shoes, which drive the highest profit per order.  
- **Regional Tailoring**: Deepen presence in Mumbai, Delhi, and Bengaluru, while exploring growth opportunities in second-tier cities.  
- **Segmented Campaigns**: Align B2B promotions with corporate buying cycles; use end-of-quarter offers to smooth revenue spikes.  
- **Data Quality Checks**: Investigate orders with high Unit Price but negative profit to correct potential errors in cost or returns data.

---

## License

This project is licensed under the MIT License.  

---
  
