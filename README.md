
# Candy Sales Analysis (US & Canada) – Python EDA Project

This project analyzes a candy company’s sales data across the **US and Canada**, focusing on:
data cleaning, feature engineering, business KPIs, performance vs targets, and time-series trends.

The analysis was performed in **Python (Pandas)** inside a Jupyter Notebook.

---

## What’s Included (Files & Tools)

This project includes:
- **Python / Jupyter Notebook** – core analysis and visualizations
- **CSV datasets** – sales, customers, products, factories
- **JSON** – division sales targets (Chocolate / Sugar / Other) :contentReference[oaicite:0]{index=0}
- **PDF / PNG outputs** – exported charts (e.g., daily sales trend) :contentReference[oaicite:1]{index=1}

---

## Dataset Files

- `Sales_US.csv` – main sales dataset (US)
- `Sales_CA.csv` – sales dataset (Canada)
- `Customers.csv` – customer details (incl. age and address)
- `Candy_Products.csv` – product catalog (division, unit price, unit cost, factory, etc.)
- `Candy_Factories.csv` – factories with geo coordinates (latitude/longitude)
- `Candy_Targets.json` – sales targets per division (Chocolate/Sugar/Other) :contentReference[oaicite:2]{index=2}

---

## Key Analysis Steps

### 1) Data Cleaning & Standardization
- Unified column naming to a consistent format (snake_case style)
- Converted date columns to datetime (`order_date`, `ship_date`)
- Handled missing values (e.g., customer address filled as “unknown”)
- Parsed numeric columns safely (e.g., postal_code coercion)

### 2) Feature Engineering
Created additional business fields, such as:
- **shipping_cost** derived from `ship_mode` mapping
- **sales_level** categorical bucket (low / med / high) based on sales thresholds
- **total_price** = `units * cost`
- Derived **year/month** from order dates to support time-based analysis

### 3) Business KPI Exploration
- Top and bottom customers by sales
- Customer-level aggregations (sum/mean, min/max/total)
- Product-level and location-level (city/country) activity and counts
- Filtering logic for “high impact” orders (units and/or value)

### 4) Targets vs Actuals (Division Performance)
- Aggregated total sales by division
- Joined with division targets and flagged whether each division reached the target :contentReference[oaicite:3]{index=3}

### 5) Time-Series Trend (Daily Sales)
- Built a daily sales series and visualized the sales trend over time  
- Exported the trend chart (also saved as `daily_sales.pdf`) :contentReference[oaicite:4]{index=4}

---

## Outputs

- `daily_sales.pdf` – Daily sales over time chart :contentReference[oaicite:5]{index=5}
- (Optional) `cities.csv` – extracted location dataset exported from the notebook

---

## How to Run

### Option A — Run in VS Code / Jupyter
1. Ensure all files are in the same project folder:
   - `candy_data.ipynb`
   - `Sales_US.csv`, `Sales_CA.csv`, `Customers.csv`
   - `Candy_Products.csv`, `Candy_Factories.csv`
   - `Candy_Targets.json`
2. Open the notebook and run cells from top to bottom.

### Option B — Create a Clean Python Environment (Recommended)
```bash
python -m venv .venv
# Windows:
.venv\Scripts\activate
# macOS/Linux:
source .venv/bin/activate
pip install pandas matplotlib seaborn
