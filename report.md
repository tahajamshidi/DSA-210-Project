# DSA 210 Term Project Report

# Machine Learning Analysis of Global Population and Economic Growth (2000–2025)

---

# Introduction

Economic growth and population dynamics are closely interconnected and vary significantly across countries and regions. Factors such as GDP per capita, demographic trends, regional characteristics, wars, and natural disasters all influence national development patterns. Understanding these relationships is important because it helps governments, economists, and policymakers better understand long-term development trends, economic stability, and demographic changes.

The main purpose of this project is to analyze the relationship between population growth and economic indicators using data science and machine learning techniques. The project investigates whether economic, demographic, and regional variables can successfully explain and predict GDP growth behavior.

The analysis combines:

* Data preprocessing
* Feature engineering
* Exploratory Data Analysis (EDA)
* Statistical hypothesis testing
* Supervised machine learning
* Hyperparameter tuning
* Feature importance analysis
* Unsupervised learning using K-Means clustering

The project also aims to identify natural economic-demographic groupings among countries and determine which variables contribute most strongly to GDP growth classification.

---

# Dataset Description

The dataset used in this project is:

* `Global_Population_Economic_Growth_2000_2025_BALANCED.csv`

The dataset contains yearly country-level observations between 2000 and 2025.

The main variables include:

| Variable               | Description                       |
| ---------------------- | --------------------------------- |
| Country                | Country name                      |
| Year                   | Observation year                  |
| GDP_Per_Capita         | GDP per capita                    |
| GDP_Growth_Rate        | Annual GDP growth rate            |
| Population_Growth_Rate | Annual population growth rate     |
| Continent              | Geographic continent              |
| War                    | Indicates war/conflict occurrence |
| Disaster               | Indicates disaster occurrence     |

The dataset contains balanced observations from multiple countries and continents.

---

# Data Cleaning and Preprocessing

Before analysis, multiple preprocessing operations were performed to improve data quality and model performance.

## Handling Missing Values

Missing values were removed from important variables to avoid inconsistencies during training and analysis.

Certain operations such as lagged variables and percentage-change calculations naturally created missing values (`NaN`) in the first observation of each country. These rows were removed after feature generation.

---

# Feature Engineering

Feature engineering was one of the most important stages of the project because raw variables alone were insufficient for capturing economic patterns.

Several additional variables and transformations were created.

## Logarithmic Transformation of GDP

GDP per capita values were highly skewed because wealthy countries had much larger GDP values compared to developing countries.

To reduce skewness and stabilize variance, logarithmic transformation was applied.

This transformation improved model stability and reduced the effect of extreme outliers.

### Figure 1 — Distribution of Raw GDP Per Capita

<img width="641" height="467" alt="Screenshot 2026-05-18 at 8 32 33 PM" src="https://github.com/user-attachments/assets/9b4c3b1d-3251-4ae6-8b5f-5c87c0184cfc" />

Interpretation:
The original GDP distribution is heavily right-skewed because wealthy countries have extremely large GDP values. Most observations are concentrated in lower GDP ranges.

---

### Figure 2 — Distribution of Log GDP Per Capita

<img width="664" height="466" alt="Screenshot 2026-05-18 at 8 33 33 PM" src="https://github.com/user-attachments/assets/9885c8e0-4d2e-4638-a3ff-c7892e53d06e" />




Interpretation:
After logarithmic transformation, the GDP distribution becomes significantly more balanced and closer to a normal distribution. This improves statistical analysis and machine learning stability.

---

# GDP Growth Calculation

Country-level GDP growth was calculated using year-to-year percentage change.

The implementation grouped observations by country before computing percentage change. This ensured that GDP growth was calculated independently for each country.

---

# GDP Growth Classification

GDP growth values were converted into categorical classes using quantile-based categorization (`qcut`).

Three balanced classes were created:

| Class | Meaning           |
| ----- | ----------------- |
| 0     | Low GDP Growth    |
| 1     | Medium GDP Growth |
| 2     | High GDP Growth   |

This transformed the problem into a multiclass classification task suitable for supervised machine learning.

---

# Continent Mapping

Countries were grouped into continents using a manually created continent mapping dictionary.

Special country naming cases and edge cases were also handled carefully to ensure consistency.

---

# Exploratory Data Analysis (EDA)

EDA was conducted to understand distributions, relationships, trends, and anomalies within the dataset.

## Population Growth Distribution

