# 🛒 Customer Purchase Behavior — Power BI Report

A 5-page interactive Power BI report analyzing customer purchase behavior, brand performance, promotional impact, and demographic segmentation across a 730-day study period.

---

## 📁 Repository Structure

```
├── Chocolate_Sales_Analysis.pbix   # Main Power BI report file
├── data/
│   ├── FACT_Purchase.csv           # Transaction-level fact table (~58,693 rows)
│   ├── DIM_Customer.csv            # Customer demographic dimensions (500 customers)
│   ├── DIM_Brand.csv               # Brand reference table (5 brands)
│   └── DIM_Date.csv                # Date dimension table (730 days)
└── README.md
```

---

## 📊 Report Pages

| Page | Title | Description |
|------|-------|-------------|
| 1 | Executive Summary | High-level KPIs, purchase trend, and brand share overview |
| 2 | Purchase Behavior & Brand Analysis | Brand performance, pricing, and promotional impact |
| 3 | Customer Demographics & Segmentation | Purchase patterns by age, income, education, occupation, and settlement size |
| 4 | Promotion & Price Sensitivity | Promo dependency, price tiers, and age-based promo response |
| 5 | Customer-Level Deep Dive | Individual customer profiles, top buyers, and purchase frequency |

---

## 🗃️ Data Model

The report uses a **star schema** with the following relationships:

- `FACT_Purchase[CustomerKey]` → `DIM_Customer[CustomerKey]`
- `FACT_Purchase[BrandKey]` → `DIM_Brand[BrandKey]`
- `FACT_Purchase[DateKey]` → `DIM_Date[DateKey]`

---

## 📐 Key Measures (DAX)

| Measure | Formula Description |
|---------|---------------------|
| Total Visits | Count of all rows in FACT_Purchase |
| Purchase Incidence | Sum of Incidence column (where Incidence = 1) |
| Conversion Rate | Purchase Incidence / Total Visits |
| Total Units Sold | Sum of Quantity column |
| Avg Units per Customer | Total Units Sold / Distinct Customer count |
| 7-Day Moving Avg | Rolling 7-day average of daily purchase incidence |
| Promotion Active | Calculated column — flags if any promotion was active on that row |
| Preferred Brand | Brand with highest units sold per customer |

---

## 🔢 Data Dictionary

### Demographic Codes

**Settlement Size**
| Code | Meaning |
|------|---------|
| 0 | Small (Rural) |
| 1 | Mid-sized (Suburban) |
| 2 | Large (Urban) |

**Education**
| Code | Meaning |
|------|---------|
| 0 | No education / Primary school |
| 1 | High school |
| 2 | University / Bachelor's degree |
| 3 | Postgraduate / Master's or higher |

**Occupation**
| Code | Meaning |
|------|---------|
| 0 | Unemployed / Unskilled |
| 1 | Skilled employee / Official |
| 2 | Management / Self-employed |

**Sex**
| Code | Meaning |
|------|---------|
| 0 | Male |
| 1 | Female |

**Marital Status**
| Code | Meaning |
|------|---------|
| 0 | Single |
| 1 | Married |

---

## 💡 Key Findings

- Overall conversion rate is approximately **25%** — 3 in 4 visits do not result in a purchase
- **Brand_2** leads in total units sold while **Brand_5** leads in total revenue, driven by its premium pricing
- **Brand_3 and Brand_5** have the strongest organic demand with 92%+ non-promotional purchases
- The **25–34 age group** is the largest purchasing segment; the **18–24 group** buys the least often but in the highest quantities per visit
- Customers in **small settlements** purchase the most, nearly double that of urban customers
- **High school educated, skilled-employee** customers form the core buyer profile

---

## 🛠️ Requirements

- **Power BI Desktop** (latest version recommended)
- No additional licenses or connectors required — all data is loaded from local CSV files

---

## 👤 Author- Bedadyuti Debnath

Built as part of a consumer behavior analytics project using transactional purchase data across 500 customers, 5 brands, and 730 days.
