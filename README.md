# telco-churn-dashboard
Dashboard showing Telcom churn  
# 📊 Telecommunications Customer Churn Analytics

An end-to-end cloud analytics project investigating customer attrition drivers for a telecommunications provider. Built using **Google BigQuery** for cloud data warehousing and SQL transformation, **Looker Studio** for interactive business intelligence, and custom **HTML5/CSS3** for responsive web presentation.

🔗 **Live Interactive Dashboard:** [View Project on GitHub Pages](https://YOUR_USERNAME.github.io/telco-churn-dashboard/)

---

## 🎯 Business Problem & Churn Definition
Customer acquisition in telecommunications is significantly more expensive than retention. Understanding *who* is leaving and *why* enables targeted retention campaigns.

* **Dataset:** IBM Telco Customer Churn (`7,043` customer records across `21` demographic, service, contract, and billing attributes).
* **Churn Definition:** Customers who cancelled or terminated their service within the last month (`Churn = "Yes"` / `TRUE`, representing a ~26.5% baseline churn rate).
* **Tenure Definition:** Total number of months (`0` to `72`) a customer remained subscribed prior to churning or reaching the end of the observation window.

---

## 🏗️ Cloud Architecture & Data Pipeline

1. **Data Warehouse (`Google BigQuery`):** Raw dataset stored in `local-pointer-383413.customer_data.Telco`.
2. **Data Cleaning & Transformation (`BigQuery SQL`):**
   * Stripped whitespace and converted blank strings in `TotalCharges` to `NULL`, safely casting the column to `FLOAT64`.
   * Standardized the boolean `Churn` flag (`TRUE`/`FALSE`) into human-readable `"Yes"` and `"No"` categories in a clean production table (`Telco_Cleaned`).
3. **BI Modeling & Visualization (`Looker Studio`):**
   * Connected natively to BigQuery (`Telco_Cleaned`).
   * Engineered custom calculated fields (`Is_Churned`, `Churn Rate %`) and bucketed raw `tenure` months into chronological lifecycle stages (`Tenure Group`).
4. **Web Presentation (`HTML5 & CSS3`):**
   * Embedded the live Looker Studio report inside a responsive, dark-themed portfolio wrapper hosted via GitHub Pages.

---

## 📝 Project Change Log

| Phase | Action / Modification Description | Status |
| :--- | :--- | :--- |
| **Phase 0: Setup** | Selected Telco Customer Churn dataset and defined cloud architecture (`BigQuery` $\rightarrow$ `Looker Studio` $\rightarrow$ `HTML/CSS` $\rightarrow$ `GitHub Pages`). | Complete |
| **Phase 1: Ingestion** | Loaded raw dataset into Google BigQuery (`local-pointer-383413.customer_data.Telco`). | Complete |
| **Phase 2: SQL Cleaning** | Resolved BigQuery type mismatches: converted empty `TotalCharges` spaces to `NULL` (`FLOAT64`) and replaced `TRIM()` on boolean `Churn` with native `IS TRUE` / `IS FALSE` checks. | Complete |
| **Phase 3: BI Modeling** | Connected Looker Studio to `Telco_Cleaned`, defined churn KPIs, created chronological `Tenure Group` buckets, and built interactive charts. | Complete |
| **Phase 4: Web & Hosting** | Fixed embed URL syntax, built responsive `index.html` container, and prepared repository for GitHub Pages deployment. | Complete |

---

## 💡 Key Analytical Insights

* **Contract Commitment:** Month-to-month customers experience drastically higher churn (~42%) compared to customers locked into one-year (~11%) or two-year (<3%) contracts.
* **Early Lifecycle Risk:** Customers within their first **0–6 months** of tenure represent the highest-risk segment, highlighting the importance of early onboarding support and promotional incentives.
* **Payment Friction:** Customers paying via electronic check exhibit notably higher churn rates than those enrolled in automatic bank transfers or credit card payments.

---

## 📂 Repository Structure

```text
telco-churn-dashboard/
├── index.html             # Responsive HTML5/CSS3 portfolio page with live Looker Studio embed
├── clean_telco_data.sql   # BigQuery SQL data cleaning and type-standardization script
└── README.md              # Project documentation, insights, and change log
