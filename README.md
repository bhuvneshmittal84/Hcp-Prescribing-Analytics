<div align="center">

# 💊 HCP Prescribing Potential \& Visit Prioritization

### *A Data-Driven Framework for Optimizing Pharmaceutical Sales Rep Visits*

!\[Python](https://img.shields.io/badge/Python-3.10+-3776AB?style=for-the-badge\&logo=python\&logoColor=white)
!\[Pandas](https://img.shields.io/badge/Pandas-Data\_Wrangling-150458?style=for-the-badge\&logo=pandas\&logoColor=white)
!\[scikit-learn](https://img.shields.io/badge/scikit--learn-ML\_Models-F7931E?style=for-the-badge\&logo=scikit-learn\&logoColor=white)
!\[Power BI](https://img.shields.io/badge/Power\_BI-Dashboard-F2C811?style=for-the-badge\&logo=powerbi\&logoColor=black)

\---

**2,000 HCPs** · **8 Quarters of Data** · **4 Specialties × 4 Regions** · **+2.6 % Projected Rx Uplift**

</div>

\---

## 📌 Table of Contents

* [Problem Statement](#-problem-statement)
* [Solution Overview](#-solution-overview)
* [Dashboard Walkthrough](#-dashboard-walkthrough)

  * [Page 1 — Executive Summary](#page-1--executive-summary)
  * [Page 2 — Segmentation](#page-2--segmentation)
  * [Page 3 — Predictive Analytics](#page-3--predictive-analytics)
  * [Page 4 — Business Impact \& Executive Dashboard](#page-4--business-impact--executive-dashboard)
* [Key Findings](#-key-findings)
* [Tech Stack \& Methodology](#-tech-stack--methodology)
* [Project Structure](#-project-structure)
* [How to Reproduce](#-how-to-reproduce)

\---

## 🎯 Problem Statement

Pharmaceutical field teams face a recurring challenge: **how to allocate a finite number of sales rep visits across thousands of Healthcare Providers (HCPs) to maximise prescription growth.**

Most allocation strategies rely on gut feel or historical volume alone — ignoring predictive signals like growth probability, specialty-specific behaviour, and diminishing returns from over-visiting.

**This project answers one question:**

> \*Given a fixed budget of 6,000 visits per quarter, which HCPs should receive more visits — and which fewer — to maximise incremental prescriptions?\*

\---

## 🧠 Solution Overview

The project follows a **10-phase analytics pipeline** that moves from raw data → insights → optimised actions:

```
Raw Panel Data
    │
    ▼
┌───────────────────────┐
│  EDA \& Feature Eng.   │  Phases 1-3
└──────────┬────────────┘
           ▼
┌───────────────────────┐
│  HCP Segmentation     │  Phase 4  (K-Means → 4 segments)
└──────────┬────────────┘
           ▼
┌───────────────────────┐
│  Predictive Modeling   │  Phases 5-7  (Gradient Boosting Regressor + Classifier)
└──────────┬────────────┘
           ▼
┌───────────────────────┐
│  Visit Optimization    │  Phases 8-9  (Constrained allocation)
└──────────┬────────────┘
           ▼
┌───────────────────────┐
│  Dashboard \& Delivery  │  Phase 10  (Power BI, 4 pages)
└───────────────────────┘
```

\---

## 📊 Dashboard Walkthrough

> The interactive Power BI dashboard distils the entire pipeline into \*\*4 pages\*\*, each targeting a different stakeholder question. Region and Specialty slicers are available on every page.

\---

### Page 1 — Executive Summary

<p align="center">
  <img src="Hcp%20ss/H_1.png" alt="Executive Summary" width="900"/>
</p>

The landing page answers: ***"What's the overall opportunity, and is it worth investing in optimised visit allocation?"***

|KPI Card|Value|What It Means|
|-|-|-|
|**Total HCPs**|2,000|Universe of providers in the panel|
|**Current Quarter Rx**|6K|Baseline prescriptions in Q8|
|**Projected Next Qtr Rx**|7236|Model-predicted Rx under the optimised plan|
|**Expected Rx Uplift**|+1,236 (20.6 %)|Incremental scripts from reallocation alone|
|**Avg Opportunity Score**|34.11 / 100|Mean composite score across all HCPs|

**Charts on this page:**

* **Opportunity Score Distribution** — Histogram showing the majority of HCPs cluster in the 20-40 range, with a long right tail of high-potential providers.
* **Avg Opportunity Score by Region** — Scores are remarkably consistent (33–35) across North, South, East, and West — confirming that provider-level characteristics drive prescribing potential more than geography.
* **Quarterly Prescription Trend** — Actual vs. Predicted Rx from Q2 → Q8. The Q8 data point is the true holdout (out-of-sample), while Q2–Q7 are in-sample fit.

**Actionable Insight Cards:**

* 🔄 **Visit Optimization** — Reallocate visits toward high-opportunity HCPs without increasing total visit budget.
* 📈 **Growth Focus** — Prioritise high-opportunity providers next quarter for maximum field-force ROI.
* 🌍 **Regional Insight** — Consistent scores across regions suggest provider-level factors matter more than geography.
* 💰 **Business Impact** — Projected +2.6 % Rx uplift with zero net increase in total sales visits.

\---

### Page 2 — Segmentation

<p align="center">
  <img src="Hcp%20ss/H_2.png" alt="Segmentation" width="900"/>
</p>

This page answers: ***"Who are our HCPs, and how do they cluster?"***

Using **K-Means clustering**, every HCP is assigned to one of four strategic segments:

|Segment|Count|% of Panel|Profile|
|-|-:|-:|-|
|🟢 **Rising Stars**|290|14.5 %|High engagement, moderate Rx — near visit-saturation plateau|
|🔵 **Core Advocates**|414|20.7 %|Highest volume \& Rx rate — protect and maintain|
|🟡 **Maintain**|627|31.4 %|Veteran providers, low engagement — **highest marginal ROI**|
|🔴 **Low Priority**|669|33.5 %|Early-career, lowest Rx — but strong uplift potential per visit|

**Charts on this page:**

* **HCP Segment Distribution** — Donut chart showing the proportion of each segment.
* **Segment Performance Comparison** — Dual-axis line comparing Avg Opportunity Score vs. Avg Growth Probability across segments.
* **Opportunity vs Growth Matrix** — Scatter plot (X = Opportunity Score, Y = Growth Probability %) colored by segment, revealing the strategic positioning of each cluster.
* **Priority HCP Ranking** — Sortable table listing top HCPs with their Region, Specialty, Opportunity Score, Growth Probability, and Current Visits.

**Key Insight:** Maintain and Low Priority segments show the **highest marginal ROI** per additional visit — they're under-visited relative to their potential.

\---

### Page 3 — Predictive Analytics

<p align="center">
  <img src="Hcp%20ss/H_3.png" alt="Predictive Analytics" width="900"/>
</p>

This page answers: ***"How accurate are our predictions, and where should we invest next?"***

|Model Metric|Value|
|-|-|
|Regression R² (Q8 Holdout)|**0.991**|
|RMSE (Q8 Holdout)|**6.75**|
|Classification AUC|**0.874**|
|Classification Recall|**0.857**|

> R² of 0.991 is genuine — driven by `rx\_prev\_q` being a strong autoregressive predictor. Prescribing behaviour is highly persistent quarter-to-quarter, which makes this realistic, not a data leak.

**Charts on this page:**

* **Current Quarter Visits by Region** — Bar chart comparing visit volume across South, East, West, and North.
* **Additional Visits Needed by Region** — Diverging bar chart showing which regions need more (+) or fewer (−) visits under the optimised plan. North shows the largest need for additional visits.
* **HCP Distribution by Visit Change** — Histogram of recommended visit changes per HCP, showing most providers see small adjustments (−2 to +5 visits).
* **Prescription Uplift vs Additional Visits** — Scatter plot (colored by segment) showing the relationship between visit changes and projected Rx uplift.
* **Prescription Uplift Contribution** — Waterfall chart breaking down how each segment contributes to the total projected uplift.

\---

### Page 4 — Business Impact \& Executive Dashboard

<p align="center">
  <img src="Hcp%20ss/H_4.png" alt="Business Impact and Executive Dashboard" width="900"/>
</p>

This page answers: ***"What's the concrete ROI, and who are the top providers to act on?"***

|KPI|Value|
|-|-|
|Total Current Visits|6,000|
|Total Optimised Visits|6,000|
|Net Additional Visits|**−25** (reallocation, not expansion)|
|Projected Prescription Increase|**3.01 %**|
|High Priority HCPs|**400**|

> Unlike typical analyses that request \*more\* reps, this optimisation \*\*reallocates within the existing 6,000-visit budget\*\* — a more realistic, defensible recommendation.

**Charts on this page:**

* **Actual vs Predicted Prescription Trend** — Full quarterly trend (Q3–Q6) showing model accuracy over time; the prediction band closely tracks actuals.
* **Projected Rx Uplift by Region** — Horizontal bar chart confirming all four regions benefit from the optimised allocation, with North and West showing the largest uplift.
* **Projected Prescription Uplift by Specialty** — Treemap showing GP and Oncology capture the largest share of projected uplift, followed by Endocrinology and Cardiology.
* **Top 10 High Impact Providers** — Table listing the highest-value HCPs with Opportunity Score, Projected Rx Uplift, and Recommended Visits. These are the "must-win" accounts.

\---

## 🔑 Key Findings

|#|Finding|Business Implication|
|:-:|-|-|
|1|**Maintain \& Low Priority segments have the highest marginal ROI** per additional visit (priority scores of 44.7 and 43.9).|Shift visits *toward* these under-served segments.|
|2|**Rising Stars are near visit-saturation** (avg 6.33 visits/quarter) — further increases yield diminishing returns.|Protect current engagement; don't over-invest.|
|3|**Core Advocates are high-value but low-growth** — already the top prescribers.|Maintain relationship; reallocate excess visits elsewhere.|
|4|**Region is not a primary driver** of prescribing potential — all regions score 33–35 on opportunity.|Don't over-rotate strategy by geography; focus on provider-level factors.|
|5|The optimised plan delivers a **+2.6 % Rx uplift with zero net increase** in total visit capacity.|Efficiency gain — no additional headcount required.|

\---

## ⚙️ Tech Stack \& Methodology

|Layer|Technology|Purpose|
|-|-|-|
|**Data Processing**|Python · Pandas · NumPy|Cleaning, feature engineering, aggregation|
|**Machine Learning**|scikit-learn (Gradient Boosting)|Rx prediction (regression) + growth classification|
|**Segmentation**|K-Means Clustering|HCP behavioral segmentation into 4 groups|
|**Optimisation**|Constrained Allocation (Python)|Visit reallocation within fixed budget|
|**Visualisation**|Power BI (DAX Measures)|4-page interactive executive dashboard|
|**Version Control**|Git \& GitHub|Repository management|

### Optimisation Constraints

```
✅ Max 6 visits per HCP per quarter
✅ Min 2 visits for top-quartile priority HCPs
✅ Min 1 visit for every HCP (relationship maintenance floor)
✅ Total budget: 6,000 visits/quarter (hard cap)
✅ Objective: Maximise visit\_priority\_score-weighted visits (marginal impact)
```

\---

## 📂 Project Structure

```
hcp-prescribing-analytics/
│
├── 📄 README.md                          ← You are here
├── 📄 requirements.txt                   ← Python dependencies
├── 📄 .gitignore
│
├── 📁 files/
│   ├── 10\_dashboard\_prep.py              ← Phase 10: Data prep for Power BI
│   ├── DAX\_measures.md                   ← All DAX measures for the dashboard
│   └── dashboard\_build\_guide.md          ← Page-by-page build instructions
│
├── 📁 data/
│   └── processed/                        ← Pipeline outputs (CSV)
│       ├── final\_hcp\_dashboard\_data.csv  ← 2,000 rows, one per HCP
│       └── quarterly\_trend.csv           ← Q2-Q8 actual vs predicted Rx
│
├── 📁 powerbi/
│   └── HCP Dashboard.pbix               ← Power BI dashboard file
│
└── 📁 Hcp ss/                            ← Dashboard screenshots
    ├── H\_1.png                           ← Page 1: Executive Summary
    ├── H\_2.png                           ← Page 2: Segmentation
    ├── H\_3.png                           ← Page 3: Predictive Analytics
    └── H\_4.png                           ← Page 4: Business Impact
```

\---

## 🚀 How to Reproduce

```bash
# 1. Clone the repository
git clone https://github.com/<your-username>/hcp-prescribing-analytics.git
cd hcp-prescribing-analytics

# 2. Create a virtual environment
python -m venv .venv
source .venv/bin/activate        # Linux/Mac
.venv\\Scripts\\activate           # Windows

# 3. Install dependencies
pip install -r requirements.txt

# 4. Run the dashboard prep script
cd files
python 10\_dashboard\_prep.py

# 5. Open the Power BI dashboard
# Open powerbi/HCP Dashboard.pbix in Power BI Desktop
```

\---

<div align="center">

### Built with ❤️ for Data-Driven Decision Making

*If you found this project insightful, feel free to ⭐ the repo!*

</div>

