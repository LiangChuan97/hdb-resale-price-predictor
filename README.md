### 🏠 Predicting HDB Resale Prices in Singapore ###
***
**Project Overview**

This project develops a machine learning model to estimate Singapore HDB resale prices using housing characteristics, location data, and nearby amenities. Using historical transaction data, it identifies key price drivers such as floor area, MRT proximity, flat type, and flat age, providing a data-driven pricing reference for real estate agents when advising on listing and purchase decisions.

<p>The project includes:
	<p>• exploratory data analysis to identify price drivers
	<p>• feature engineering to capture housing and accessibility factors
	<p>• model comparison across multiple regression algorithms
	<p>• a Tableau dashboard for interactive market exploration

***

**Business Problem**

Agents often struggle to determine the correct listing price for HDB flats. By accurately estimating resale prices helps real estate agents:
	•	advise sellers on competitive listing prices
	•	help buyers determine fair market value
	•	identify undervalued investment opportunities.

***

**Dataset**

The dataset contains historical HDB resale transactions and property characteristics which was sourced from <a href = "https://www.kaggle.com/competitions/dsi-sg-project-2-regression-challenge-hdb-price/data"> kaggle </a> 

Target variable:

resale_price

Example features:
	•	town
	•	flat_type
	•	floor_area_sqm
	•	lease_commence_date
	•	mrt_nearest_distance
	•	hawker_nearest_distance
	•	mall_nearest_distance

The dataset also includes geographic coordinates and amenity proximity features.

⸻

Project Workflow

1. Data Cleaning

Steps performed:
- handled missing values by filling amenity count variables with 0 where appropriate
- checked for and verified absence of duplicated records
- removed irrelevant features to focus on location, transport, and amenity-related variables
- converted binary indicator columns (e.g., MRT and school affiliation variables) to boolean format
- ensured correct data types for numerical, categorical, and boolean variables
- validated transaction date fields by extracting year and month from 'Tranc_YearMonth'
- exported the cleaned dataset for further analysis and modelling

***

2. Exploratory Data Analysis (EDA)

Key questions explored:
	•	What factors influence HDB resale prices?
	•	How does flat size (floor area) affect resale price?
	•	Does proximity to MRT stations increase property value?
	•	Do nearby amenities such as malls and hawker centres impact prices?
	•	Does flat age or lease duration affect resale value?
	•	Are there price differences across towns or locations?
	•	How strongly are the features correlated with resale price?

These questions help identify the most relevant predictors for the resale price model.
	
New variables created:

Several new variables were created to better capture housing characteristics and accessibility factors.

Transaction Date Features

Extracted from Tranc_YearMonth:
	•	t_year – extracted transaction year
	•	t_month – extracted transaction month

These were used to validate the consistency of existing date columns.

Housing Characteristics

Derived variables used to better represent property age:
	•	flat_age
	•	remaining_lease

These help measure how the remaining lease affects property value.

Price-Based Metrics

Additional analytical variables were created:
	•	price_per_sqm

This standardises price relative to property size.

Visualisations include:
	•	resale price distribution
	•	floor area vs resale price
	•	resale price comparison by town
	•	distance to MRT by resale price
	•	correlation heatmap

The resale price of HDB flats varies significantly depending on:

Property Size Drives Price

Floor area is one of the strongest predictors of resale price. Larger flats generally command significantly higher prices, showing a clear positive relationship between floor_area_sqm and resale_price.

Location Plays a Major Role

Resale prices vary noticeably across towns and planning areas. Flats located in central or mature estates tend to have higher resale values compared to those in less central locations.

Accessibility to Public Transport

Flats located closer to MRT stations tend to have higher resale prices. The variable mrt_nearest_distance shows that properties with better transport accessibility often command a price premium.

Nearby Amenities Increase Property Value

Proximity to amenities such as shopping malls and hawker centres also appears to influence resale prices. Flats with more nearby amenities or shorter distances to these facilities tend to be more desirable.

Age of the Flat Matters

Older flats with shorter remaining lease periods generally have lower resale prices. This highlights the importance of variables such as lease_commence_date and flat_age in predicting resale value.

Geographic Location Effects

Latitude and longitude data indicate that resale prices cluster geographically, reinforcing the strong impact of location on housing prices.

These insights informed the feature selection and model development process for predicting HDB resale prices.

***

3. Feature Engineering

Additional features created:
	•	flat_age = transaction_year - lease_commence_date
	•	floor_area_sqft
	•	distance_to_mrt
	•	distance_to_hawker

These help capture housing quality and accessibility.

⸻

4. Model Development

To estimate HDB resale prices, several regression models were developed and compared.
The goal was to identify a model that could accurately predict resale prices while also providing insights into the factors influencing property values.

The modelling workflow included:
	•	selecting relevant housing and location features
	•	splitting the dataset into training and testing sets
	•	training multiple regression models
	•	evaluating model performance using prediction error

