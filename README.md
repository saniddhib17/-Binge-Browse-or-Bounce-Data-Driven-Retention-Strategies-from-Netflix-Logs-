## Binge Browse or Bounce-Data-Driven-Retention-Strategies from Netflix-Logs
## Overview
This project delivers a full data analytics pipeline for Netflix-style user engagement, journey mapping, funnel analysis, and churn prediction. By combining clickstream, viewing, search, device, and profile logs, it extracts actionable insights into engagement, conversion, and retention drivers across devices and behavioral segments.

---

## Tech Stack

| Category          | Tools / Libraries             |
|-------------------|------------------------------|
| Data Processing   | pandas, numpy                |
| Visualization     | matplotlib, seaborn          |
| Modeling          | scikit-learn, xgboost, prophet|
| Notebook          | Google Colab, Jupyter        |

---

## Datasets

| Dataset           | Type        | File Name               | Key Columns                     |
|-------------------|-------------|-------------------------|----------------------------------|
| Viewing Activity  | Sessions    | All_ViewingActivity.csv | Start Time, Duration, Device     |
| Clickstream       | Navigation  | All_Clickstream.csv     | Navigation Level, Source, Time   |
| Search History    | Events      | All_SearchHistory.csv   | Query, Action, Country, Time     |
| Devices           | Meta        | All_Devices.csv         | Device Type, Activation Dates    |
| Profiles          | User Master | All_Profiles.csv        | Maturity, Language, Profile Meta |

---

## Project Objectives

- **Engagement Profiling**: Identify binge, casual, and power users through session gap and frequency analysis.
- **Cohort and Funnel Analytics**: Build user funnels (profilesGate → browseTitles → playback → signupPrompt) and measure conversion/drop-off by device or behavioral group.
- **A/B and Segmentation**: Compare engagement and churn across source, device, and behavioral cohorts.
- **Churn Prediction**: Engineer features (recency, frequency, engagement, device usage) and train interpretable ML models to predict churn and inform retention strategies.

---
## Key Quantified Insights

- **User Engagement & Watch Time**
    - Top user: **User 4** watched **5,221,435 seconds** (≈1,450 hours) over **5,239 sessions** (88% binge rate).
    - Watch time per user ranges from **75,170 sec** to **1,659,712 sec** among active users.
    - **Binge sessions** (gap <2h): **82.6%** of all sessions, highlighting high platform stickiness.
    - Users inactive for >200 days are at greatest churn risk.

- **Device & Platform Usage**
    - Users interact via up to **12 device types** (User 8); most active users are highly device-diverse.
    - **Mobile iOS (Type 0)** and **Android (Type 1)** account for the majority of sessions (~5,000 & 2,500 respectively).
    - Device diversity is a key marker of high engagement (correlation up to **r=0.69** with search frequency).
    - **India** is the top market by device and search count; AE (UAE) skews toward Device Type 0.

- **Clickstream & Search Behavior**
    - Most active users performed up to **3,553 clicks** (User 5), traversing as many as **21 unique navigation levels**.
    - Search queries per user range from **6** to **1,090**; User 8 performed **172 unique queries**.
    - **Search-to-play conversion:** **64.4%** of search events led to playback within ±30min.
    - **Top search actions:** 'select' (**71%**), 'play' (**27%**), 'add to list' (**1%**).

- **Funnel & Cohort Analysis**
    - **Funnel conversion (profilesGate → playback):**
        - **Source A:** 87.5% (7/8 users)
        - **Source B:** 100% (5/5 users)
    - **Biggest drop-off:** Before 'signupPrompt' step—only **25%** (2/8) of Source A reach signup; Source B has 0%.
    - **Device drop-off:** Device Types 5 and 0 lose 20–25% at movieDetails→playback; nearly all device types lose nearly 100% at signup.

- **Retention & Churn**
    - **Retention rate:** 77.8% (Group A), 80% (Group B); small sample, but consistent.
    - **Churn risk is highest among users with low binge rate, long recency (e.g., User 1: 419 days since last session).**
    - **Power users:** High device diversity, frequent searches, deep navigation—strongly correlated with retention.