### Figure 3 — Population Growth Rate Distribution

<img width="628" height="461" alt="Screenshot 2026-05-18 at 8 34 01 PM" src="https://github.com/user-attachments/assets/780917e9-6b0d-4dc9-af7a-0a958f41630c" />


Interpretation:
Most countries cluster around low-to-moderate population growth rates, while several developing countries exhibit extremely high growth rates. Some developed countries also display negative population growth.

---

## GDP vs Population Growth Relationship

### Figure 4 — GDP Per Capita vs Population Growth Rate

<img width="945" height="558" alt="Screenshot 2026-05-18 at 8 34 26 PM" src="https://github.com/user-attachments/assets/ca19d56a-d560-4fb6-904b-6ced0d85b0ae" />


Interpretation:
The scatterplot shows that countries with higher GDP per capita generally tend to have lower population growth rates. Developing economies appear more concentrated in higher population growth regions.

---

## GDP Trends by Continent

### Figure 5 — GDP Per Capita Over Time by Continent

<img width="1067" height="558" alt="Screenshot 2026-05-18 at 8 34 54 PM" src="https://github.com/user-attachments/assets/bfb667ee-8168-4856-b172-705128b97b2e" />


Interpretation:
North America and Europe maintain consistently high GDP levels throughout the observed years. Asia shows significant growth over time, while Africa remains comparatively lower.

---

## Log GDP Trends by Continent

### Figure 6 — Log GDP Over Time by Continent

<img width="1051" height="545" alt="Screenshot 2026-05-18 at 8 35 16 PM" src="https://github.com/user-attachments/assets/063a081d-7674-4b56-8634-243930903dfb" />


Interpretation:
The logarithmic transformation reveals long-term growth patterns more clearly and reduces visual distortion caused by extremely wealthy countries.

---

## Combined GDP and Population Growth Trends

### Figure 7 — GDP and Population Growth Trends by Continent

<img width="515" height="609" alt="Screenshot 2026-05-18 at 8 36 14 PM" src="https://github.com/user-attachments/assets/cb6b0971-9ad1-46f7-9fbd-d623410252b8" />
<img width="511" height="614" alt="Screenshot 2026-05-18 at 8 36 37 PM" src="https://github.com/user-attachments/assets/97366913-3ad4-4a6b-9fe6-d087f3fa3151" />


Interpretation:
Different continents display distinct economic-demographic behavior. Some regions exhibit rapid GDP growth with declining population growth, while others experience higher population growth alongside slower economic development.

---

# Correlation Analysis

Correlation matrices and heatmaps were generated to identify relationships between variables.

### Figure 8 — Correlation Heatmap

<img width="529" height="422" alt="Screenshot 2026-05-18 at 8 37 11 PM" src="https://github.com/user-attachments/assets/c374c0ce-f47e-4e49-af47-b0e86a79cadd" />
<img width="1365" height="900" alt="Screenshot 2026-05-18 at 10 58 22 PM" src="https://github.com/user-attachments/assets/cb897a4d-013a-431f-a229-fe897e48f40c" />


Interpretation:
GDP-related variables show stronger positive relationships with each other, while war and disaster variables have weaker direct correlations. Population growth exhibits weaker linear relationships with GDP variables.

---

# Statistical Hypothesis Testing

Several hypothesis tests were conducted to statistically evaluate economic-demographic relationships.

## ANOVA Test for Continents and Population Growth

One-way ANOVA was used to test whether population growth rates differed significantly across continents.

The test produced statistically significant results (`p < 0.05`). Therefore, the null hypothesis was rejected, indicating that population growth patterns differ significantly between continents.

---

# Correlation Hypothesis Testing

Pearson correlation analysis was used to evaluate relationships between GDP and population growth.

The results showed weak-to-moderate relationships between GDP and population growth variables.

---

# War and Disaster Analysis

The project also investigated whether wars and natural disasters significantly influenced GDP growth.

### Figure 9 — GDP Growth Rate: War vs No War

<img width="639" height="475" alt="Screenshot 2026-05-18 at 8 37 49 PM" src="https://github.com/user-attachments/assets/26e56d6b-b780-44f5-b577-301da55b4c49" />


Interpretation:
Countries experiencing wars generally display more unstable GDP growth distributions compared to non-war observations.

---

### Figure 10 — GDP Growth Rate: Disaster vs No Disaster

