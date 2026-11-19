# 🛍️ Walmart Customer Retention & Churn Analytics

[![Power BI](https://img.shields.io/badge/Power%20BI-Desktop-F2C811?style=flat&logo=powerbi&logoColor=black)](https://powerbi.microsoft.com/)
[![DAX](https://img.shields.io/badge/DAX-Data%20Modeling-0078D4?style=flat&logo=microsoft&logoColor=white)](https://learn.microsoft.com/en-us/dax/)
[![Data Modeling](https://img.shields.io/badge/Schema-5--Table%20Relational-2E8B57?style=flat)](https://github.com/KailasH1245/Walmart-Customer-Retention-Analytics)

An end-to-end retail retention and churn intelligence solution built on **multi-table Walmart customer and transaction data**. This project unifies 5 normalized retail datasets into a **4-page interactive Power BI diagnostic report** backed by custom **DAX measures**, behavioral segmentation tiers, and executive documentation.

---

## 🎯 Business Problem & Objectives
High customer acquisition costs make retention critical to retail profitability, yet blanket discounting often erodes margin without improving loyalty. Using transactional, demographic, store, and loyalty program data, this project answers four core business questions:
1. **Attrition & Root-Cause Diagnosis:** What share of the customer base has churned, and what are the primary operational or competitive drivers?
2. **Promotional ROI & Basket Lift:** Do promotional discounts measurably increase average order value or repeat purchase frequency?
3. **Loyalty Tier Effectiveness:** How do churn rates, point redemption rates, and Customer Lifetime Value (CLV) compare across Basic, Silver, Gold, and Elite tiers?
4. **Channel & Regional Risk:** How does customer retention vary across in-store vs. online channels, store formats, and geographic regions?

---

## 📊 Key Analytical Findings

| Metric | Value | Business Insight |
| :--- | :--- | :--- |
| **Overall Churn Rate** | `49.67%` (`149 / 300`) | Nearly half of the customer base has churned, funneling down from `300` total to `251` repeat customers. |
| **Top Churn Driver** | `36%` Competitor Switching | Competitor switching leads attrition, followed equally by **low engagement (32%)** and **prolonged inactivity (32%)**. |
| **Promotional Basket Lift** | `Rs. 516.30` vs. `Rs. 516.23` | Despite **49% promotional coverage**, average spend with vs. without a promotion is virtually identical—confirming zero basket lift. |
| **Loyalty Tier Paradox** | `55%` Elite Churn | **Elite tier** members showed the highest churn (**55%**), while **Basic tier** members had the lowest churn (**41%**) and highest avg CLV (**Rs. 590**) due to longer tenure. |
| **Channel & Income Gap** | `53.55%` In-Store Churn | In-store shoppers churn faster than online shoppers (**45.52%**), and low-income segments experience the highest attrition (**53%**). |
| **Regional Risk Outliers** | `60%` West / `58%` Central | **West (60%)** and **Central (58%)** regions significantly exceed the national churn average, while churn stays near **50%** across all store formats. |

---

## 🏗️ Data Pipeline & Architecture

```text
┌───────────────────────────┐     ┌──────────────────────────────────┐     ┌──────────────────────────────┐
│  5 Multi-Table Retail CSVs│ ──► │   Power BI Relational Model      │ ──► │  4-Page Executive Report     │
│ • Transactions & Churn    │     │ • 5 Normalized Tables (1:1 & *:1)│     │ • Churn & Root-Cause Overview│
│ • Demographics & Loyalty  │     │ • Core DAX KPIs (Churn %, CLV)   │     │ • Repeat Purchase & Loyalty  │
│ • Store Locations         │     │ • Frequency & Age Cohort Tiers   │     │ • Store & CLV Segmentation   │
└───────────────────────────┘     └──────────────────────────────────┘     └──────────────────────────────┘
