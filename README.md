https://github.com/SriramSrinivasan1/Hospital-Patients-Records/tree/main/data-and-data-dictionary# 🏥 Hospital Patient Records Analytics
### End-to-End Healthcare Analytics | Python · Power BI · DAX

![Python](https://img.shields.io/badge/Python-3.x-blue?logo=python&logoColor=white)
![Power BI](https://img.shields.io/badge/Power%20BI-Dashboard-F2C811?logo=powerbi&logoColor=black)
![Jupyter](https://img.shields.io/badge/Jupyter-Notebook-orange?logo=jupyter&logoColor=white)

---

## Overview

This project demonstrates a full analytics workflow applied to synthetic hospital patient records spanning **2011–2022** across Massachusetts healthcare facilities. Starting from ![raw, messy multi-table data](https://github.com/SriramSrinivasan1/Hospital-Patients-Records/tree/main/data-and-data-dictionary), the analysis covers data cleaning, feature engineering, cross-table integration, and stakeholder-ready dashboard delivery via Power BI.

The goal was to surface actionable KPIs around patient admissions, readmissions, procedure costs, and insurance coverage — insights that hospital operations and finance teams can act on directly.

---

## Dataset

Five interconnected synthetic datasets sourced from a Massachusetts hospital system (2011–2022):

| Table | Description |
|---|---|
| `Encounters` | Each patient visit, including type (inpatient, outpatient, surgery, etc.) and associated costs |
| `Patients` | Biographical details — name, address, DOB, marital status, ethnicity |
| `Procedures` | Medical procedures performed per encounter (e.g., MRI, depression screening) |
| `Organizations` | High-level hospital/facility metadata |
| `Payers` | Major U.S. health insurance provider records |

> **Note:** All data is synthetic and intended for educational and portfolio purposes only. No real patient information is used.

---

## Methodology

### 1. Data Cleaning & Standardization
- Standardized patient names using **regex** pattern matching to handle inconsistent formatting
- Corrected malformed 4-digit ZIP codes using Python **lambda** functions
- Imputed missing procedure codes with `'unknown'` or `0` to preserve record completeness

### 2. Feature Engineering
- Computed **Age** from date of birth relative to current date
- Constructed **Full Name** field via string concatenation
- Calculated **Procedure Duration** from start/stop timestamps
- Created **Admission Type Flag** classifying each encounter as a first-time visit or readmission

### 3. Cross-Table Integration
- Performed SQL-style **joins in Python** (pandas merge) across Encounters, Procedures, Patients, and Payers
- Identified procedures covered by insurance, segmented by provider

### 4. Power BI Dashboard Development
- Built table relationships using shared keys across all five datasets
- Created **Age Category** groups using DAX nested `IF` statements
- Designed interactive visuals covering readmission trends, procedure costs, average stay duration, and insurance breakdowns

---

## Key Findings

- **Readmission patterns** vary meaningfully by encounter type, with inpatient stays showing the highest readmission rates
- **Average stay duration** differs substantially across encounter categories, with surgical admissions averaging the longest stays
- **Insurance coverage gaps** exist across specific procedure types, with certain providers leaving a higher share of procedure costs uncovered
- **Age distribution** of patients skews toward older cohorts, consistent with higher utilization of inpatient and surgical services

---

## Tools & Technologies

| Tool | Purpose |
|---|---|
| Python (pandas, re) | Data ingestion, cleaning, transformation, feature engineering |
| Jupyter Notebook | Exploratory analysis and workflow documentation |
| Power BI | Interactive dashboard creation and stakeholder delivery |
| DAX | Calculated columns, measures, and age segmentation logic |

---

## Repository Contents

```
Hospital-Patients-Records/
├── Hospital Patients Records.ipynb   # Full Python analysis: cleaning, EDA, feature engineering
├── Hospital Dashboard.png            # Power BI dashboard (static screenshot)
├── hospital_analytics_portfolio.pdf  # Project summary document
└── README.md
```

---

## Dashboard Preview

![Hospital Dashboard](Hospital%20Dashboard.png)

---

## Challenges & How They Were Solved

**Understanding domain-specific data structures** — Encounters and Procedures represent distinct but related clinical concepts. Clarifying their relationship through domain research improved the depth and accuracy of the analysis.

**Multi-table integration** — Joining five tables with different granularities required careful key identification and deliberate merge strategies to avoid row duplication and data loss.

**KPI prioritization** — With many possible metrics available, the analysis was scoped by thinking from a hospital stakeholder perspective: what do operations leads and finance teams actually need to make decisions?

---

## Next Steps

- Apply **predictive modeling** (e.g., logistic regression or gradient boosting) to predict readmission risk at the patient level
- Enrich the dashboard with **drill-through pages** for individual facility or payer deep-dives
- Incorporate **time-series analysis** to surface seasonal admission trends across the 11-year dataset

---
