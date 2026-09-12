# 🛡️ Advanced Threat Incident Analytics & Security Visualization Framework

> **Intelligent Security. Actionable Insights. Safer Tomorrow.**

![SQL](https://img.shields.io/badge/SQL-MySQL-blue)
![Python](https://img.shields.io/badge/Python-Analysis-yellow)
![Excel](https://img.shields.io/badge/Excel-Advanced-green)
![PowerBI](https://img.shields.io/badge/Dashboard-PowerBI-orange)
![StarSchema](https://img.shields.io/badge/Data_Model-Star_Schema-purple)
![Level](https://img.shields.io/badge/Level-Intermediate--Advanced-green)
![Pages](https://img.shields.io/badge/Dashboard_Pages-4-orange)
![Records](https://img.shields.io/badge/Records-1%2C00%2C000-red)
![Status](https://img.shields.io/badge/Status-Completed-brightgreen)
![Internship](https://img.shields.io/badge/Infosys_Springboard-7.0-blue)
![GitHub last commit](https://img.shields.io/github/last-commit/mr-deepak-kp/ThreatAnalytics-Dashboard)
![GitHub repo size](https://img.shields.io/github/repo-size/mr-deepak-kp/ThreatAnalytics-Dashboard)
![GitHub stars](https://img.shields.io/github/stars/mr-deepak-kp/ThreatAnalytics-Dashboard?style=social)
![GitHub forks](https://img.shields.io/github/forks/mr-deepak-kp/ThreatAnalytics-Dashboard?style=social)
---

## 📌 Project Overview

The **Advanced Threat Incident Analytics & Security Visualization Framework** is an integrated security intelligence platform built as part of the **Infosys Springboard Virtual Internship 7.0 — Batch 2**.

This project consolidates cybersecurity incident data from multiple sources into a unified analytics environment — enabling security teams to detect threats, monitor trends, and make faster decisions through a **4-page interactive Power BI Dashboard**.

The solution combines **Star Schema data modeling**, **TSI Score calculation**, **geospatial threat mapping**, and **executive-level risk scorecards** into a single cohesive security analytics platform.

---

## 🎯 Problem Statement

Organizations responsible for public safety, enterprise security, and emergency management generate massive volumes of incident data daily. This data is often scattered across multiple systems, making it difficult for security teams to:

- Identify emerging threats on time
- Understand incident patterns across locations
- Evaluate response effectiveness against SLA targets
- Proactively mitigate future risks across industries

---

## ✅ Our Solution

A **4-page interactive Power BI Dashboard** that transforms raw cybersecurity data into actionable intelligence through:

- 📊 **Data Visualization** — KPI cards, bar charts, donut charts, and heatmaps
- ⭐ **Star Schema Modeling** — Organized data warehouse with fact and dimension tables
- ⚡ **TSI Score** — Custom Threat Severity Index formula
- 🗺️ **Geospatial Mapping** — Country-wise global threat hotspot map
- 📈 **Trend Analysis** — Monthly incident and TSI score patterns
- 🏆 **Security Risk Scorecard** — Industry × Severity breakdown table

---

## 🔗 Quick Links

| Resource | Link |
|----------|------|
| 📊 Power BI Dashboard (.pbix) | [View Dashboard](https://github.com/mr-deepak-kp/-Advanced-Threat-Incident-Analytics-Security-Visualization/tree/main/DashBoard) |
| 📄 Dashboard PDF Export | [View PDF](https://github.com/mr-deepak-kp/-Advanced-Threat-Incident-Analytics-Security-Visualization/blob/main/DashBoard/Threats_Analysis_dashboard.pdf) |
| 🐍 Python Notebook | [View Notebook](https://github.com/mr-deepak-kp/-Advanced-Threat-Incident-Analytics-Security-Visualization/blob/main/notebook/StarSchema.ipynb) |
| 📑 Presentation | [View Presentation](https://github.com/mr-deepak-kp/-Advanced-Threat-Incident-Analytics-Security-Visualization/blob/main/Final_ThreatAnalytics_Presentation.pdf) |

---

## 📁 Dataset Details

| Property | Value |
|----------|-------|
| Total Records | 1,00,000 |
| Total Columns | 15 |
| Time Period | 2023–2024 |
| Countries | 10 |
| Industries | 8 |
| Attack Types | 8 |

### 📋 Columns Used

| Column | Description |
|--------|-------------|
| `attack_type` | Type of attack — Phishing, DDoS, Ransomware etc. |
| `target_system` | System attacked — Cloud, IoT, Database etc. |
| `outcome` | Attack result — Success or Failure |
| `timestamp` | When the attack happened |
| `attack_severity` | Danger level 1–10 |
| `data_compromised_GB` | Data stolen in GB |
| `location` | Country of attack |
| `industry` | Sector attacked |
| `response_time_min` | Response time in minutes |
| `mitigation_method` | How attack was stopped |
| `security_tools_used` | Tool used — Firewall, MFA etc. |
| `user_role` | Who was targeted |
| `attack_duration_min` | How long the attack lasted |
| `attacker_ip` | IP address of attacker |
| `target_ip` | IP address of victim |

---

## ⭐ Star Schema Design

```
          DIM_TIME
             |
DIM_LOCATION ── FACT_INCIDENT ── DIM_THREAT
             |         |
       DIM_INDUSTRY  DIM_RESPONSE
```

| Table | Rows | Purpose |
|-------|------|---------|
| FACT_INCIDENT | 1,00,000 | Main incident data — central fact table |
| DIM_TIME | 1,00,000 | Time information for each incident |
| DIM_LOCATION | 10 | Country-level location details |
| DIM_INDUSTRY | 8 | Industry/sector details |
| DIM_THREAT | 8 | Attack type and severity classification |
| DIM_RESPONSE | 1,00,000 | Response time and mitigation details |

---

## ⚡ TSI Score Formula

```
TSI = (Attack Severity × 0.4) +
      (Data Compromised / 100 × 10 × 0.3) +
      (Response Time / 180 × 10 × 0.3)
```

| TSI Range | Level |
|-----------|-------|
| 0 – 3 | 🟢 Low |
| 3 – 5 | 🔵 Medium |
| 5 – 7 | 🟠 High |
| 7 – 10 | 🔴 Critical |

**Our Dataset TSI Score: 5.21 — HIGH THREAT ⚠️**

---

## 🛠️ Tech Stack

| Tool | Purpose |
|------|---------|
| ![Python](https://img.shields.io/badge/Python-ETL-yellow) | Data processing, Star Schema creation, TSI calculation |
| ![Pandas](https://img.shields.io/badge/Pandas-Analysis-lightblue) | Data cleaning, transformation, feature engineering |
| ![Power BI](https://img.shields.io/badge/PowerBI-Dashboard-orange) | 4-page interactive dashboard with navigation and slicers |
| ![Star Schema](https://img.shields.io/badge/Star_Schema-Data_Model-purple) | Fact + dimension table warehouse design |
| ![Jupyter](https://img.shields.io/badge/Jupyter-Notebook-orange) | Development and analysis environment |
| ![GitHub](https://img.shields.io/badge/GitHub-Version_Control-black) | Repository and version control |

---

## 📦 Libraries Used

```python
import pandas as pd              # Data manipulation
import numpy as np               # Numerical operations
import matplotlib.pyplot as plt  # Basic charts
import seaborn as sns            # Statistical visualization
import plotly                    # Interactive charts
```

---

## 📊 Dashboard Pages — 4 Pages

| Page | Title | Milestone | Key Visuals |
|------|-------|-----------|-------------|
| **P1** | 🏠 Overview | Milestone 1 — Weeks 1–2 | Total Incidents · Avg TSI · Avg Response · Data Compromised · Attack Type Bar · Industry Bar · Attack Outcome Donut · Severity Donut |
| **P2** | 🎯 Threat Intelligence | Milestone 2 — Weeks 3–4 | TSI Gauge · Monthly Trend · Incident Categories Donut · Security Tools Bar · Anomaly Alert |
| **P3** | 🗺️ Geospatial | Milestone 3 — Weeks 5–6 | Global Hotspot Map · Avg Response by Country Bar · Location × Industry Matrix Table |
| **P4** | 📊 Executive Summary | Milestone 4 — Weeks 7–8 | Security Risk Scorecard · Platform Risk Gauge · Industry Risk Bar · TSI Trend Line · SLA Summary |

---

## 🖥️ Dashboard Preview

### Page 1 — Overview
![Overview Dashboard](https://github.com/mr-deepak-kp/-Advanced-Threat-Incident-Analytics-Security-Visualization/blob/main/Dashboard_screenshort/page1_overview.png)

> 📌 **KPI Cards:** Total Incidents (1,00,000) · Avg TSI Score (5.21) · Avg Response Time (90 Min) · Data Compromised (5.01M GB)

---

### Page 2 — Threat Intelligence
![Threat Intelligence Dashboard](https://github.com/mr-deepak-kp/-Advanced-Threat-Incident-Analytics-Security-Visualization/blob/main/Dashboard_screenshort/page2_threat.png)

> 📌 **KPI Cards:** Overall TSI Score (5.21) · Critical Incidents (25,024) · High Severity Count (5.50) · Avg Severity Score (7.00)

---

### Page 3 — Geospatial
![Geospatial Dashboard](https://github.com/mr-deepak-kp/-Advanced-Threat-Incident-Analytics-Security-Visualization/blob/main/Dashboard_screenshort/page3_geospatial.png)

> 📌 **KPI Cards:** Most Attacked Country (India) · Avg Response Time (90.78 Min) · Total Locations (10) · Max Response Time (180 Min)

---

### Page 4 — Executive Summary
![Executive Summary Dashboard](https://github.com/mr-deepak-kp/-Advanced-Threat-Incident-Analytics-Security-Visualization/blob/main/Dashboard_screenshort/page4_executive.png)

> 📌 **KPI Cards:** Overall TSI Score (5.21) · SLA Compliance (33.3%) · Attacks Resolved (25,024) · Total Data at Risk (5.01M GB) · Critical Attacks (12,499) · Avg Attack Duration (151.8 Min)

---

## 🧠 Skills Demonstrated

| Skill | Description |
|-------|-------------|
| **Star Schema Design** | Fact + 5 dimension tables — modeled in Python and loaded into Power BI |
| **TSI Score Formula** | Custom weighted index combining severity, data loss, and response time |
| **Power BI Dashboard** | 4-page navigation, slicers (Industry, Month, Location), KPI cards |
| **Geospatial Mapping** | Bing Maps integration — global country-level threat hotspot visualization |
| **ETL Pipeline** | Python Pandas — raw CSV → cleaned fact and dimension CSVs |
| **Anomaly Detection** | Monthly spike identification and alert panels in Power BI |
| **Security Risk Scorecard** | Industry × Severity × TSI Score matrix table |
| **EDA** | Univariate and bivariate analysis of 1,00,000 cybersecurity records |
| **Python** | pandas, numpy, matplotlib, seaborn, plotly |
| **Documentation** | README, milestone reports, presentation deck |

---

## 🔑 Key Findings

| Metric | Value |
|--------|-------|
| 🚨 Total Incidents | 1,00,000 |
| ⚡ Avg TSI Score | 5.21 (HIGH) |
| ⏱️ Avg Response Time | 90 Min (Target: 60 Min) |
| 💾 Data Compromised | 5.01 Million GB |
| ✅ Attacks Resolved | 25,024 (50%) |
| ❌ Attacks Still Getting Through | 50% |
| 📋 SLA Compliance | 33.3% |
| 🔴 Critical Attacks (Ransomware) | 12,499 |
| ⏳ Avg Attack Duration | 151.8 Min |
| 🌐 Total Countries Attacked | 10 |

### ⚠️ Critical Findings

- **Brute Force** is the most common attack with **12,605 incidents** — closely followed by DDoS (12,557) and Zero-Day Exploit (12,555)
- **Government sector** is the most targeted industry with **12,645 incidents**
- **India** has the highest average response time at **91.3 minutes** — 31 minutes above the 60-minute SLA target
- **March** recorded the highest monthly incidents at **8.6K** — January, August, and December also show anomaly spikes
- **Endpoint Detection** is the most used security tool across all incidents
- **50% of attacks** were successfully stopped — 50% still getting through, requiring urgent improvement
- **All 8 attack types** show nearly equal distribution at ~12.5% each — no single attack type dominates
- **SLA Compliance is only 33.3%** — well below the 60-minute response target benchmark

---

## 📋 Milestone Summary

### ✅ Milestone 1 — Data Integration (Weeks 1–2)
- Dataset collected (1,00,000 records, 15 columns) and cleaned
- Star Schema designed and implemented (1 fact + 5 dimension tables)
- ETL pipeline created using Python Pandas
- TSI Score calculated and applied to all 1 lakh records

### ✅ Milestone 2 — Threat Intelligence (Weeks 3–4)
- TSI Gauge chart built (Current: 5.21 vs Target: ≤ 5.0)
- Monthly incident trend analysis completed (March highest at 8.6K)
- All 8 incident categories classified and visualized
- Security tools usage ranked (Endpoint Detection leads at 145,231)

### ✅ Milestone 3 — Geospatial Analytics (Weeks 5–6)
- Global threat hotspot map created using Power BI Bing Maps
- Country-wise average response time bar chart built
- Location × Industry incident matrix table created (10 countries × 8 industries)

### ✅ Milestone 4 — Executive Analytics (Weeks 7–8)
- Security Risk Scorecard built (Industry × Severity × TSI Score)
- Industry Risk Analysis bar chart completed
- Platform Risk Gauge implemented (TSI: 5.21 vs Target: ≤ 5.0)
- Executive command center dashboard with anomaly alert panel built

---

## 🗂️ Project Structure

```
ThreatAnalytics-Dashboard/
│
├── 📊 Dashboard/
│   ├── ThreatAnalytics_Dashboard.pbix       # Power BI dashboard file
│   └── ThreatAnalytics_Dashboard.pdf        # PDF export of all 4 pages
│
├── 📁 Dataset/
│   ├── threat_incident_data.csv   # Original raw dataset
│   ├── fact_incident.csv                    # Fact table
│   ├── dim_time.csv                         # Time dimension
│   ├── dim_location.csv                     # Location dimension
│   ├── dim_industry.csv                     # Industry dimension
│   ├── dim_threat.csv                       # Threat dimension
│   └── dim_response.csv                     # Response dimension
│
├── 🐍 Notebooks/
│   └── StarSchema.ipynb                     # ETL + Star Schema creation notebook
│
├── 🖼️ Screenshots/
│   ├── page1_overview.png                   # Page 1 — Overview
│   ├── page2_threat.png                     # Page 2 — Threat Intelligence
│   ├── page3_geospatial.png                 # Page 3 — Geospatial
│   └── page4_executive.png                  # Page 4 — Executive Summary
│
├── 📑 Presentation.pptx                     # Project presentation deck
└── 📝 README.md                             # Project documentation
```

---

## 🚀 How to Run the Project

**1. Clone the Repository**

```bash
git clone https://github.com/mr-deepak-kp/ThreatAnalytics-Dashboard.git
cd ThreatAnalytics-Dashboard
```

**2. Install Python Libraries**

```bash
pip install pandas numpy matplotlib seaborn plotly
```

**3. Run the Jupyter Notebook**

```bash
jupyter notebook Notebooks/StarSchema.ipynb
```

> This generates all 6 CSV files (fact + 5 dimensions) from the raw dataset.

**4. Open the Power BI Dashboard**

```
Open Dashboard/ThreatAnalytics_Dashboard.pbix
in Power BI Desktop
```

---

## 📑 Project Deliverables

| # | Deliverable | Format | Status |
|---|-------------|--------|--------|
| 1 | Raw Cybersecurity Dataset | `.csv` | ✅ Complete |
| 2 | Star Schema (Fact + 5 Dimensions) | `.csv` | ✅ Complete |
| 3 | ETL & Star Schema Notebook | `.ipynb` | ✅ Complete |
| 4 | Power BI Dashboard — 4 Pages | `.pbix` | ✅ Complete |
| 5 | Dashboard PDF Export | `.pdf` | ✅ Complete |
| 6 | Dashboard Screenshots × 4 | `.png` | ✅ Complete |
| 7 | Project Presentation | `.pptx` | ✅ Complete |
| 8 | GitHub Repository | Public | ✅ Complete |

---

## 👨‍💻 About

| Field | Details |
|-------|---------|
| **Internship** | Infosys Springboard Virtual Internship 7.0 |
| **Batch** | Batch 2 |
| **Domain** | Data Visualization & Security Analytics |
| **Duration** | 8 Weeks — 4 Milestones |

---

## 🔮 Future Improvements

- [ ] Publish Power BI dashboard to Power BI Service for live access
- [ ] Build real-time threat alert system using streaming data
- [ ] Add ML-based anomaly detection for automated threat classification
- [ ] Integrate SIEM log data for deeper incident correlation
- [ ] Add predictive response time modeling using regression
- [ ] Expand geospatial analysis to city-level granularity
- [ ] Build automated weekly security KPI report using Python

---

## 🤝 Connect With Me

[![GitHub](https://img.shields.io/badge/GitHub-mr--deepak--kp-181717?style=for-the-badge&logo=github)](https://github.com/mr-deepak-kp)
[![LinkedIn](https://img.shields.io/badge/LinkedIn-deepak--kumar--prasad-0A66C2?style=for-the-badge&logo=linkedin)](https://www.linkedin.com/in/deepak-kumar-prasad/)

---

<div align="center">

**🛡️ Advanced Threat Incident Analytics & Security Visualization Framework**

*Intelligent Security. Actionable Insights. Safer Tomorrow.*

Made with ❤️ for Infosys Springboard Virtual Internship 7.0

</div>

---

*Threat Incident Analytics · Python · Power BI · Star Schema · ETL · Security Intelligence · Infosys Springboard 7.0*
