# Predicting Road Accident Severity Using Location, Time, and Weather Factors

## Business Analytics – Individual Case Study

**Name:** Kanish Kumaran M  
**Roll No:** CB.SC.U4CSE23424  
**Class:** CSE E  
**Domain:** Transportation / Public Safety

## 1. Problem Statement

Road accidents vary in severity depending on contextual factors such as location, time of occurrence, weather, road environment, vehicle involvement and collision characteristics. This case study uses publicly accessible accident-reporting webpages to explore these factors and develop a preliminary classification workflow for accident severity.

## 2. Objectives

1. Collect publicly accessible road-accident reports through web scraping and document the collection procedure.
2. Prepare and explore the collected information to identify location, time, weather, vehicle and collision patterns associated with reported severity.
3. Implement and compare classification models and translate the findings into practical road-safety and resource-planning insights.

## 3. Data Collection

Data were collected from publicly accessible Google News results and linked news articles using the Apify platform. Accident-focused queries were used, and article URLs and article bodies were collected where available.

Collection summary:

- Initial combined raw rows: **1,000**
- Unique URLs in the initial combined file: **787**
- Current working article corpus used for exploratory analysis: **848 records**
- Pilot modeling dataset: **290 records**

The article corpus is an intermediate source corpus. Multiple news articles can describe the same accident, so article count is not interpreted as the number of unique accidents.

## 4. Important Variables

| Variable | Meaning | Role |
|---|---|---|
| article_title | Headline of the collected report | Source/text |
| published_date | Publication date | Temporal reference |
| state | State/location evidence | Predictor |
| time_of_day | Morning/afternoon/evening/night evidence | Predictor |
| rain_or_wet | Explicit rain or wet-road evidence | Predictor |
| fog | Explicit fog/mist evidence | Predictor |
| highway | Explicit highway/expressway evidence | Predictor |
| bus / lorry / car / two-wheeler | Reported vehicle involvement | Predictor |
| head_on / rear_end / collision | Reported collision evidence | Predictor |
| severity | Fatal / Serious / Minor/Reported Injury | Target |

## 5. Analytics Methods

The saved pilot experiment uses:

- Stratified 80:20 train/test split with `random_state=42`
- One-hot encoding for categorical variables
- Logistic Regression
- Decision Tree
- Random Forest
- Gradient Boosting
- Accuracy
- Macro Precision
- Macro Recall
- Macro F1
- Confusion matrix

Deaths and injuries were excluded from predictors to avoid target leakage.

## 6. Pilot Results

| Model | Accuracy | Macro Precision | Macro Recall | Macro F1 |
|---|---:|---:|---:|---:|
| Logistic Regression | 0.362 | 0.362 | 0.350 | 0.345 |
| Decision Tree | **0.414** | **0.425** | **0.415** | **0.391** |
| Random Forest | 0.397 | 0.375 | 0.378 | 0.375 |
| Gradient Boosting | 0.397 | 0.282 | 0.321 | 0.298 |

The Decision Tree produced the highest macro F1 in this pilot experiment. These are preliminary article-level pilot metrics, not final accident-event predictive performance.

## 7. Data and Model Limitation

The source is a news-article corpus rather than a fully validated one-row-per-accident database. Duplicate reporting, incomplete descriptions, ambiguous locations, missing weather information and differences between publication date and accident date can affect the extracted data.

The next stage should perform event-level deduplication and validation before the model is used as an operational severity predictor.

## 8. Repository Contents

```text
Road-Accident-Business-Analytics/
├── README.md
├── data/
│   ├── collected_dataset.csv
│   └── cleaned_pilot_dataset.csv
├── analysis.ipynb
└── Case_Study_Report.pdf
```

## 9. References

- Zhang et al. (2023). *Predicting the severity of traffic accidents on mountain freeways with dynamic traffic and weather data*. Transportation Safety and Environment, 5(4), tdad001.
- *Evaluating expressway traffic crash severity by using logistic regression and explainable & supervised machine learning classifiers* (2023).
- Khanum et al. (2025). *A methodological framework for road accident severity prediction for Indian highways using machine learning models*. MethodsX, 15, 103728. DOI: 10.1016/j.mex.2025.103728.
- Phojaem et al. (2026). *Comparative injury-severity modeling on highway-speed motorways: performance, interpretability, and policy implications*. Case Studies on Transport Policy, 24, 101826.
- Tamil Nadu GIS Accident Dashboard, Government of Tamil Nadu.
- Apify Google News scraping platform/documentation.
- Google News public search results and linked public news webpages.
