# Project:forecast the revenue
A project to forecast the revenue of companies based on the previous financial data

### Team member:

* Yihui Wang  https://github.com/yhwang0123
* Chaitali Sonawane https://github.com/Chaitali1290
* Soukaina Ait hammou  https://github.com/soukiait


## Project Summary
Mission: create a Machine Learning model to predict the company's revenue for current year based on historical data (the 5 past annuel reports).

#### Objectives:

- [x]Using Pandas for data manipulation.
- [x]Using MatplotLib and/or Seaborn for plotting.
- [x]Finding and understanding correlations between dataset's variables.

#### Dataset: 
a dataset with more than 50.000 entries provided by the client


### Files in this repo
1. data_clean.ipynb\
file for data exploring, wrangling and cleaning, and get the final dataset for training
2. model_selection.ipynb\
try diferent regression model, and choose based on their r2 score
3. Final_model.ipynb\
fine tune the final model for training

## Workflow

### Step 1 : Data cleaning

The cleaning phase is a very significate process in this project. Only with a good data wrangling and cleaning, we can analysis the data efficiently. So, we explored the data and identified our need during the analysis phase, to drop the useless column and clean the usefull ones.

* normalize the json data
* select next_year revenue as target value
* select features based on the heatmap of correlation, and finalized features are ebit,net_added_value, and total_assets
* handle None and NaN values

- Strategy we used to deal with missing value:
1. Fill with the median value of previous years
fill in the missing value of 2019 with the median value of 2015,2016,2017,2018
![alt text](https://github.com/yhwang0123/revenue_forecast/blob/yihui/asset/fill_example2.png)
2. Fill in the missing value of median based on company_category, province, and nace_code, and year
![alt text](https://github.com/yhwang0123/revenue_forecast/blob/yihui/asset/fill_example2.png)

* remove features that have too strong correlation
* remove entries that are not relevant for training your model
* use melt and pivot to transform the dataset to proper form for the training

### Step 2: Data formatting

* Divide your dataset for training and testing. (X_train, y_train, X_test, y_test)

### Step 3: Model selection

The model we tested are as follows:

1. LinearRegression
2. KNeighborsRegressor
3. DecisionTreeRegressor
4. XGBRegressor
5. RandomForestRegressor
6. Lasso
7. ExtraTreesRegressor

The evaluation score (r2 score and mean_absolute_error) we choose ExtraTreeRegressor, RandomForestRegressor and DecisionTreeRegressor, as they make the most sense according to your data.

### Step 4: Apply your model

* Train your model and apply it on your data.

## Step 5: Fine-tune the model


## Step 6: Model evaluation

we use several metrics to evaluate our model. 

1. R squared score
2. Cross validation

