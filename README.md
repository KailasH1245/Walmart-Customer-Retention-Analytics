# 🛍️ Walmart Customer Retention & Churn Analytics (Power BI)

> **Executive Summary:** An end-to-end Power BI diagnostic solution analyzing customer churn drivers, loyalty tier performance, and promotional ROI across multi-table retail transaction and customer data.

![Walmart Churn & Retention Dashboard](Page%201.png)

---

## 📋 Table of Contents
- [Key Business Insights](#-key-business-insights)
- [Data Model & DAX Architecture](#️-data-model--dax-architecture)
- [Dashboard Walkthrough](#-dashboard-walkthrough)
- [Strategic Recommendations](#-strategic-recommendations)
- [Repository Structure](#-repository-structure)
- [How to Run](#-how-to-run)

---

## 📊 Key Business Insights

Diagnostic analysis revealed a critical retention bottleneck: **49.67% of the customer base (149 of 300 customers) has churned.**

- **Primary Churn Drivers:** Competitor switching (**36%**) is the leading cause of attrition, followed equally by low engagement (**32%**) and prolonged inactivity (**32%**).
- **Zero Promotional Lift on Basket Size:** Blanket discounts failed to increase order value—average spend remained virtually identical with a promotion (**Rs. 516.30**) vs. without (**Rs. 516.23**).
- **The Loyalty Tier Paradox:** **Elite tier** members exhibited the highest churn rate (**55%**), whereas **Basic tier** members had the lowest churn (**41%**) and highest average CLV (**Rs. 590**), driven by longer tenure.
- **High-CLV Win-Back Opportunity:** Scatter plot segmentation isolated a high-value cohort of previously loyal customers who recently went inactive—representing the highest-ROI target for immediate retention outreach.
- **Geographic Risk Concentration:** The **West (60%)** and **Central (58%)** regions significantly outperformed the national churn average.

---

## 🛠️ Data Model & DAX Architecture

### Relational Schema
The Power BI data model connects transactional records with customer, loyalty, and store attributes across five normalized tables:

- **`Customer_Transactions` (Fact Table):** Granular purchase records linked via `Customer_ID` (`*:1`) and `Store_ID` (`*:1`).
- **`Customer_Demographics` (Dimension):** Core customer profile (age, gender, region, income bracket, tenure, preferred channel).
- **`Store_Locations` (Dimension):** Store format (Supercenter, Sam's Club, etc.), region, and opening year.
- **`Loyalty_Program` & `Churn_Labelled_Customers` (Attribute Tables):** Linked `1:1` via `Customer_ID` to track points earned/redeemed, tier status, and churn classification.

### Core DAX Measures & Calculated Columns
- **Churn Rate %:** `DIVIDE([Churned Customers], [Total Customers], 0)`
- **Customer Lifetime Value (CLV):** `DIVIDE([Total Amount Spent], [Membership Duration (Years)], 0)`
- **Purchase Frequency Tiers:** Segmented into **Low-Tier** (0–3 orders), **Mid-Tier** (4–8 orders), and **High-Tier** (9+ orders).
- **Age Cohorts:** Grouped into 5 demographic brackets (`18–25`, `26–35`, `36–45`, `46–55`, `55+`).

---

## 📈 Dashboard Walkthrough

### 1. Churn & Retention Overview
Diagnoses **who** is churning and **why**, featuring a retention funnel (`300 Total` → `251 Repeat` → `149 Churned`). In-store shoppers churn at a higher rate (**53.55%**) than online shoppers (**45.52%**), and low-income segments show the highest attrition (**53%**).

### 2. Repeat Purchase Behavior
![Repeat Purchase Behavior](Page%202.png)
Tracks order frequency and category stickiness. Customers aged **55+** shop most frequently (**3.8 avg orders**), **Groceries** anchor repeat visits ahead of Apparel and Electronics, and only **0.68%** of customers reach High-Tier purchase volume.

### 3. Promotion & Loyalty Effectiveness
![Promotion & Loyalty Effectiveness](Page%203.png)
Evaluates marketing ROI across loyalty tiers. Despite a **49% promotional coverage rate**, discounts do not lift basket size, while Basic tier members show the lowest point redemption rate (**67%**).

### 4. Store Performance & CLV Segmentation
![Store Performance & CLV](Page%204.png)
Maps CLV against recency/frequency across store formats. Churn hovers near **50% across all store types**, confirming a systemic retention gap rather than an isolated store-operations issue.

---

## 💡 Strategic Recommendations

1. **Launch Targeted High-CLV Win-Back Campaigns:** Replace blanket discounts with personalized reactivation offers aimed strictly at High-CLV inactive customers identified in the CLV segmentation matrix.
2. **Restructure Loyalty Tier Incentives:** Introduce automated point-expiry alerts and double-point events to boost Basic tier redemption above 67%, while adding exclusive experiential perks to curb the 55% Elite tier churn.
3. **Close the Omnichannel & Digital Gap:** Counter competitor switching (36% of churn) by promoting online ordering incentives and faster fulfillment, leveraging the lower churn rate seen among digital shoppers.
4. **Deploy Regional Retention Interventions:** Prioritize localized marketing and customer feedback audits in the **West (60% churn)** and **Central (58% churn)** regions.

---

## 📂 Repository Structure

```text
Walmart-Customer-Retention-Analytics/
├── Customer Churn Analysis.pbix     # Power BI report (data model, DAX measures & visuals)
├── Walmart_Report.pdf               # Executive analytical report (PDF)
├── Walmart_Report.docx              # Editable analytical report (Word)
├── Churn_Labelled_Customers.csv     # Churn flags, recency dates & exit reasons
├── Customer_Demographics.csv        # Customer profile, income & channel preferences
├── Customer_Transactions.csv        # Transaction log with spend & promotion flags
├── Loyalty_Program.csv              # Tier status, points earned & points redeemed
├── Store_Locations.csv              # Store format, region & launch year
├── Page 1.png ... Page 4.png        # High-resolution dashboard exports
└── README.md
