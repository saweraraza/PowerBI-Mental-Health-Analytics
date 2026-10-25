# PowerBI-Mental-Health-Analytics

# 📊 Mental Health & Workplace Analytics Power BI Dashboard

An interactive, multi-page Power BI dashboard analyzing workplace mental health trends, employee coping mechanisms, lifestyle factors, and treatment patterns across global respondents.

---

## 📸 Key Pages & Features

### 1. Overview & Geographic Distribution (Page 1)
- **Global Map Visual**: Interactive location mapping displaying response density across 30+ countries.
- **Top Metrics**: Response counts, global treatment seeking rates, and high-stress concentrations.
- **Occupational Breakdown**: Comparative bar charts mapping treatment rates across occupations.

### 2. Behavioral & Lifestyle Analytics (Page 2)
- **Core Behavioral KPIs**: Coping Struggle Rate (53.23%), Isolation Index (59.91%), and Work Interest Decline (68.66%).
- **Interactive Heatmap**: Cross-tabulation of Mood Swings vs. Habit Changes with high-contrast conditional formatting.
- **Chronological Time Indoors Chart**: Custom-sorted bar visual tracking stress progression relative to indoor isolation.

### 3. Executive Deep Dive & Segment Benchmarking (Page 3)
- **Executive Risk KPIs**: High Risk Rate (5.04%), Care Awareness Rate (40.72%), and Interview Openness Rate (28.23%).
- **Occupational Risk Matrix**: Granular cross-filtering identifying acute risk clusters (e.g., Student & Corporate segments).
- **100% Stacked Treatment Distribution**: Comparative ratio analysis of workplace care options vs. employee willingness to discuss mental health.

---

## 🛠️ Data Architecture & DAX Measures

### Data Engineering & Cleaning
- Handled `NaN` and uncategorized entries across demographic columns using Power Query.
- Custom index sorting applied to categorical duration attributes (`Days_Indoors`) for chronological visual ordering.

### Key DAX Formulas

```dax
// Coping Struggle Rate
Coping Struggle Rate = 
DIVIDE(
    CALCULATE(
        COUNTROWS('Mental Health Dataset'),
        'Mental Health Dataset'[Coping_Struggles] = "Yes"
    ),
    [Total Respondents],
    0
)

// High Risk Concentration Rate
High Risk Rate = 
DIVIDE(
    CALCULATE(
        COUNTROWS('Mental Health Dataset'),
        'Mental Health Dataset'[Growing_Stress] = "Yes" &&
        'Mental Health Dataset'[Coping_Struggles] = "Yes" &&
        'Mental Health Dataset'[Mood_Swings] = "High"
    ),
    [Total Respondents],
    0
)

// Care Options Awareness Rate
Care Awareness Rate = 
DIVIDE(
    CALCULATE(
        COUNTROWS('Mental Health Dataset'),
        'Mental Health Dataset'[care_options] = "Yes"
    ),
    [Total Respondents],
    0
)
