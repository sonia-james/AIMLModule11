# AIMLModule11
# Introduction:

The goal of this analysis was to predict the price of used cars based on various features available in the dataset. The dataset contains features such as year, mileage, and other relevant characteristics of the cars. Our primary focus was to evaluate how different factors impact the price of used cars and assess the performance of linear and ridge regression models in predicting car prices.

# Data Preparation and Preprocessing:

## Data Exploration:**
* Explored data :
  Analysed and explored the data set and tried to understand the domain and business usecase. 
* Analyze Missing Values:
  Identified missing values in the odometer column, which were replaced by the mean odometer reading for each car year. We also checked for other missing values across the dataset and dropped irrelevant columns (id, VIN, size) that contained excessive missing data or were non-predictive.
* Converted Columns to Appropriate Types: Convert object etc types to appropriate type
* Handled missing data : Applied multiple ways to handle missing data. State utilized region data for missing value. Ordinal fields like condition/cylinders were set with 'unknown' tag for null values. Columns with large amount of missing date were dropped from analysis. Transmission column had 77% automatic value, this was set to null as well. For missing odometer, the mean of the mileage from corresponding year was used. 
* Check for Outliers:
To detect outliers, visualized key features (price, odometer, year) using box plots. Outliers were identified as values that fell outside the typical range, such as unusually high prices or mileage. Q1-1.5 IQR --- Q3+1.5 IQR was applied on price column to exclude outliers. 
These preprocessing steps ensured the dataset was clean, with missing values and outliers appropriately handled, making it ready for model building.
* Feature Engineering and Encoding:
Categorical Encoding: Used One-Hot Encoding and James-Stein encoding to encode categorical values to numerical columns. Ordinal fields like conditions, cylinders were encoded with 1,2,3,4.
* Scale data : Used StandardScalar() for scaling the data

# Model Building:

## Created two models to predict the price of used cars:

* Linear Regression:
A linear regression model was created to predict car prices using all the features. The linear regression algorithm assumes a linear relationship between the input features and the target price.
The model was trained and evaluated using cross-validation to ensure a robust assessment.
* Ridge Regression:
To address potential multicollinearity issues (where features might be correlated with each other), we used Ridge Regression. This model applies L2 regularization to prevent overfitting by shrinking the coefficients of correlated features.
We performed hyperparameter tuning using GridSearchCV to find the optimal value of alpha, which controls the strength of the regularization.

The models were evaluated using various metrics, including the Mean Squared Error (MSE) and R-squared (R²). Here's a summary of the performance evaluation:

**Linear Regression Model:**
MSE (Mean Squared Error): The MSE was calculated to measure the average squared difference between the observed actual outcomes and the model's predictions.
R² (R-squared): The R² score tells us how well the model explains the variance in the data. A higher R² value indicates a better fit of the model to the data. \
MSE = 60856811.91417967 \
R² = 62.776 \
**Ridge Regression Model:**
MSE and R²: After tuning the alpha hyperparameter using GridSearchCV, the Ridge regression model performed similarly to the linear regression model but with a slightly better ability to generalize to unseen data due to the regularization effect.
The optimal value of alpha was found to be around 10, indicating a good balance between fitting the data and controlling overfitting. \
MSE = 64721814.32004122 \
R² = 60.41

These models can be used to predict the price for a new car with given features. 

# Key Insights:

* Observed a positive correlation between the year and price: As the year of a car increases, so does its price. This suggests that newer cars generally have a higher value compared to older cars.
* Noticed a negative correlation between mileage and price: As the mileage (or odometer reading) increases, the price of the car tends to decrease. This aligns with the intuition that cars with more miles driven are generally worth less.
* Cars in better condition has higher demand
* Clean title status has high demand among customers than others
* Type of car sedan/suv also impacts the price of the car

# Conclusion:

## Based on the analysis and model evaluations, the following conclusions can be drawn:

* The relationship between year and price, as well as between mileage and price, is consistent with real-world intuition and is well captured by both the linear and ridge regression models.
* Similar key insigts were drawn on mileage, condition , title_status, type etc to affect the price of the car
* While both models performed well, the Linear regression model provided slightly better results, making it more robust for this dataset.
* The model could be used to predict plausible selling price for a car 
* Future improvements could involve exploring additional features (model) and experimenting with other regression models, such as Lasso or ElasticNet, which might offer further enhancements in predictive performance.

## Recommendations for Further Analysis:
* Feature Expansion: Incorporating additional features such as the car model, could improve the predictive power of the models.
* Better Preparation: We could involve better handling for null values with more advanced techniques which could improve the overall quality of the data set. 
* Model Refinement: Experimenting with more advanced machine learning algorithms, such as decision trees or ensemble methods (Random Forest, Gradient Boosting), could provide a more complex and potentially higher-performing model.
* Outlier Detection: Further analysis on outliers in car prices and mileage could help improve model accuracy, as extreme values could skew predictions.