- **Forecasting & Trend Analysis**
    - **Monthly watch time** peaked at **~1,030,000 seconds/month**, but fell to **178,136 sec** in June 2023 (an **80% drop**).
    - **Time-series forecast** shows further decline unless retention interventions are made.

- **Content Discovery**
    - The same **top 10 titles** ("Night Drive", "Doctor (Tamil)", etc.) dominate across all major device types.
    - Device "Other" users watch more niche titles, with no dominant show per device.
    - **No title exceeds 4 unique viewers per device group**—high audience fragmentation.

---

## Example Results Table

| Segment          | Sessions | Binge Rate | Churn/Recency | Device Types | Search-to-Play | Top Title(s)            |
|------------------|----------|------------|---------------|--------------|----------------|-------------------------|
| User 4           | 5,239    | 88%        | 264 days      | 10           | 64.4%          | Night Drive, Kurup      |
| User 8           | 1,932    | 81%        | 1 day         | 12           | 64.4%          | Doctor (Tamil)          |
| Device Type 0    | ~5,000   | –          | –             | –            | –              | Never Have I Ever S1    |
| Device Type 1    | ~2,500   | –          | –             | –            | –              | Breaking Bad S3         |
| India (IN)       | –        | –          | –             | 7+           | –              | High engagement, search |

---

## Key Findings

- **Heavy users (sessions, device, clicks, searches) drive most platform engagement.**
- **Recency (low days since last session)** is the strongest retention predictor.
- **Device and search diversity** are key engagement signals (r = 0.69 with searches).
- **Most session starts peak between 4 AM–6 PM; Sundays at 8 AM highest.**
- **Search-to-play conversion is strong (64.4%) but add-to-list is rarely used (1%).**
- **Major drop-off occurs at final signup step for all device types.**
- **Content popularity is device-agnostic for mainstream titles; niche content dominates rare devices.**

## Key Features

- **Sessionization**: Event sessionization and gap analysis for binge/casual detection.
- **Funnel & Drop-Off Analysis**: Stepwise funnel visualizations and drop-off measurement by cohort.
- **Multi-Event Join**: Integrate search, click, and viewing logs for end-to-end journey analysis.
- **Churn & LTV Modeling**: ML pipeline for churn/LTV with explainable features.
- **Actionable Insights**: Power-user detection, churn risk, and UX recommendations.

---

## Research Questions

- Where are the biggest drop-offs in the onboarding-to-playback journey?
- How do device, source, and behavioral segments impact engagement and churn?
- Can we identify high-churn-risk users before inactivity?
- How do search and navigation events relate to engagement?

---

## Visual Analytics

- **Session gap histogram:** Most sessions <17 min, but long tail of binge sessions up to 2 hours.
- **Heatmaps:** Session and search activity cluster on weekends and evenings.
- **Bubble plot:** Largest bubbles = highest engagement (User 4, User 8).
- **Funnel and drop-off plots:** Identify critical conversion and churn points by segment.

---

## Recommendations

- **Focus retention & reactivation on users with rising recency and lower binge rates.**
- **Optimize UX for Device Type 0/1 (iOS/Android) and India/AE markets.**
- **Improve search-to-play matching and promote add-to-list feature.**
- **Prioritize funnel optimization at signup; address device-specific drop-off.**
- **Personalize discovery for power users; experiment with cohort-based interventions.**

---

## How to Run

1. **Open `NETFLIX_WATCHLOG_.ipynb` in Colab/Jupyter.**
2. **Upload all five datasets** or mount Google Drive.
3. **Run each notebook cell** in sequence for cleaning, feature engineering, sessionization, funnel, cohort, and churn modeling.
4. **Export visuals for Power BI/Tableau** or as PDF for reports.

---

## Future Work

- Real-time analytics dashboard
- Genre/episode-level engagement and uplift analysis
- A/B testing for feature changes and retention interventions
- Deploy predictive churn models in production

---

## Acknowledgments

This project applies advanced analytics and BI best practices for streaming platforms, with direct portfolio application and actionable insights.

---





---


