# Walmart Customer Retention Analytics Dashboard

> **Project Overview:** A comprehensive Power BI analytics solution designed to diagnose customer churn, analyze loyalty program effectiveness, and uncover actionable retention strategies using a dataset of 300 customers.

This project was developed as part of the **Power BI Analytics** course by **Internshala Trainings**. The goal was to build an interactive dashboard that answers critical business questions: *Why are customers leaving? Which segments are most at risk? And how effective are our current loyalty and promotion strategies?*

---

## Table of Contents
- [Key Business Insights](#-key-business-insights)
- [Technical Architecture](#️-technical-architecture)
- [Dashboard Walkthrough](#-dashboard-walkthrough)
- [Strategic Recommendations](#-strategic-recommendations)
- [Project Structure](#-project-structure)
- [How to Use](#-how-to-use)

---

## 📊 Key Business Insights

The analysis uncovered a critical retention challenge: **~50% of the customer base has churned.**

### 🚨 Critical Findings
- **Churn Rate:** 49.67% (149 out of 300 customers).
- **Top Churn Reasons:** Competitor switching (36%), followed closely by low engagement (32%) and inactivity (32%).
- **Promotion Inefficacy:** Promotions have **zero measurable impact** on basket size — average spend is nearly identical with (Rs. 516.30) and without (Rs. 516.23) a discount.
- **Loyalty Paradox:** The **Elite tier** has the highest churn rate (55%), while the **Basic tier** has the lowest (41%).
- **High-Value At-Risk Segment:** A distinct group of "High CLV" customers has recently gone inactive — the most critical target for win-back campaigns.
- **Geographic Hotspots:** The **West (60%)** and **Central (58%)** regions show the highest churn rates.

---

## 🛠️ Technical Architecture

### Data Model
The solution uses a **star schema** with `Customer_Demographics` as the central fact table.

**Relationships:**
- `(1)` Customer_Demographics → `(*)` Customer_Transactions (via `Customer_ID`)
- `(1)` Customer_Demographics → `(*)` Loyalty_Program (via `Customer_ID`)
- `(1)` Customer_Demographics → `(*)` Churn_Labelled_Customers (via `Customer_ID`)
- `(1)` Store_Locations → `(*)` Customer_Transactions (via `Store_ID`)

### Datasets Used
| Dataset | Description |
| :--- | :--- |
| `Customer_Demographics.csv` | Age, gender, region, income, membership date, preferred channel |
| `Customer_Transactions.csv` | Transaction ID, store, product category, amount, promotion flags |
| `Store_Locations.csv` | Store type, region, opening year |
| `Loyalty_Program.csv` | Loyalty tier, points earned, points redeemed |
| `Churn_Labelled_Customers.csv` | Churn flag, last purchase date, churn reason |

### Key Calculations (DAX)
- **CLV (Customer Lifetime Value):** `Total_Amount_Spent / Membership_Duration_Years`
- **Churn Rate %:** `(Churned Customers / Total Customers) * 100`
- **Purchase Segments:** Discretized into Low-Tier (0–3), Mid-Tier (4–8), and High-Tier (9+) purchases.
- **Age Groups:** Segmented into 5 distinct cohorts (18–25, 26–35, etc.).

---

## 📈 Dashboard Walkthrough

### 1. Churn & Retention Analysis
Identifies **who** is leaving and **why**.
- **Demographics:** Low-income customers churn the most (53%).
- **Channel:** Store customers churn more (53.55%) than online customers (45.52%).
- **Retention Funnel:** Visualizes the drop-off from Total Customers (300) → Repeat Customers (251) → Churned Customers (149).

### 2. Repeat Purchase Behavior
Focuses on engagement frequency and product preferences.
- **Frequency:** Older customers (55+) shop most frequently (3.8 avg).
- **Categories:** Groceries drive the most repeat visits, followed by Apparel and Electronics.
- **Engagement Gap:** Only **0.68%** of customers (2 out of 300) are High-Tier purchasers.

### 3. Promotion & Loyalty Effectiveness
Tests the ROI of current marketing efforts.
- **Promotions:** Despite a 49% promotion rate, they fail to increase basket size.
- **Loyalty Redemption:** Basic tier members have the lowest redemption rate (67%), suggesting the program feels less valuable to them.

### 4. Store Performance & CLV
Analyzes value per customer and store format impact.
- **CLV Surprise:** Basic tier customers actually hold the highest CLV (Rs. 590), likely due to longer membership duration.
- **Store Format:** Churn is roughly 50% across all store types (Supercenter, Sam's Club, etc.), indicating a systemic issue rather than a location-specific one.

---

## 💡 Strategic Recommendations

Based on the data, the following actions are recommended to improve retention:

1. **Win back high-value inactives** — Prioritize customers with High CLV who have recently gone silent (identified via the scatter plot). Use personalized offers rather than blanket promotions.
2. **Revamp the loyalty program:**
   - Implement point-expiry reminders, especially for Basic tier members.
   - Add visual progress bars to encourage tier upgrades.
   - Run "double-point" events to re-engage Basic members.
3. **Improve the online experience** — Since competitor switching is the top churn reason, invest in Walmart.com UX, faster delivery, and exclusive online deals to compete with Amazon.
4. **Target regional campaigns** — Focus retention efforts urgently in the West and Central regions, where churn exceeds 58%.

---

## 📂 Project Structure

```text
Walmart-Customer-Retention-Analytics/
│
├── Churn_Labelled_Customers.csv     # Churn flag, last purchase date, churn reason
├── Customer_Demographics.csv        # Age, gender, region, income, membership date
├── Customer_Transactions.csv        # Transaction ID, store, category, amount, promo flag
├── Loyalty_Program.csv              # Loyalty tier, points earned, points redeemed
├── Store_Locations.csv              # Store type, region, opening year
│
├── Customer Churn Analysis.pbix     # Power BI dashboard (data model + visuals)
│
├── Walmart_Report.pdf               # Full analytical report (PDF)
├── Walmart_Report.docx              # Full analytical report (Word)
│
├── Page 1.png ... Page 4.png        # Dashboard page screenshots
│
└── README.md                        # This file
```

---

## ▶️ How to Use

1. Clone or download this repository.
2. Open `Customer Churn Analysis.pbix` in [Power BI Desktop](https://www.microsoft.com/en-us/power-platform/products/power-bi/desktop) to explore the interactive dashboard.
3. Source data lives in the five `.csv` files in the repo root — refresh or re-point the data model to update figures.
4. See `Walmart_Report.pdf` / `Walmart_Report.docx` for the full write-up, or the `Page 1–4.png` screenshots for a quick visual preview.
