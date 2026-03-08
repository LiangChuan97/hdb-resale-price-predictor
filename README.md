<h1 align="center">🏠 Machine Learning for HDB Resale Flat Price Estimation</h1>

<p align="center">
<img src="https://img.shields.io/badge/Python-3.14-blue">
<img src="https://img.shields.io/badge/Models-Linear%20Regression%20%7C%20Random%20Forest%20%7C%20⭐%20XGBoost-blue">
<img src="https://img.shields.io/badge/Domain-Real%20Estate-orange">
<img src="https://img.shields.io/badge/Data-HDB%20Resale-purple">
<img src="https://img.shields.io/badge/Dashboard-Tableau-red">
</p>

## 🚀 Project Summary

This project develops a machine learning model to estimate HDB resale prices in Singapore using housing characteristics, location attributes, and accessibility features.

Key Highlights:

- Built a machine learning model to predict HDB resale prices using housing characteristics, location attributes, and accessibility features.
- Conducted exploratory data analysis to identify key drivers of property prices such as floor area, storey level, MRT proximity, and flat age.
- Engineered additional features including remaining lease and regional housing classification to improve model performance.
- Compared multiple regression models including Linear Regression, Random Forest, and XGBoost.
- XGBoost achieved the best performance, explaining 97% of the variance in resale prices.
- The final model provides a data-driven pricing reference to support real estate agents and buyers in property valuation decisions.
- Developed a Tableau dashboard to enable interactive exploration of HDB resale market trends.

## 🧠 Skills Demonstrated

- Regression modelling
- Feature engineering for property pricing
- Exploratory data analysis
- Model comparison (Linear Regression, Random Forest, XGBoost)
- Data visualisation with Tableau
- Real estate price modelling

## 📑 Table of Contents

