# Snitch Clothing Sales Data Cleaning & EDA

This repository contains a synthetic dataset of sales transactions from Snitch, a fictional Indian clothing brand. It’s crafted to mirror real-world retail data with intentionally uncleaned records, making it perfect for practicing data cleaning, exploratory data analysis (EDA), and dashboard development using Python, Power BI, or Excel.

## Table of Contents

- [Dataset Overview](#dataset-overview)  
- [Project Objectives](#project-objectives)  
- [Data Cleaning Tasks](#data-cleaning-tasks)  
- [Exploratory Data Analysis](#exploratory-data-analysis)  
- [Dashboard & Reporting](#dashboard--reporting)  
- [Tech Stack](#tech-stack)  
- [Project Structure](#project-structure)  
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

---

## Dashboard & Reporting

Use Power BI or Excel to build:

- Sales overview with slicers for date range  
- Drill-down by product category and city  
- Monthly vs. target performance gauges  
- Customer segmentation charts  

---

## Tech Stack

- Python 3.8+  [Download Here](https://anaconda.org/anaconda/jupyter)
- pandas, NumPy  
- Matplotlib, Seaborn, Plotly  
- Power BI Desktop or Excel [Download Here](https://powerbi.microsoft.com/en-us/blog/power-bi-may-2025-feature-summary/) 

---

## Project Structure

```
snitch-sales-project/
├── data/
│   ├── snitch_sales_raw.csv
│   └── snitch_sales_cleaned.csv
├── notebooks/
│   ├── 01_data_cleaning.ipynb
│   ├── 02_eda.ipynb
│   └── 03_dashboard_prototype.ipynb
├── reports/
│   └── dashboard.pbix
├── requirements.txt
└── README.md
```

---

## Getting Started

1. Clone the repo:  
   ```bash
   git clone https://github.com/yourusername/snitch-sales-project.git
   cd snitch-sales-project
   ```  
2. Install dependencies:  
   ```bash
   pip install -r requirements.txt
   ```  

---

## Usage Examples

- Run the cleaning notebook to generate `snitch_sales_cleaned.csv`.  
- Execute the EDA notebook to produce visual insights.  
- Open `reports/dashboard.pbix` in Power BI for an interactive dashboard.

---

## Contributing

Contributions are welcome! Feel free to open issues or submit pull requests for:

- New cleaning rules  
- Additional visualizations  
- Dashboard enhancements  

---

## License

This project is licensed under the MIT License.  

---

Looking ahead, you might explore:

- Building a predictive model (e.g., forecasting next quarter’s sales).  
- Deploying the dashboard to Power BI Service for live sharing.  
- Packaging the cleaning pipeline as a reusable Python module.  
