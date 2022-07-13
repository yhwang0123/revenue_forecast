# Project:forecast the revenue
A project to forecast the revenue of companies based on the previous financial data

### Team member:

* Yihui Wang  https://github.com/yhwang0123
* Chaitali Sonawane https://github.com/Chaitali1290
* Soukaina Ait hammou  https://github.com/soukiait


## Project Summary
Mission: create a Machine Learning model to predict the company's revenue for current year based on historical data (the 5 past annual reports).

### Objectives:

- [x]Be able to preprocess data for machine learning.
- [x]Be able to train, apply and evaluate a regression model with real-world data.


### Dataset: 
a dataset with more than 50.000 entries provided by the client


### Files in this repo
1. data_clean.ipynb\
file for data exploring, wrangling and cleaning, and get the final dataset for training
2. model_selection.ipynb\
try diferent regression model, and choose based on their r2 score
3. Final_model.ipynb\
fine tune the final model for training

### Workflow for this project

#### Step 1 : Data cleaning

The cleaning phase is a very significate process in this project. Only with a good data wrangling and cleaning, we can analysis the data efficiently. So, we explored the data and identified our need during the analysis phase, to drop the useless column and clean the usefull ones.

* normalize the json data
* select next_year revenue as target value
* select features based on the heatmap of correlation, and finalized features are ebit,net_added_value, and total_assets
* use melt and pivot to transform the dataset to proper form for the training
![alt text](https://github.com/yhwang0123/revenue_forecast/blob/yihui/asset/example3.png)
* handle None and NaN values
* remove features that have too strong or similar correlation,like ebit with operating_profit_and_loss, total_assets with total_liabilities
* remove entries that are not relevant for training your model

##### Strategy we used to deal with missing values:
1. Fill with the median value of previous years
fill in the missing value of 2019 with the median value of 2015,2016,2017,2018
![alt text](https://github.com/yhwang0123/revenue_forecast/blob/yihui/asset/example1.png)

2. Fill in the missing value of median based on company_category, province, and nace_code, and year
![alt text](https://github.com/yhwang0123/revenue_forecast/blob/yihui/asset/example2.png)

3. remove all the 6-year nan value in revenue
4. remove rows if there are missing values in next_year_revenue(as this will be target)

#### Step 2: Data formatting

* Performing data scaling to avoid extreme data
* Divide your dataset for training and testing. (X_train, y_train, X_test, y_test)

#### Step 3: Model selection

The model we tested are as follows:

1. LinearRegression
2. KNeighborsRegressor
3. DecisionTreeRegressor
4. XGBRegressor
5. RandomForestRegressor
6. Lasso
7. ExtraTreesRegressor

Based on the evaluation score (r2 score and mean_absolute_error), we choose ExtraTreeRegressor, RandomForestRegressor and DecisionTreeRegressor, as they make the most sense according to your data.

#### Step 4: Apply your model

* We tested with three regressor and train our model on your data.

#### Step 5: Fine-tune the model

1. Feature importance
* we checked the features importance of the each model, and found current_revenue is too strong in feature importance. As there are a lot of missing value in current_revenue, and we have filled them with median,then they become artificial data, which will influence the accuracy of our model, so we improve our dataset by droping current_revenue.

2. Hyperparamenter tuning
* we used the GridSearchCV to find the best parameter of each model, with checking the performance on training and test set


#### Step 6: Model evaluation

we use maily two metrics to evaluate our model. 

1. R squared score (0.88 for ExtraTreesRegressor )
2. Cross validation (0.66 for ExtraTreesRegressor)

Based on the score we have, we finally select ExtraTreesRegressor as our model to do the prediction.