- [Project Overview](#-project-overview)
- [Business Problem](#-business-problem)
- [Dataset](#-dataset)
- [Data Cleaning](#-data-cleaning)
- [Exploratory Data Analysis](-exploratory-data-analysis)
- [Key Market Insights](-key-market-insights)
- [Feature Engineering](#-feature-engineering)
- [Model Development](#-model-development)
- [Model Evaluation](#-model-evaluation)
- [Business Insights](#-business-insights)
- [Business Recommendations](#-business-recommendations)
- [Business Value](#-business-value)
- [Limitations](#-limitations)
- [Tech Stack](#-tech-stack)
- [Future Improvements](#-future-improvements)
- [HDB Pricing Decision Tool](#-hdb-pricing-decision-tool)

## 🚀 Project Overview

This project develops a machine learning model to estimate Singapore HDB resale prices using housing characteristics, location data, and nearby amenities.

Using historical transaction data, the analysis identifies key price drivers such as:
- Floor size
- Remaining lease
- Distance to MRT
- Storey level
- Town and region
- Flat model tier
- Transaction year

The model provides a data-driven pricing reference to support real estate agents when advising buyers and sellers on resale pricing.

The project includes:
- Exploratory data analysis to identify price drivers
- Feature engineering to capture housing and accessibility factors
- Model comparison across multiple regression algorithms
- Tableau dashboard for interactive market exploration
- Model export for resale price estimation tools
- Business insights on key price drivers
- Data-driven recommendations for agents, buyers, and sellers
- Discussion of project limitations and future improvements

## 🏠 Business Problem

Determining the correct listing price for HDB flats can be challenging.

Pricing too high may reduce buyer interest, while pricing too low may result in lost value for sellers.

A predictive pricing model can help agents:
- Advise sellers on competitive listing prices
- Help buyers determine fair market value
- Identify undervalued investment opportunities

## 🗂 Dataset

The dataset contains historical HDB resale transactions and property characteristics which was sourced from <a href = "https://www.kaggle.com/competitions/dsi-sg-project-2-regression-challenge-hdb-price/data"> kaggle. </a> 

Target variable:

resale_price

Example features include:
- town
- flat_type
- floor_area_sqm
- lease_commence_date
- mrt_nearest_distance
- storey
- planning_area

The dataset also includes geographic coordinates and amenity proximity features.

## 🧹 Data Cleaning

The following preprocessing steps were applied:
- Handling missing values for amenity variables
- Verifying absence of duplicate records
- Removing irrelevant variables
- Converting binary indicators to boolean format
- Ensuring correct data types for all features
- Extracting transaction year and month
- Exporting cleaned dataset for analysis

## 🔍 Exploratory Data Analysis

Key questions explored:
- What factors influence HDB resale prices?
- How does flat size (floor area) affect resale price?
- Does higher storey attributes to higher resale value?
- Are there price differences across towns or locations?
- Does proximity to MRT stations increase property value?
- Does flat age or lease duration affect resale value?
- How strongly are the features correlated with resale price?

These questions help identify the most relevant predictors for the resale price model.

## 📊 Key Market Insights

The resale price of HDB flats varies significantly depending on:

<h2 align="center">Property Size Drives Price</h2>

<p align="center"><img width="1016" height="821" alt="Screenshot 2026-03-07 at 18 44 24" src="https://github.com/user-attachments/assets/9503b49c-65d1-488e-a5fa-d7da53db0130" />

Floor area is one of the strongest predictors of resale price. Larger flats generally command significantly higher prices, showing a clear positive relationship between floor_area_sqm and resale_price. 

<h2 align="center">Higher Storey Level Drives Price</h2>

<p align="center"><img width="1016" height="367" alt="Screenshot 2026-03-07 at 19 24 22" src="https://github.com/user-attachments/assets/7b96b152-24e7-4306-af21-a958f88a7620" />

Higher floors are often more desirable due to better views, reduced noise, and improved ventilation, which contributes to higher resale values. However, most resale transactions still occur at mid-level floors, where supply is more abundant.


<h2 align="center">Location Plays a Major Role </h2>

<p align="center"><img width="1016" height="821" alt="Screenshot 2026-03-07 at 18 46 18" src="https://github.com/user-attachments/assets/8dabfe7d-b531-446b-969f-54f0fbbede6e" />

Resale prices vary noticeably across towns and planning areas. Flats located in central or mature estates tend to have higher resale values compared to those in less central locations.

<h2 align="center">Accessibility to Public Transport</h2>

<p align="center"><img width="1016" height="458" alt="Screenshot 2026-03-07 at 18 47 18" src="https://github.com/user-attachments/assets/daf03a5c-cfd9-4c91-9ad5-74af622cd684" />

Flats located closer to MRT stations tend to have higher resale prices. The variable mrt_nearest_distance shows that properties with better transport accessibility often command a price premium.

<h2 align="center">Age of the Flat Matters </h2>

<p align="center"><img width="1016" height="367" alt="Screenshot 2026-03-07 at 18 51 09" src="https://github.com/user-attachments/assets/afd02e56-06b1-48c5-82cf-8976b22a9864" />
 
Older flats with shorter remaining lease periods generally have lower resale prices. This highlights the importance of variables such as lease_commence_date and flat_age in predicting resale value.

<h2 align="center">Correlation Heatmap</h2>

<p align="center"><img width="590" height="523" alt="image" src="https://github.com/user-attachments/assets/c1f19c28-d83e-4cef-be0a-f313eead1b4e" />

Floor area shows the strongest positive relationship with resale price (0.65), indicating that larger flats command significantly higher prices. Flat age is negatively correlated with price (-0.35), suggesting older flats with shorter remaining leases tend to sell for less, while higher storey levels show a moderate positive impact on resale value.

## ⚙️ Feature Engineering

Additional variables were created to improve modelling performance:
- remaining_lease = 99 - hdb_age
- region categorising planning areas by Singapore region

These features help capture:
- housing lifespan
- geographical housing patterns

## 🧠 Model Development

To estimate HDB resale prices, several regression models were developed and compared.

The goal was to identify a model that could accurately predict resale prices while also providing insights into the factors influencing property values.

The modelling workflow included:
- selecting relevant housing and location features
- splitting the dataset into training and testing sets
- training multiple regression models
- evaluating model performance using prediction error

Model performance was evaluated using Root Mean Squared Error (RMSE), which measures the difference between predicted and actual resale prices.

RMSE measures the average difference between predicted resale prices and the actual transaction prices.

Lower RMSE values indicate that the model is making more accurate predictions.


<h2 align="center">Linear Regression (Baseline Model) </h2>

A Linear Regression model was first implemented as a baseline model.

This model assumes a linear relationship between housing features and resale price.

It provides a simple and interpretable starting point for understanding how factors such as:
- floor area
- remaining lease
- proximity to MRT stations
- location

affect resale prices.

While simple, this model helps establish a benchmark for comparing more advanced algorithms.

<h2 align="center">Random Forest Regressor</h2>

A Random Forest Regressor was trained to capture more complex relationships between housing characteristics and resale prices.

Random Forest combines many decision trees and averages their predictions, which helps improve prediction accuracy and reduce overfitting.

This model is particularly useful when relationships between variables are nonlinear, such as:
- the impact of location on price
- interactions between flat size and accessibility

<h2 align="center">XGBoost Regressor</h2>

An XGBoost Regressor was also implemented as an advanced machine learning model designed for strong predictive performance.

XGBoost builds trees sequentially, where each new tree improves on the errors of the previous one. This allows the model to capture subtle patterns in the data and often results in higher predictive accuracy.

The model was trained with tuned parameters to optimise performance on the resale price prediction task.

<h2 align="center">Top Features of resale price used in the Models </h2>

The models were trained using a combination of property characteristics, location data, and accessibility features, including:
- floor_area_sqft
- remaining_lease_years
- mrt_nearest_distance
- mid (storey level indicator)
- flat_model_tier
- town
- region

These variables were selected based on insights obtained during the exploratory data analysis.

## 📊 Model Evaluation

| | Linear Regression | RandomForest | ⭐ XGBoost |
|---|---|---|---|
| R2 | 0.872 | 0.925 | 0.970 |
| RMSE | 51135.77 | 39160.78 | 24958.11|
| MAE | 36777.51 | 30155.43| 17942.72 |


<h2 align="center">🏆 Best Model </h2>

The **XGBoost model** achieved the best predictive performance.

- Highest R² (0.970)
This means the model explains 97% of the variance in HDB resale prices, indicating a very strong fit to the data.

- Lowest RMSE (24,958)
RMSE measures the average magnitude of prediction errors.
Compared to the other models, XGBoost produces much smaller prediction errors, meaning its predicted prices are closer to the actual resale prices.

- Lowest MAE (17,943)
MAE measures the average absolute difference between predicted and actual prices.
The lower MAE indicates that XGBoost consistently produces more accurate predictions.

Interpretation

The strong performance of XGBoost is likely due to its ability to:
- capture non-linear relationships between housing features and resale prices
- model interactions between variables such as floor area, location, and accessibility
- iteratively correct prediction errors through gradient boosting

As a result, XGBoost was selected as the final model for predicting HDB resale prices.

## 💡 Business Insights

Major drivers of HDB resale prices include:
- Floor area
- Flat type
- Distance to MRT
- HDB Storey
- Town/location
- Flat Model Tier
- Flat age

✔ Larger flats tend to have higher resale prices, making floor area one of the strongest predictors of property value.
<p>✔ Higher floors generally command higher prices due to desirability, although most transactions occur at mid-level floors where supply is greater.
<p>✔ Resale prices vary by town, with flats in central or mature estates typically selling at higher values.
<p>✔ Flats closer to MRT stations often sell at higher prices, reflecting the value of transport convenience.
<p>✔ Older flats with shorter remaining leases tend to have lower resale prices.


## 💡 Business Recommendations

Real estate agents, buyers should prioritise:
- larger flats with higher floor area
- properties near MRT stations
- flats in high-demand towns such as Queenstown and Bukit Merah
- newer flats with longer remaining lease

## 💰 Business Value

This model provides a data-driven pricing benchmark for real estate agents.

Benefits include:

- Faster property valuation
- More accurate listing prices
- Identification of undervalued flats
- Improved buyer negotiation insights

These factors significantly influence resale value.


## ⚠️ Limitations

- Dataset contains a 5-year data gap
- Cannot capture behavioural factors such as buyer preferences
- Government policies such as HIP or LIP are not included
- Macroeconomic factors like inflation are not captured
- Final transaction prices also depend on market liquidity and negotiation

## 🧰 Tech Stack

🐍 Python
📊 Pandas
🤖 Scikit-learn
📈 Matplotlib / Seaborn
📊 Tableau


## 🚀 Future Improvements

Possible next steps include:
- Incorporating buyer preference features
- Predicting price ranges instead of point estimates
- Developing a lease-adjusted pricing framework
- Tailoring market insights by planning area

## 🏠 HDB Pricing Decision Tool

The trained model can be used as a pricing support tool for real estate agents.

Instead of relying solely on comparable listings, the model provides a data-driven estimate of fair market value based on property characteristics.

### Example Prediction

| Feature | Value |
|--------|-------|
| Floor Area | 90 sqm |
| Remaining Lease | 75 years |
| Distance to MRT | 450 m |
| Storey Level | 12 |
| Town | Queenstown |

**Predicted Resale Price:** **$612,450**

Agents can use this estimate to:
- benchmark listing prices
- evaluate buyer offers
- identify undervalued flats in the market
