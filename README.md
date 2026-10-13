# ShopSmart Retail Group: Exploratory Data Analysis

**AnalystLab Africa Experience Lab | Week 1 | Mission DS01 | Data Science Track**
**Author:** Cheruiyot Nickson Kirui

Exploratory data analysis of ShopSmart Retail Ltd.'s 2025 retail data (50,000 orders, 5,000 customers, 500 products, 25 stores): cleaning, integrity checks, statistical testing, visualisation, feature engineering and customer segmentation.

## Headline findings
- Realised revenue (Completed orders) is **NGN 2.50B** from 16,529 orders; only **33.1%** of orders are Completed.
- Stores, regions, categories and membership tiers perform almost identically; eight statistical tests found **no significant differences**.
- The data has logic problems that should be fixed before modelling: an ambiguous discount field, 24% of orders priced below cost, and returns dated before their order.
- 21 stock records need restocking, but **74%** of records are heavily over-stocked.
- K-Means found four customer segments; 14% of customers ("Champions") generate 31% of revenue.

## Repository structure
```
Week1_DataScience_Project/
├── Week1_EDA.ipynb          # Main notebook (executed, with outputs)
├── Cleaned_Data/            # Cleaned tables, master dataset, features, cleaning log, KPI summary
├── Visualizations/          # All charts (PNG)
├── EDA_Report.pdf           # Full written report
├── Presentation.pptx        # Executive presentation
├── requirements.txt
├── README.md
└── data/                    # Raw ShopSmart CSV files (input)
```

## How to run
```bash
pip install -r requirements.txt
jupyter notebook Week1_EDA.ipynb      # then Kernel > Restart & Run All
```
The notebook reads the raw files from `data/` and writes to `Cleaned_Data/` and `Visualizations/`. Python 3.10+ is recommended.

## Notebook contents
1. Environment setup
2. Loading the data (head, tail, shape, columns, dtypes, missing values for all tables)
3. Data cleaning and integrity checks (documented in `Cleaned_Data/cleaning_log.csv`)
4. Exploratory data analysis: KPIs, descriptive statistics, statistical tests
5. Ten visualisations
6. Correlation analysis (matrix, heatmap, pair plot)
7. Feature engineering (order, customer and inventory features)
8. Ten business questions, with a bonus K-Means customer segmentation
9. Findings, recommendations and machine learning opportunities
10. Code quality and reproducibility notes

## Key assumptions
- **Revenue** = `line_total` on **Completed** orders (gross value across all statuses is reported alongside: NGN 7.58B).
- **Currency** is not stated in the data; values are assumed to be Nigerian Naira (NGN).
- **Discount** behaves as a flat amount (`line_total = quantity x unit_price - discount`). If it was meant to be a percentage, revenue is overstated by about NGN 250M.
- **Revenue by state** uses the store's state. **Return rate** = orders with a return / all orders.
- **Inventory value** = stock on hand x cost price. **Suppliers** are linked to products through brand (`supplier_name` = brand + " Supplies").
- Suspect records (returns before the order, refunds above the sale, sales below cost) are **flagged, not deleted**.

## Libraries
pandas, numpy, matplotlib, seaborn, missingno, scipy, scikit-learn (see `requirements.txt` for versions).

## Author
Cheruiyot Nickson Kirui | [LinkedIn](#) | #AnalystLabAfrica
