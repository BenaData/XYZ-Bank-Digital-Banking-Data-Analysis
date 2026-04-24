# XYZ Bank — Digital Customer Journey Analysis | FY 2024

![Excel](https://img.shields.io/badge/Excel-Executive%20Brief-217346?style=flat&logo=microsoft-excel&logoColor=white)
![MySQL](https://img.shields.io/badge/MySQL-Data%20Cleaning-4479A1?style=flat&logo=mysql&logoColor=white)
![Python](https://img.shields.io/badge/Python-Exploratory%20Analysis-3776AB?style=flat&logo=python&logoColor=white)
![Tableau](https://img.shields.io/badge/Tableau-Dashboard-E97627?style=flat&logo=tableau&logoColor=white)

---

## Business Problem

XYZ Bank's digital banking platform recorded strong registration growth in FY 2024,
with 2,000 new customers onboarded across Mobile App, USSD, Agent, and Branch channels.
However, monthly active user numbers were not growing at the same rate, raising concerns
at senior management level.

**The core question:** Where are customers dropping off in the digital journey,
which segments are most at risk, and what is the financial impact?

---

## Key Findings

| # | Finding | Detail |
|---|---------|--------|
| 1 | **Activation Gap** | 26.4% of registered customers (528) never made a single transaction after signing up |
| 2 | **Retention Crisis** | Only 19.6% of all registered customers were active by end of year |
| 3 | **Churn Dominates** | 45% of activated customers churned — the single biggest drop-off point |
| 4 | **High-Risk Segments** | SME had the highest churn rate (48.9%), Mass Affluent second (47.1%) |
| 5 | **Platform-Wide Problem** | Churn rates consistent across all channels (43–47%) — not a channel issue |
| 6 | **Revenue at Risk** | KSh 1.58 Billion at risk from churn and dormancy combined |

---

## Dashboard

👉 **[View Interactive Tableau Dashboard](https://public.tableau.com/app/profile/benard.mwinzi/viz/XYZBankDigitalCustomerJourneyAnalysis/DigitalCustomerJourneyAnalysis)**

![Dashboard Preview](https://github.com/BenaData/XYZ-Bank-Digital-Banking-Data-Analysis/blob/main/dashboard_preview.png.png)

The dashboard covers:
- Customer journey funnel (Registered → Activated → Active)
- Activation rate by channel and segment
- Retention breakdown by segment
- Revenue at risk from churn and dormancy

---

## Project Structure

```
├── digital_customers_raw.csv            # Raw dataset (2,012 rows with data quality issues)
├── xyz_bank_customers_analysed.csv      # Cleaned and analysed dataset (2,000 rows)
├── xyz_bank_data_cleaning.ipynb         # Phase 2 — Data cleaning in MySQL via Jupyter
├── XYZ_Bank_Exploratory_Analysis.ipynb  # Phase 3 — Exploratory analysis in Python
├── XYZ_Bank_Digital_Business_           
│   Executive_Brief_FY2024.xlsx          # Phase 5 — Executive brief
└── README.md
```

---

## Methodology

### Phase 1 — Data Generation
Designed a realistic 2,000-row digital banking customer dataset  to simulate real-world conditions.

### Phase 2 — Data Cleaning (MySQL + Jupyter Notebook)
Connected Python to MySQL via SQLAlchemy and PyMySQL. Conducted a structured
audit across all columns before applying any fixes. Each cleaning step followed
a **preview → apply → verify** pattern.

**Issues identified and resolved:**

| # | Issue | Records | Action |
|---|-------|---------|--------|
| 1 | Duplicate rows | 12 | Removed using ROW_ID deduplication |
| 2 | Impossible dates (first transaction before registration) | 25 | Set to NULL |
| 3 | Negative total_transactions | 8 | Corrected using ABS() |
| 4 | Segment casing inconsistencies | 37 | Standardised using TRIM() and UPPER/LOWER |
| 5 | Blank status values | 10 | Converted to NULL |
| 6 | Blank region values | 15 | Converted to NULL |
| 7 | Blank age_band values | 20 | Relabelled as 'Unknown' |
| 8 | Value/transaction mismatch (ETL failure) | 40 | Flagged as 'REVIEW' for Finance |
| 9 | VARCHAR date columns | 2 columns | Converted to DATE type |

**Final dataset: 2,000 rows × 14 columns**

### Phase 3 — Exploratory Analysis (Python)
Connected directly to MySQL database via SQLAlchemy. Analysis conducted in
Pandas with visualisations in Matplotlib and Seaborn.

Five analytical areas covered:
1. **Activation Analysis** — overall and by channel and segment
2. **Customer Funnel Analysis** — Registered → Activated → Active/Dormant/Churned
3. **Segment Analysis** — churn and retention rates by customer segment
4. **Channel Analysis** — churn and retention rates by registration channel
5. **Revenue Impact** — KSh value at risk from churn and dormancy

Additional data quality issues discovered and resolved during analysis:
- Segment casing inconsistencies missed in Phase 2 (CORPORATE, mass market, sme)
- 21 never-activated customers incorrectly labelled Active or Churned → reclassified as Dormant

### Phase 4 — Dashboard (Tableau Public)
Built an executive-ready interactive dashboard with 4 views and 4 KPI cards.
Published to Tableau Public for public access and portfolio presentation.

### Phase 5 — Executive Brief (Excel)
Produced a one-page boardroom-ready executive brief covering business context,
key findings, recommendations, and next steps. Formatted to professional
banking standards.

---

## Tools & Technologies

| Tool | Purpose |
|------|---------|
| Python (Pandas, Matplotlib, Seaborn) | Exploratory analysis and visualisation |
| MySQL | Data storage and cleaning |
| SQLAlchemy + PyMySQL | Python-MySQL connection |
| Jupyter Notebook | Documented, reproducible analysis |
| Tableau Public | Interactive executive dashboard |
| Microsoft Excel | Executive brief and reporting |

---

## How to Run

### Requirements
```bash
pip install pandas sqlalchemy pymysql matplotlib seaborn jupyter
```

### Setup
1. Clone this repository
```bash
git clone https://github.com/BenaData/xyz-bank-digital-analysis.git
```

2. Set up MySQL database
```sql
CREATE DATABASE xyz_bank;
USE xyz_bank;
```

3. Load the raw data
- Open `xyz_bank_data_cleaning.ipynb`
- Update the database connection string with your MySQL credentials
- Run all cells in order

4. Run the exploratory analysis
- Open `XYZ_Bank_Exploratory_Analysis.ipynb`
- Update the database connection string
- Run all cells in order

---

## Recommendations

1. **Fix Branch Onboarding** — Implement a 72-hour post-registration follow-up
   for Branch-onboarded customers. Target: improve activation rate from 56.4% to 70%.

2. **SME Retention Programme** — Launch tailored digital banking features for SME
   customers addressing bulk payments, payroll, and supplier management needs.

3. **Dormant Reactivation Campaign** — Target 410 dormant activated customers with
   push notifications and transaction fee waivers. Revenue at risk: KSh 394M.

4. **Platform UX Review** — Commission a product review focused on post-activation
   engagement. Consistent churn across all channels confirms a platform-level problem.

---

## Domain

Banking & Financial Services | Digital Business Analytics | Customer Journey Analysis

---

## Author

**Benard Musyoka Mwinzi**
Data Analyst | Nairobi, Kenya

[![LinkedIn](https://img.shields.io/badge/LinkedIn-Connect-0077B5?style=flat&logo=linkedin&logoColor=white)](https://www.linkedin.com/in/benard-musyoka1234/)
[![Tableau](https://img.shields.io/badge/Tableau-View%20Dashboard-E97627?style=flat&logo=tableau&logoColor=white)](https://public.tableau.com/app/profile/benard.mwinzi/viz/XYZBankDigitalCustomerJourneyAnalysis/DigitalCustomerJourneyAnalysis)
[![Portfolio](https://img.shields.io/badge/Portfolio-1B2A4A?style=flat)](https://benadata.github.io/)
