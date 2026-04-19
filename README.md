# Customer Purchase Data Pipeline & KPI Engine
### Bronze → Silver ETL Pipeline | Python · Pandas · MySQL · SQL

![Python](https://img.shields.io/badge/Python-3.8%2B-blue?style=flat-square&logo=python)
![Pandas](https://img.shields.io/badge/Pandas-2.0%2B-150458?style=flat-square&logo=pandas)
![MySQL](https://img.shields.io/badge/MySQL-8.0%2B-4479A1?style=flat-square&logo=mysql&logoColor=white)
![NumPy](https://img.shields.io/badge/NumPy-1.24%2B-013243?style=flat-square&logo=numpy)

---

## 📌 Business Objective

Retail businesses lose revenue to poor customer segmentation and uninformed discount strategies. This pipeline ingests, cleans, and transforms 3,900 customer purchase transaction records through a structured **Bronze → Silver** data preparation workflow, loads them into a normalized MySQL schema, and computes KPIs via SQL to surface high-value customer segments and behavioral spending patterns.

---

## 📂 Dataset Overview

| Property | Detail |
|----------|--------|
| Total Records | 3,900 customer purchase transactions |
| Attributes | 18 demographic & behavioral columns |
| Key Fields | Age, Gender, Subscription Status, Shipping Type, Discount Usage, Product Category, Purchase Amount, Customer Rating |
| Domain | Retail consumer purchase behavior |

---

## 🏗️ Architecture

```
Raw CSV (3,900 records · 18 attributes)
            │
            ▼
  [BRONZE LAYER]  ← Raw data preserved as-is, no modifications
            │
            ▼  Python · Pandas transformations
  [SILVER LAYER]  ← Cleaned, typed, imputed, feature-engineered
            │       loaded into normalized MySQL schema
            ▼
  [KPI LAYER]     ← SQL aggregations computing business metrics
                     structured for BI consumption
```

---

## ⚙️ Pipeline — Transformations Applied

### Bronze Layer
- Raw CSV ingested and preserved without modification
- Source of truth for all downstream reprocessing

### Silver Layer
- **Null Handling** — categorical nulls replaced with column mode; numerical nulls replaced with column median
- **Data Type Enforcement** — purchase amounts cast to DECIMAL, dates parsed to DATE type, categorical columns standardized
- **Feature Engineering** — derived `AgeGroup` buckets and `PurchaseFrequency` flags for segmentation queries
- **Schema Normalization** — 18 attributes mapped to typed MySQL columns with appropriate constraints

### KPI Layer
- SQL-based aggregations across subscription status, shipping preference, gender, and discount usage
- Revenue contribution computed per segment
- Average transaction value compared across behavioral groups

---

## 🔍 Business Questions Addressed

1. Which customer segments contribute the most to revenue?
2. How do discounts impact high-value customer spending?
3. Does shipping preference influence purchase value?
4. What is the revenue impact of customer subscriptions?
5. Which product categories receive the highest customer satisfaction?

---

## 📊 Key Business Insights

| Finding | Metric |
|---------|--------|
| Subscription revenue share | **~45%** of total revenue |
| Express shipping spend premium | **~12%** higher per transaction |
| Discount impact on high-value customers | Remained profitable — effective strategy confirmed |
| Female vs Male revenue | Female customers generated slightly higher total revenue |
| Top satisfaction driver | Specific product categories showed consistently high ratings |

---

## 💻 Tech Stack

| Component | Technology |
|-----------|------------|
| Transformation Engine | Python · Pandas · NumPy |
| Database | MySQL |
| KPI Computation | SQL |
| Notebook Environment | Jupyter |

---

## 📁 Project Structure

```
customer-purchase-pipeline/
│
├── notebooks/
│   └── etl_pipeline.ipynb      # Bronze → Silver transformation logic
├── sql/
│   └── kpi_queries.sql         # Segmentation & KPI SQL queries
├── data/
│   └── raw/                    # Raw CSV input (Bronze)
└── README.md
```

---

## 🚀 How to Run

**1. Install dependencies**
```bash
pip install pandas numpy sqlalchemy pymysql jupyter
```

**2. Set up MySQL database**
```sql
CREATE DATABASE customer_pipeline;
USE customer_pipeline;
```

**3. Run the ETL pipeline**
```bash
jupyter notebook notebooks/etl_pipeline.ipynb
```

**4. Run KPI queries**
```bash
# Open MySQL Workbench and execute sql/kpi_queries.sql
```

---

## 📄 License

This project is licensed under the MIT License.
