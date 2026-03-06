:::writing{variant=“standard” id=“read1”}

🏠 Predicting HDB Resale Prices in Singapore

Project Overview

This project develops a machine learning model to estimate HDB resale prices using property attributes, location features, and nearby amenities. The analysis identifies key price drivers such as floor area, MRT proximity, and flat age. The resulting predictive model provides agents with a data-driven tool to estimate fair market prices and support better real estate decisions.

⸻

Business Problem

Agents often struggle to determine the correct listing price for HDB flats.
This project builds a predictive model that estimates resale value and identifies key factors affecting pricing.

The resale price of HDB flats varies significantly depending on:
	•	location
	•	flat size
	•	floor level
	•	lease age
	•	proximity to MRT stations
	•	nearby amenities such as malls and hawker centres

Accurately estimating resale prices helps real estate agents:
	•	advise sellers on competitive listing prices
	•	help buyers determine fair market value
	•	identify undervalued investment opportunities.

⸻

Dataset

The dataset contains historical HDB resale transactions and property characteristics.

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
	•	handled missing values and duplicated records
	•	removed irrelevant features
	•	converted categorical variables
	•	ensured correct data types

New variables created:
	•	flat_age
	•	price_per_sqm
	•	distance-based features

⸻

2. Exploratory Data Analysis (EDA)

Key questions explored:
	•	Which towns have the highest resale prices?
	•	Does larger floor area significantly increase price?
	•	Do flats near MRT stations sell at higher prices?

Visualisations include:
	•	resale price distribution
	•	correlation heatmap
	•	price vs floor area
	•	price vs MRT distance
	•	price comparison by town

⸻

3. Feature Engineering

Additional features created:
	•	flat_age = transaction_year - lease_commence_date
	•	floor_area_sqft
	•	distance_to_mrt
	•	distance_to_hawker

These help capture housing quality and accessibility.

⸻

4. Model Development

Several regression models were tested:
	•	Linear Regression
	•	Random Forest
	•	XGBoost

Feature importance chart:

Top predictors of resale price

1 Floor area
2 MRT distance
3 Town
4 Flat type
5 Flat age

Evaluation metric:

RMSE (Root Mean Squared Error)

⸻

5. Model Performance

Best model:

Random Forest Regressor

Example performance:

RMSE ≈ 38,000 SGD

The model demonstrates strong predictive capability for resale prices.

⸻

Key Insights

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
