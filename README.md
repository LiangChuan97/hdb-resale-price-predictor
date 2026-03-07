### 🏠 Predicting HDB Resale Prices in Singapore ###
***
<h2 align="center"><u>Project Overview</u></h2>

This project develops a machine learning model to estimate Singapore HDB resale prices using housing characteristics, location data, and nearby amenities. 

Using historical transaction data, it identifies key price drivers such as floor size (sq ft), remaining lease (years), distance to mrt, storey, resale transaction price(SGD), HDB town and flat model tier, region and transaction year, providing a data-driven pricing reference for real estate agents when advising on listing and purchase decisions.

The project includes:
	<p>• exploratory data analysis to identify price drivers</p>
	<p>• feature engineering to capture housing and accessibility factors</p>
	<p>• model comparison across multiple regression algorithms</p>
	<p>• a Tableau dashboard for interactive market exploration</p>
	<p>• model export for deployment in resale price estimation tools</p>
	<p>• business insights on key drivers influencing HDB resale prices</p>
	<p>• data-driven recommendations for agents, buyers, and sellers</p>
	<p>• discussion of project limitations and potential future improvements</p>

***

<h2 align="center"><u>Business Problem</u></h2>

Agents often struggle to determine the correct listing price for HDB flats. By accurately estimating resale prices helps real estate agents:
	<p>•advise sellers on competitive listing prices</p>
	<p>•help buyers determine fair market value</p>
	<p>•identify undervalued investment opportunities</p>

***

<h2 align="center"><u>Dataset</u></h2>

The dataset contains historical HDB resale transactions and property characteristics which was sourced from <a href = "https://www.kaggle.com/competitions/dsi-sg-project-2-regression-challenge-hdb-price/data"> kaggle. </a> 

Target variable:

resale_price

Example features:
	<p>•town</p>
	<p>•flat_type</p>
	<p>•floor_area_sqm</p>
	<p>•lease_commence_date</p>
	<p>•mrt_nearest_distance</p>
	<p>•storey</p>
	<p>•planning_area</p>

The dataset also includes geographic coordinates and amenity proximity features.

***

<h2 align="center"><u>Project Workflow</u></h2>

1. Data Cleaning

Steps performed:
- handled missing values by filling amenity count variables with 0 where appropriate
- checked for and verified absence of duplicated records
- removed irrelevant features to focus on location, transport, and housing-related variables
- converted binary indicator columns (e.g., MRT and school affiliation variables) to boolean format
- ensured correct data types for numerical, categorical, and boolean variables
- validated transaction date fields by extracting year and month from 'Tranc_YearMonth'
- exported the cleaned dataset for further analysis and modelling

2. Exploratory Data Analysis (EDA)

Key questions explored:
- What factors influence HDB resale prices?
- How does flat size (floor area) affect resale price?
- Does higher storey attributes to higher resale value?
- Are there price differences across towns or locations?
- Does proximity to MRT stations increase property value?
- Does flat age or lease duration affect resale value?
- How strongly are the features correlated with resale price?

These questions help identify the most relevant predictors for the resale price model.

The resale price of HDB flats varies significantly depending on:

<h2 align="center">Property Size Drives Price</h2>

<img width="1016" height="821" alt="Screenshot 2026-03-07 at 18 44 24" src="https://github.com/user-attachments/assets/9503b49c-65d1-488e-a5fa-d7da53db0130" />

Floor area is one of the strongest predictors of resale price. Larger flats generally command significantly higher prices, showing a clear positive relationship between floor_area_sqm and resale_price. 

<h2 align="center">Higher Storey Level Drives Price</h2>

<img width="1016" height="367" alt="Screenshot 2026-03-07 at 19 24 22" src="https://github.com/user-attachments/assets/7b96b152-24e7-4306-af21-a958f88a7620" />

Higher floors are often more desirable due to better views, reduced noise, and improved ventilation, which contributes to higher resale values. However, most resale transactions still occur at mid-level floors, where supply is more abundant.


<h2 align="center">Location Plays a Major Role </h2>

<img width="1016" height="821" alt="Screenshot 2026-03-07 at 18 46 18" src="https://github.com/user-attachments/assets/8dabfe7d-b531-446b-969f-54f0fbbede6e" />

Resale prices vary noticeably across towns and planning areas. Flats located in central or mature estates tend to have higher resale values compared to those in less central locations.

<h2 align="center">Accessibility to Public Transport</h2>

<img width="1016" height="458" alt="Screenshot 2026-03-07 at 18 47 18" src="https://github.com/user-attachments/assets/daf03a5c-cfd9-4c91-9ad5-74af622cd684" />

Flats located closer to MRT stations tend to have higher resale prices. The variable mrt_nearest_distance shows that properties with better transport accessibility often command a price premium.

<h2 align="center">Age of the Flat Matters </h2>

 <img width="1016" height="367" alt="Screenshot 2026-03-07 at 18 51 09" src="https://github.com/user-attachments/assets/afd02e56-06b1-48c5-82cf-8976b22a9864" />
 
Older flats with shorter remaining lease periods generally have lower resale prices. This highlights the importance of variables such as lease_commence_date and flat_age in predicting resale value.

<h2 align="center">Correlation Heatmap</h2>

<img width="590" height="523" alt="image" src="https://github.com/user-attachments/assets/c1f19c28-d83e-4cef-be0a-f313eead1b4e" />

Floor area shows the strongest positive relationship with resale price (0.65), indicating that larger flats command significantly higher prices. Flat age is negatively correlated with price (-0.35), suggesting older flats with shorter remaining leases tend to sell for less, while higher storey levels show a moderate positive impact on resale value.

***

3. Feature Engineering

Additional features created:
- remaining_lease = 99 - hdb_age
- region: Categorising planning_area according to the region in Singapore

These help capture housing quality and region area. 

***

4. Model Development

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

***

5. Model Evaluation


| | Linear Regression | RandomForest | XGBoost |
|---|---|---|---|
| R2 | 0.872 | 0.925 | 0.970 |
| RMSE | 51135.77 | 39160.78 | 24958.11|
| MAE | 36777.51 | 30155.43| 17942.72 |


The XGBoost model achieved the best overall performance across all evaluation metrics.

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

***

**Business Insights**

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

***

**Business Recommendations**

Real estate agents, buyers should prioritise:
<p>- larger flats with higher floor area
<p>- properties near MRT stations
<p>- flats in high-demand towns such as Queenstown and Bukit Merah
<p>- newer flats with longer remaining lease

These factors significantly influence resale value.

***

**Limitations**

<p>-5-years gap of data from 2026C
<p>-cannot account for human factors (proximity to family, jobs,vanity, good primary school, fengshui, inflation)
<p>-Data cannot capture government policies like homeimprovement programme and lift improvement programme
<p>-Model estimates fair market value but final transaction pricedepends on various factors such as listing strategy and marketliquidity

***

**Tech Stack**

<p>Python
<p>Pandas
<p>Scikit-learn
<p>Matplotlib / Seaborn
<p>Tableau

***

**Future Improvements**

Possible next steps:
<p>-Ask client for their priorities when it comes to purchasing
<p>-Provide price range instead of single point estimate (reducesrisk of overpricing and unrealistic seller expectations)
<p>-Develop a lease-adjusted pricing framework
<p>-Tailor marketing messaging by planning area

***

**Model Export**

Users input:
- floor_area_sqft
- remaining_lease_years
- mrt_nearest_distance
- storey
- town
