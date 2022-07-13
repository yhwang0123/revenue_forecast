# Project:forecast the revenue
A project to forecast the revenue of companies based on the previous financial data

### Team member:

* Yihui Wang  https://github.com/kaiyungtan
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
2. model_check.ipynb\
3. 

Workflow

### Step 1 : Data cleaning

The cleaning phase is a very significate process in this project. Only with a good data wrangling and cleaning, we can analysis the data efficiently. So, we explored the data and identified our need during the analysis phase, to drop the useless column and clean the usefull ones.

* normalize the json data
* select next_year revenue as target value
* select features based on the heatmap of correlation, and finalized features are ebit,net_added_value, and total_assets
* handle None and NaN values
#### Strategy we used to deal with missing value:
1. Fill with the median value of previous years
examples 1:
fill in the missing value of 2019 with the median value of 2015,2016,2017,2018




You have to handle categorical data.
You have to remove features that have too strong correlation.
You have to remove entries that are not relevant for training your model.

### Step 2: Data formatting

Now that the dataset is ready, you have to format it for machine learning:

Divide your dataset for training and testing. (X_train, y_train, X_test, y_test)

### Step 3: Model selection

The model we tested are as follows:
1. LinearRegression
2. Ridge 
3. Lasso
3. ElasticNet
4. KNeighborsRegressor
5. GradientBoostingRegressor
6. ExtraTreesRegressor
7. RandomForestRegressor
8. DecisionTreeRegressor
9. XGBRegressor\
The evaluation score are as shown as below:

Based on the score, we choose ExtraTreeRegressor, RandomForestRegressor and DecisionTreeRegressor, as they make the most sense according to your data.

### Step 4: Apply your model

Train your model and apply it on your data.

## Step 5: Fine-tune the model


## Step 6: Model evaluation

Let's evaluate your model. You first need to select the best metrics according to your usecase. Then you can compute the score of your model on your test set.

1. R

Try to answer those questions:

How could you improve this result?
Which part of the process has the most impact on the results?
Do our model avoid overfitting?