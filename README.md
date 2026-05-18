# DSA-210-Project
# Global Population and Economic Growth Analysis

## Project Overview

This project analyzes the relationship between economic development and population growth across countries between 2000 and 2025. The project studies how GDP per capita, GDP growth, regional differences, and major events such as wars and natural disasters relate to demographic trends around the world.

The analysis includes exploratory data analysis (EDA), statistical hypothesis testing, supervised machine learning models, hyperparameter tuning, and unsupervised clustering methods.

---

## Objectives

The main objectives of this project are:

- Analyze the relationship between GDP per capita and population growth
- Compare demographic patterns across continents
- Investigate the effects of wars and disasters on GDP growth
- Build machine learning models for predicting GDP growth classes
- Compare multiple machine learning models
- Apply hyperparameter tuning using GridSearchCV
- Interpret feature importance and model performance differences

---

## Dataset

The dataset contains country-level economic and demographic information between 2000 and 2025.

Main variables include:

- Country
- Year
- GDP_Per_Capita
- Population_Growth_Rate

Data source:
- World Bank API
- Publicly available economic datasets
- Kaggle

---

## Data Enrichment

Several additional features were created to enrich the dataset:

- Log-transformed GDP (`log_GDP`)
- GDP growth rate
- GDP category by year (`GDP_Year`)
- Continent mapping
- War indicators
- Disaster indicators
- Lagged war/disaster variables

---

## Repository Structure

```text
data/           -> dataset files
notebooks/      -> notebooks used during development
src/            -> additional source files
README.md       -> project documentation
proposal.pdf    -> project proposal

---

Exploratory Data Analysis (EDA)

The project includes:

Histograms
Scatterplots
Line plots
Boxplots
Correlation heatmaps
Hypothesis Testing

The following statistical tests were applied:

Pearson correlation tests
ANOVA
Independent t-tests
Machine Learning Models

The following machine learning models were compared:

Logistic & Linear Regression
Decision Tree
Random Forest
Gradient Boosting
KNN
SVM

Hyperparameter tuning was performed using GridSearchCV.

Clustering

K-Means clustering was applied as an unsupervised learning method.

---

Key Findings:

GDP per capita and population growth show statistically significant relationships.
Population growth patterns differ significantly across continents.
Economic variables such as GDP and GDP growth are among the strongest predictors in machine learning models.
Random Forest and ensemble-based methods generally performed better than simpler baseline models.
Hyperparameter tuning improved model performance.
Visualizations

The project includes visualizations such as:

GDP distribution plots
Population growth distributions
GDP vs population growth scatterplots
Continent-wise comparisons
Correlation heatmaps
Confusion matrices
Feature importance plots
K-Means clustering plots

---

Main libraries used:

pandas
numpy
matplotlib
seaborn
scipy
scikit-learn
xgboost
Future Work

---

Possible future improvements include:

Adding more economic indicators
Including migration and fertility data
Using deeper time-series forecasting models
Expanding war/disaster datasets
Applying advanced ensemble learning techniques

---

AI Assistance Disclosure

AI tools were used during development for debugging assistance, code refinement, explanation of methods, and documentation support. All final implementation decisions, analysis, and interpretations were reviewed and completed by the project author.
