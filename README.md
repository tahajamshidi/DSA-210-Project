# DSA-210-Project

# Global Population and Economic Growth Analysis

---

## Project Overview

This project analyzes the relationship between economic development and population growth across countries between 2000 and 2025.

The project studies how GDP per capita, GDP growth, regional differences, and major events such as wars and natural disasters relate to demographic trends around the world.

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

### Main Variables

- Country
- Year
- GDP_Per_Capita
- Population_Growth_Rate

### Data Sources

- World Bank API
- Publicly available economic datasets
- Kaggle Dataset: https://www.kaggle.com/datasets/abidhussai512/global-population-and-economic-growth-dataset

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

The war and disaster variables were manually enriched using public international conflict and disaster databases.

---

## Repository Structure

```text
data/           -> dataset files
notebooks/      -> notebooks used during development
src/            -> additional source files
README.md       -> project documentation
proposal.pdf    -> project proposal
DSA_210_project_stage_4.ipynb -> final notebook
```

---

## Exploratory Data Analysis (EDA)

The project includes:

- Histograms
- Scatterplots
- Line plots
- Boxplots
- Correlation heatmaps

The EDA phase was used to identify economic and demographic trends across countries and continents.

---

## Hypothesis Testing

The following statistical tests were applied:

- Pearson correlation tests
- ANOVA
- Independent t-tests

These tests were used to evaluate statistical relationships between GDP, population growth, wars, disasters, and continent-based differences.

---

## Machine Learning Models

The following machine learning models were compared:

- Logistic Regression
- Decision Tree
- Random Forest
- Gradient Boosting
- KNN
- SVM

Hyperparameter tuning was performed using GridSearchCV.

The models were evaluated using:

- Accuracy
- Macro F1-score
- Classification reports
- Confusion matrices

---

## Clustering

K-Means clustering was applied as an unsupervised learning method.

The clustering analysis was used to identify groups of countries with similar economic and demographic characteristics.

---

## Key Findings

- GDP per capita and population growth show statistically significant relationships.
- Population growth patterns differ significantly across continents.
- Economic variables such as GDP and GDP growth are among the strongest predictors in machine learning models.
- Random Forest and ensemble-based methods generally performed better than simpler baseline models.
- Hyperparameter tuning improved model performance.
- Wars and disasters showed measurable relationships with GDP growth in several analyses.

---

## Visualizations

The project includes visualizations such as:

- GDP distribution plots
- Population growth distributions
- GDP vs population growth scatterplots
- Continent-wise comparisons
- Correlation heatmaps
- Confusion matrices
- Feature importance plots
- K-Means clustering plots

---

## How to Run

1. Clone the repository
2. Install dependencies
3. Open the notebook in Jupyter Notebook or Google Colab
4. Run all cells sequentially

---

## Requirements

Install dependencies using:

```bash
pip install -r requirements.txt
```

### Main Libraries Used

- pandas
- numpy
- matplotlib
- seaborn
- scipy
- scikit-learn
- statsmodels

---

## Future Work

Possible future improvements include:

- Adding more economic indicators
- Including migration and fertility data
- Using deeper time-series forecasting models
- Expanding war/disaster datasets
- Applying advanced ensemble learning techniques
- Using larger real-world conflict event datasets

---

## References

1. Global Population and Economic Growth Dataset  
https://www.kaggle.com/datasets/abidhussai512/global-population-and-economic-growth-dataset

Explanation: Main dataset containing country-level GDP per capita and population growth information between 2000 and 2025.

---

2. World Bank API  
https://data.worldbank.org/

Explanation: Source of economic and demographic indicators used in the dataset.

---

3. EM-DAT International Disaster Database  
https://www.emdat.be/

Explanation: Used as reference source for identifying major global natural disaster events added to the enrichment process.

---

4. Uppsala Conflict Data Program (UCDP)  
https://www.uu.se/en/websites/ucdp---uppsala-conflict-data-program

Explanation: Used as reference source for identifying major international war and conflict events added to the enrichment process.

---

5. Pandas Documentation  
https://pandas.pydata.org/

Explanation: Used for data cleaning, preprocessing, and manipulation.

---

6. Statsmodels Documentation  
https://www.statsmodels.org/

Explanation: Used for statistical analysis and hypothesis testing.

---

## AI Assistance Disclosure

AI tools were used during development for debugging assistance, code refinement, explanation of methods, and documentation support.

All final implementation decisions, analysis, and interpretations were reviewed and completed by the project author.