<img width="647" height="497" alt="Screenshot 2026-05-18 at 8 38 04 PM" src="https://github.com/user-attachments/assets/7451dfed-c7b4-4383-93f3-35816733e72d" />


Interpretation:
Natural disasters also influence GDP growth patterns, although the distributions overlap substantially with non-disaster observations.

---

# Supervised Machine Learning

Several supervised machine learning models were implemented to predict GDP growth classes.

The models included:

* Logistic Regression
* Decision Tree
* Random Forest
* Gradient Boosting
* KNN
* SVM

The dataset was split into:

* 80% training data
* 20% testing data

Feature scaling was applied using `StandardScaler` for models sensitive to feature magnitude.

---

# Logistic Regression

Logistic Regression was implemented as the baseline classification model.

## Logistic Regression Results

* Accuracy ≈ 56%
* Macro F1-score ≈ 0.55

### Figure 11 — Logistic Regression Confusion Matrix

<img width="559" height="421" alt="Screenshot 2026-05-18 at 8 38 36 PM" src="https://github.com/user-attachments/assets/18bfd5d9-d6d1-4d91-8381-eebddbdf5dfc" />


Interpretation:
The model performs relatively well for low-growth countries but struggles more with medium-growth observations, indicating overlapping economic patterns.

---

# Decision Tree

Decision Trees were used to capture nonlinear relationships through hierarchical feature splits.

## Decision Tree Results

* Accuracy ≈ 62%
* Macro F1-score ≈ 0.62

The model improved performance compared to Logistic Regression.

---

# Random Forest

Random Forest combined multiple decision trees using ensemble learning.

## Random Forest Results

* Baseline Accuracy ≈ 66%
* Tuned Accuracy ≈ 67.3%
* Tuned Macro F1-score ≈ 0.669

### Figure 12 — Random Forest Confusion Matrix

<img width="541" height="413" alt="Screenshot 2026-05-18 at 8 39 05 PM" src="https://github.com/user-attachments/assets/5c866bf8-6c7e-46e8-b4ac-bb3c5931809e" />


Interpretation:
Random Forest achieved stronger balanced classification across all GDP growth classes and became the best-performing model.

---

# Gradient Boosting / XGBoost

Boosting models sequentially corrected prediction errors from previous trees.

## Gradient Boosting Results

* Accuracy ≈ 63%
* Macro F1-score ≈ 0.628

The model performed well but remained slightly weaker than Random Forest.

---

# K-Nearest Neighbors (KNN)

KNN classification used nearest-neighbor relationships.

## KNN Results

* Accuracy ≈ 66.8%
* Macro F1-score ≈ 0.664

KNN became one of the strongest-performing models.

---

# Support Vector Machine (SVM)

SVM attempted to maximize class separation margins.

## SVM Results

* Accuracy ≈ 59%
* Macro F1-score ≈ 0.584

The model struggled with overlapping economic patterns.

---

# Hyperparameter Tuning

`GridSearchCV` was used for optimization.

Parameters tuned included:

* Tree depth
* Number of estimators
* Learning rate
* Number of neighbors
* Regularization strength

Tuning improved multiple models, especially Random Forest and KNN.

---

# Final Model Comparison

| Model               | Tuned Accuracy | Tuned Macro F1 |
| ------------------- | -------------- | -------------- |
| Random Forest       | ~0.673         | ~0.669         |
| KNN                 | ~0.668         | ~0.664         |
| Gradient Boosting   | ~0.631         | ~0.628         |
| Decision Tree       | ~0.622         | ~0.618         |
| SVM                 | ~0.591         | ~0.584         |
| Logistic Regression | ~0.568         | ~0.548         |

### Figure 13 — Tuned Model Performance Comparison

<img width="663" height="209" alt="Screenshot 2026-05-18 at 8 40 26 PM" src="https://github.com/user-attachments/assets/981fc404-1516-43b8-b5ee-4e090db9d820" />
<img width="891" height="554" alt="Screenshot 2026-05-18 at 8 41 25 PM" src="https://github.com/user-attachments/assets/9cb169c8-195c-45a7-acf7-597fd968df33" />



Interpretation:
Random Forest and KNN achieved the strongest overall performance, indicating that nonlinear models are more suitable for economic-demographic prediction tasks.

---

# Feature Importance Analysis

Feature importance analysis was conducted using XGBoost.

The most important features included:

* `log_GDP`
* `GDP_Growth_Rate`
* `GDP_Year_Low GDP`
* `Continent_North America`
* `Continent_South America`
* `Continent_Asia`