Model performance was evaluated using Root Mean Squared Error (RMSE), which measures the difference between predicted and actual resale prices.
RMSE measures the average difference between predicted resale prices and the actual transaction prices.
Lower RMSE values indicate that the model is making more accurate predictions.


Linear Regression (Baseline Model)

A Linear Regression model was first implemented as a baseline model.
This model assumes a linear relationship between housing features and resale price.

It provides a simple and interpretable starting point for understanding how factors such as:
	•	floor area
	•	remaining lease
	•	proximity to MRT stations
	•	location

affect resale prices.

While simple, this model helps establish a benchmark for comparing more advanced algorithms.

Random Forest Regressor

A Random Forest Regressor was trained to capture more complex relationships between housing characteristics and resale prices.

Random Forest combines many decision trees and averages their predictions, which helps improve prediction accuracy and reduce overfitting.

This model is particularly useful when relationships between variables are nonlinear, such as:
	•	the impact of location on price
	•	interactions between flat size and accessibility

XGBoost Regressor

An XGBoost Regressor was also implemented as an advanced machine learning model designed for strong predictive performance.

XGBoost builds trees sequentially, where each new tree improves on the errors of the previous one. This allows the model to capture subtle patterns in the data and often results in higher predictive accuracy.

The model was trained with tuned parameters to optimise performance on the resale price prediction task.

Top Features of resale price used in the Models

The models were trained using a combination of property characteristics, location data, and accessibility features, including:
	•	floor_area_sqft
	•	remaining_lease_years
	•	mrt_nearest_distance
	•	mid (storey level indicator)
	•	flat_model_tier
	•	town
	•	region
	•	bto_launched

These variables were selected based on insights obtained during the exploratory data analysis.

***

5. Model Evaluation


| | Linear Regression | RandomForest | XGBoost |
|---|---|---|---|
| R2 | 0.872 | 0.925 | 0.970 |
| RMSE | 51135.77 | 39160.78 | 24958.11|
| MAE | 36777.51 | 30155.43| 17942.72 |


The XGBoost model achieved the best overall performance across all evaluation metrics.

•	Highest R² (0.970)
This means the model explains 97% of the variance in HDB resale prices, indicating a very strong fit to the data.

•	Lowest RMSE (24,958)
RMSE measures the average magnitude of prediction errors.
Compared to the other models, XGBoost produces much smaller prediction errors, meaning its predicted prices are closer to the actual resale prices.

•	Lowest MAE (17,943)
MAE measures the average absolute difference between predicted and actual prices.
The lower MAE indicates that XGBoost consistently produces more accurate predictions.

Interpretation

The strong performance of XGBoost is likely due to its ability to:
	•	capture non-linear relationships between housing features and resale prices
	•	model interactions between variables such as floor area, location, and accessibility
	•	iteratively correct prediction errors through gradient boosting

As a result, XGBoost was selected as the final model for predicting HDB resale prices.

***

Business Insights

Major drivers of HDB resale prices include:
	1.	Floor area
	2.	Distance to MRT stations
	3.	Town/location
	4.	Flat type
	5.	Flat age

✔ Properties closer to MRT stations and located in central towns command higher prices.
✔ Larger flats command higher resale prices, with floor area being the strongest predictor.
✔ Flats within walking distance of MRT stations sell at a measurable premium.
✔ Central towns show consistently higher resale values than peripheral areas.


⸻

Business Recommendations

Real estate agents should prioritise:
	•	larger flats with higher floor area
	•	properties near MRT stations
	•	flats in high-demand towns such as Queenstown and Bukit Merah
	•	newer flats with longer remaining lease

Buyers should prioritise:
	•	larger flats with higher floor area
	•	properties near MRT stations
	•	flats in high-demand towns such as Queenstown and Bukit Merah
	•	newer flats with longer remaining lease

Agents should prioritise:
	•	larger flats with higher floor area
	•	properties near MRT stations
	•	flats in high-demand towns such as Queenstown and Bukit Merah
	•	newer flats with longer remaining lease


These factors significantly influence resale value.

⸻

Dashboard

An interactive dashboard was created using Tableau to explore:
	•	resale prices by location
	•	price trends over time
	•	impact of amenities on property value

⸻

Limitations

	•	macroeconomic factors not included
	•	renovation quality unknown
	•	school ranking effects not captured
	•	transaction data may lag market conditions

⸻

Tech Stack

Python
Pandas
Scikit-learn
Matplotlib / Seaborn
Tableau

⸻

Repository Structure

hdb-resale-price-predictor/
│
├── data/
├── notebooks/
├── models/
├── dashboard/
├── src/
├── images/
└── README.md

⸻

Future Improvements

Possible next steps:
	•	incorporate macroeconomic indicators
	•	build a web app for price prediction
	•	use gradient boosting models such as XGBoost
	•	apply SHAP analysis for model explainability

⸻

Model Export

Users input:
	•	town
	•	flat type
	•	floor area
	•	MRT distance

Conclusion:
