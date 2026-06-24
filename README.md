# 🛍️ Customer Shopping Behaviour Analysis

An end-to-end data analysis project exploring customer shopping patterns using Python, PostgreSQL, and Power BI. The project covers data cleaning, feature engineering, SQL-based business analysis, and interactive dashboards.

---

## 📁 Project Structure

```
customer-shopping-behaviour/
│
├── customer_shopping_behavior.csv       # Raw dataset
├── customer_shopping_behaviour.ipynb    # Data cleaning & preprocessing (Python)
├── customer_behaviour.sql               # Business analysis queries (PostgreSQL)
└── customer_behaviour.pbix              # Power BI dashboard
```

---

## 📊 Dataset Overview

The dataset contains **3,900 customer records** with **18 features** covering demographics, purchase behaviour, and preferences.

| Feature | Description |
|---|---|
| `Customer ID` | Unique customer identifier |
| `Age` | Customer age (18–70) |
| `Gender` | Male / Female |
| `Item Purchased` | Product name |
| `Category` | Clothing, Footwear, Outerwear, Accessories |
| `Purchase Amount (USD)` | Transaction value in USD |
| `Location` | One of 50 US states |
| `Season` | Winter, Spring, Summer, Fall |
| `Review Rating` | Product rating (float) |
| `Subscription Status` | Whether the customer is subscribed |
| `Shipping Type` | E.g., Standard, Express |
| `Discount Applied` | Yes / No |
| `Promo Code Used` | Yes / No (dropped — redundant with Discount Applied) |
| `Previous Purchases` | Count of past purchases |
| `Payment Method` | Venmo, Cash, Credit Card, PayPal, Bank Transfer, Debit Card |
| `Frequency of Purchases` | E.g., Weekly, Monthly, Annually |

---

## 🐍 Data Cleaning & Preprocessing (Python)

Notebook: `customer_shopping_behaviour.ipynb`

Key steps performed:

- **Missing value imputation** — `Review Rating` nulls filled with the median rating per product category
- **Column renaming** — All columns converted to snake_case for consistency
- **Feature engineering:**
  - `age_group` — Customers segmented into Young Adult, Adult, Middle-aged, Senior using quartile binning (`pd.qcut`)
  - `purchase_frequency_days` — Frequency labels mapped to numeric day intervals (e.g., Weekly → 7, Monthly → 30)
- **Redundant column removal** — `promo_code_used` dropped (perfectly mirrors `discount_applied`)
- **Database export** — Cleaned DataFrame loaded into a PostgreSQL table via SQLAlchemy

---

## 🗄️ SQL Analysis (PostgreSQL)

File: `customer_behaviour.sql`

Ten business questions answered using SQL:

| # | Question |
|---|---|
| Q1 | Total revenue by gender |
| Q2 | Discount users who still spent above average |
| Q3 | Top 5 products by average review rating |
| Q4 | Average purchase amount: Standard vs. Express shipping |
| Q5 | Do subscribers spend more? Revenue and spend comparison |
| Q6 | Top 5 products with the highest discount application rate |
| Q7 | Customer segmentation — New, Returning, and Loyal |
| Q8 | Top 3 most purchased products within each category |
| Q9 | Are repeat buyers (>5 purchases) more likely to subscribe? |
| Q10 | Revenue contribution by age group |

Techniques used: `GROUP BY`, `HAVING`, subqueries, `CASE` statements, CTEs, and window functions (`ROW_NUMBER() OVER`).

---

## 📈 Power BI Dashboard

File: `customer_behaviour.pbix`

An interactive dashboard built on the cleaned and enriched dataset, visualising key metrics including revenue breakdowns, customer segments, category performance, and subscription trends.

---

## 🛠️ Tools & Technologies

- **Python** (pandas) — Data cleaning and feature engineering
- **PostgreSQL** — Relational database and business analysis
- **SQLAlchemy / psycopg2** — Python–PostgreSQL connector
- **Power BI** — Interactive dashboard and reporting

---

