# 🍕 Pizza Sales Analysis — Python EDA
**Python · Pandas · Matplotlib · Seaborn · Plotly · Jan–Dec 2015**

![Python](https://img.shields.io/badge/Python-3776AB?style=flat&logo=python&logoColor=white)
![Pandas](https://img.shields.io/badge/Pandas-150458?style=flat&logo=pandas&logoColor=white)
![Matplotlib](https://img.shields.io/badge/Matplotlib-FF6B35?style=flat)
![Seaborn](https://img.shields.io/badge/Seaborn-7C3AED?style=flat)
![Jupyter](https://img.shields.io/badge/Jupyter-F37626?style=flat&logo=jupyter&logoColor=white)

---

## 📌 Project Overview
End-to-end EDA of **48,620 pizza order records** using Python — computing KPIs, engineering time features, and producing 12+ visualisations covering daily/hourly/monthly demand, category & size breakdowns, heatmaps, and best/worst seller rankings.

---

## 📊 Key Metrics
| Metric | Value |
|---|---|
| Total Revenue | $817,860 |
| Total Orders | 21,350 |
| Pizzas Sold | 49,574 |
| Avg Order Value | $38.31 |
| Avg Pizza / Order | 2.32 |

---

## 🔁 Analysis Pipeline
`Load CSV` → `Inspect & dtypes` → `Feature Engineering` → `KPI Calculation` → `Visualisation` → `Insights`

---

## 💻 Core Code Snippets

```python
# KPIs
total_revenue      = df['total_price'].sum()
total_orders       = df['order_id'].nunique()
avg_order_value    = total_revenue / total_orders

# Time feature engineering
df['order_date'] = pd.to_datetime(df['order_date'], dayfirst=True)
df['day_name']   = pd.Categorical(df['order_date'].dt.day_name(),
                     categories=weekday_order, ordered=True)
df['order_hour'] = df['order_time'].dt.hour

# Heatmap pivot
sales_pivot = df.pivot_table(index='pizza_category', columns='pizza_size',
                values='total_price', aggfunc='sum', fill_value=0)
sales_pct   = sales_pivot / sales_pivot.sum().sum() * 100
sns.heatmap(sales_pct, annot=True, fmt=".1f", cmap="YlOrRd")

# Top 5 / Bottom 5
top5    = df.groupby('pizza_name')['total_price'].sum().sort_values(ascending=False).head(5)
bottom5 = df.groupby('pizza_name')['total_price'].sum().sort_values().head(5)
```

---

## 🔍 Analytical Findings
- **Peak day:** Friday · **Peak hours:** 12–1 PM & 6–7 PM · **Peak months:** July & January
- **Top revenue pizza:** Thai Chicken · **Top quantity:** Classic Deluxe · **Worst:** Brie Carre
- **Classic category** leads with 26.91% revenue share · **Large size** dominates at 45.89%

---

## 📈 Charts Produced
`Orders by Day` `Revenue by Day` `Orders by Hour` `Monthly Trend` `% Sales by Category`
`% Sales by Size` `Category × Size Heatmap` `Units by Category` `Top 5 Orders/Qty/Revenue` `Bottom 5 Orders/Qty/Revenue`

---

## 🛠 Tools & Libraries
`Python 3` `Pandas` `Matplotlib` `Seaborn` `Plotly Express` `NumPy` `Jupyter Notebook`

---

## 📁 Repository Files
| File | Description |
|---|---|
| `Pizza_Sales_Analysis_Report.ipynb` | Full EDA notebook — 47 cells · 12 visualisations |
| `pizza_sales.csv` | Raw dataset — 48,620 rows × 12 columns |
| `Pizza_Dashboard_Page1_Overview.png` | Overview dashboard — KPIs · trends · breakdown |
| `Pizza_Dashboard_Page2_BestWorst.png` | Best & Worst sellers — Top/Bottom 5 analysis |

---

## 🖼️ Dashboard Preview

**Page 1 — Sales Overview**
![Overview](Pizza_Dashboard_Overview.png?raw=true)

**Page 2 — Best & Worst Sellers**
![Best Worst](Pizza_Dashboard_Best_worst_Pizza.png?raw=true)

---
📓 Jupyter notebook included &nbsp;|&nbsp; 📦 48,620 records &nbsp;|&nbsp; 📈 12 visualisations &nbsp;|&nbsp; 🖼️ 2 dashboard pages