### Figure 14 — Feature Importance Plot


<img width="923" height="471" alt="Screenshot 2026-05-18 at 8 42 05 PM" src="https://github.com/user-attachments/assets/1962790b-1752-479c-afe3-b3e24a9cce7e" />



Interpretation:
GDP-related variables dominate prediction performance, while regional indicators also contribute strongly. War and disaster variables show relatively lower predictive importance.

---

# K-Means Clustering

Unsupervised learning was applied using K-Means clustering.

Features included:

* GDP per capita
* Population growth rate
* War variables
* Disaster variables

---

# Elbow Method

The Elbow Method was used to determine the optimal cluster count.

The inertia curve flattened around:

K = 3

### Figure 15 — Elbow Method Plot

<img width="615" height="462" alt="Screenshot 2026-05-18 at 8 42 34 PM" src="https://github.com/user-attachments/assets/fdf832cf-f305-4828-ab4f-42ff37e2240b" />


Interpretation:
The elbow point appears around K=3, indicating that three clusters provide a reasonable balance between model simplicity and explanatory power.

---

# Cluster Interpretation

## Cluster 0

Characteristics:

* Moderate GDP
* Stable economic conditions
* Low conflict occurrence

---

## Cluster 1

Characteristics:

* Lower GDP
* Higher population growth
* Greater demographic instability

---

## Cluster 2

Characteristics:

* High GDP
* Lower population growth
* More developed economies

---

# Cluster Visualization

### Figure 16 — K-Means Clustering Scatter Plot

<img width="652" height="476" alt="Screenshot 2026-05-18 at 8 42 55 PM" src="https://github.com/user-attachments/assets/3a4f34ee-8104-4500-b7e6-83e0a0c56b84" />


Interpretation:
The scatter plot demonstrates visible separation between economic-demographic groups. High-income countries form distinct regions, while developing economies cluster separately.

---

# Overall Findings

The project revealed several important findings:

1. GDP-related variables dominate prediction performance.
2. Regional indicators strongly influence growth patterns.
3. Ensemble learning methods outperform linear models.
4. Random Forest achieved the highest predictive performance.
5. K-Means clustering revealed meaningful economic-demographic groups.
6. Population growth and GDP growth relationships are nonlinear.
7. Long-term structural economic variables are more important than short-term crisis events.

---

# Limitations

Several limitations exist in the project:

* Event variables had relatively low predictive power.
* Some countries may contain reporting inconsistencies.
* Economic systems depend on hidden variables not included in the dataset.
* Clustering depends heavily on selected variables and scaling methods.

---

# Conclusion

This project successfully applied machine learning and clustering techniques to analyze global population and economic growth patterns between 2000 and 2025.

The analysis demonstrated that:

* GDP growth can be reasonably classified using economic and demographic variables.
* Random Forest and KNN achieved the strongest results.
* Regional and structural economic factors strongly influence development.
* Countries naturally cluster into distinct economic-demographic profiles.

The project highlights how machine learning and data science techniques can provide valuable insights into global economic systems and demographic behavior.

---

# References

1. Global Population and Economic Growth Dataset
   [https://www.kaggle.com/datasets/abidhussai512/global-population-and-economic-growth-dataset](https://www.kaggle.com/datasets/abidhussai512/global-population-and-economic-growth-dataset)

2. World Bank API
   [https://data.worldbank.org/](https://data.worldbank.org/)

3. EM-DAT International Disaster Database
   [https://www.emdat.be/](https://www.emdat.be/)

4. Uppsala Conflict Data Program (UCDP)
   [https://www.uu.se/en/websites/ucdp---uppsala-conflict-data-program](https://www.uu.se/en/websites/ucdp---uppsala-conflict-data-program)

5. Scikit-learn Documentation
   [https://scikit-learn.org/](https://scikit-learn.org/)

6. Pandas Documentation
   [https://pandas.pydata.org/](https://pandas.pydata.org/)

7. Seaborn Documentation
   [https://seaborn.pydata.org/](https://seaborn.pydata.org/)

8. Statsmodels Documentation
   [https://www.statsmodels.org/](https://www.statsmodels.org/)

---

# AI Assistance Disclosure

AI tools were used during development for debugging assistance, code refinement, explanation of methods, and documentation support.

All final implementation decisions, analysis, and interpretations were reviewed and completed by the project author.
