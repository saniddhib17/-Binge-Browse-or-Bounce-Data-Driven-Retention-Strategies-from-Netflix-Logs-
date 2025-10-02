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
| BI/Dashboard      | Power BI, Tableau (optional) |
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

## How to Run

1. **Open the notebook** (`NETFLIX_WATCHLOG_.ipynb`) in Google Colab or Jupyter.
2. **Upload all five datasets** to your working directory or mount your Google Drive.
3. **Run each notebook cell in order**:
    - Data cleaning & feature engineering
    - Session and funnel analysis
    - Engagement & churn modeling
    - Visualization/dashboard cells
4. **Visualize** results (charts and tables ready for BI export).

---

## Example Results

| Segment   | Stepwise Funnel Drop-off | Binge User % | Churn Rate |
|-----------|-------------------------|--------------|------------|
| Device 1  | 12.5% (browse→movie)    | 61%          | 35%        |
| Device 3  | 20.0% (browse→movie)    | 80%          | 24%        |
| Source A  | 0.0% (browse→movie)     | 71%          | 28%        |



---

## Key Insights

- Conversion to playback is highest among TV users; drop-off spikes for mobile at details.
- Binge users (short session gaps) have higher LTV and lower churn.
- High-risk churn profiles show low device diversity and lower search-to-play conversion.
- UX recommendations: Simplify details→play flow, target mobile/standard users, personalize by binge pattern.

---

## Future Work

- Add recommender evaluation and retention uplift modeling.
- Expand to real-time dashboards or streaming data.
- Integrate content/genre-level analysis if available.
