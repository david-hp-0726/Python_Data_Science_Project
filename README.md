# Emory Data Science Club Project
### Description
This project aims to study the influence of Covid-19 on mental health. Specifically, we want to answer the following questions.
1. Since the start of Covid-19, has there been an overall increase in the prevalence of mental health?
2. What are some variables that can predict trends in national mental health?


### Data Sources
- [Mental Health Data] from the Household Pulse Survey Conducted by Center for Disease Control 
- [Economic Indicators Data] from the Bureau of Economic Analysis 
- [Covid-19 Data] from New York Times

[Mental Health Data]: https://www.cdc.gov/nchs/covid19/pulse/mental-health.htm
[Economic Indicators Data]: https://www.bea.gov/itable/
[Covid-19 Data]: https://github.com/nytimes/covid-19-data 


# Code Book
Data are collected from multiple sources, cleaned up, and compiled into the following [datasets](https://github.com/david-hp-0726/Python_Data_Science_Project/blob/main/Data%20Overview.ipynb). 

### Mental Health Data
|Variable Name|Description|
|:-----:|:-----|
|***State***|The state's name|
|***Date***|The month when data was recorded|
|***Grouping Method***|How observations are grouped|
|***Group***|The group the data belongs to|
|***Pct_Anxiety***|Percentage of adults who reported symptoms of generalized anxiety disorder|
|***Pct_Depression***|Percentage of adults who reported symptoms of major depressive disorder|
|***Pct_Anxiety_Or_Depression***|Percentage of adults who reported symptoms of generalized anxiety disorder or major depressive disorder|

### Merged Data (Mental Health Data & Economic Indicators Data)
|Variable Name|Description|
|:-----:|:-----|
|***State***|The state's name|
|***Date***|The month when data was recorded|
|***Fips***|Fips code of the state|
|***Population***|The population size of the state|
|***Pct_Anxiety***|Percentage of adults who reported symptoms of generalized anxiety disorder|
|***Pct_Depression***|Percentage of adults who reported symptoms of major depressive disorder|
|***Pct_Anxiety_Or_Depression***|Percentage of adults who reported symptoms of generalized anxiety disorder or major depressive disorder|
|***New_Cases***|Total number of new covid cases in the specified month|
|***New_Deaths***|Total number of new covid deaths in the specified month|
|***Cum_Cases***|Cumulative number of covid cases|
|***Cum_Deaths***|Cumulative number of covid deaths|
|***Pct_Infection***|Percent of the state's population|
|***Gdp_Change***|Percent change in gdp from the preceding period|
|***Income_Change***|Percent change in **per-capita** personal income from the preceding period|
|***Adjusted_Income_Change***|Percent change in seasonally adjusted **per-capita** personal income from the preceding period|
|***Farm_Income_Change***|Percent change in **total** income generated in farm sectors from the preceding period|
|***Nonfarm_Income_Change***|Percent change in **total** income generated in nonfarm sectors from the preceding period|
|***Pct_Unemployed***|Percent of the labor force unemployed|

### Policy Data
|Variable Name|Description|
|:-----:|:-----|
|***State***|The state's name|
|***Date***|The month when data was recorded|
|***Policy***|The covid-19 related policy introduced|
|***Policy_Category***|The type of policy introduced|
|***Policy_Stage***|Whether the policy starts or terminates|

# Discussion
## Question 1: Since the start of Covid-19, has there been an increase in mental health?
A line chart is created to model the trend in major depressive disorder and general anxiety disorder. While chart reveals significant fluctuations in national percentage of adults reporting mental symptoms, overall there does not appear to be a clear in crease or decrease. This is further supported by the result from a two-sample z-test revealing no statistical significant difference between pre- and post-covid mental health prevalence.

#### Plot 1: National Mental Health Since Covid-19
![health_us](https://user-images.githubusercontent.com/120674894/218907174-7f591a90-d062-4404-af98-cbda0534a771.png)

#### Table 1: Z-test Comparing Percentage of Adults Reporting Mental Health Symptoms Pre & Post Covid
<img width="718" alt="Screen Shot 2022-12-24 at 1 22 14 PM" src="https://user-images.githubusercontent.com/120674894/209451316-7db9b566-ccb3-426a-9fdd-0f6875b5f26c.png">

## Question 2: What are some variables that can predict trends in national mental health?
### Model Selection: XGBoost (Extreme Gradient Boosting)
For the purpose of this question, a XGBoost model was created. XGBoost is a supervised learning algorithm well-suited for performing regression analysis on time-series data. The model is applied separate to each US state, with 75% of data used for training and 25% of data used for validation. The following plots are created using data from the state of New York. 

#### Plot 2: Train Test Data Distribution
![data_distribution](https://user-images.githubusercontent.com/120674894/218908822-8a746a09-8473-477c-a258-1198558374ba.png)


### Important Features
The top-4 relevant variables identified by the model are percent employment, number of daily new deaths, number of daily new cases, and quarterly gdp change. Scatter plots are created to better visualize the relationship between these variables and mental health, with the features on the x axis and the target variable on the y axis. 

#### Plot 3: Feature Importances
![feature_importances](https://user-images.githubusercontent.com/120674894/219057099-7f04e3a7-05b8-47d0-b5f6-b3366a43cc89.png)

#### Plot 4: Correlations between Features and Target Varialbe
![feature_scatter](https://user-images.githubusercontent.com/120674894/219057791-eaba97cb-3d06-43f3-a702-b726222be29f.png)


### Model Performance
The model had been manually tuned to optimize performance. The plots below compares the actual data with the model's predictions. As revealed by the plot, while the model seems to perform reasonably well on the training data, its predictions on the test data are not as accurate. In fact, the mean-square error of predictions on the validation data is 1.17 greater than predictions on the training data.

#### Plot 5: Predictions on Training & Testing Data
![predictions_both](https://user-images.githubusercontent.com/120674894/218911006-3bccf1fb-af63-4e07-bf11-e242fd37e230.png)

#### Plot 6: Predictions on Training Data
![predictions_train](https://user-images.githubusercontent.com/120674894/218911083-c70d8266-36ee-4db0-8918-4080f6115c9a.png)

#### Plot 7: Predictions on Testing Data
![predictions_test](https://user-images.githubusercontent.com/120674894/218911092-af674e55-507e-409e-9841-7f7f1b3185e1.png)


## Model Analysis 
### 1. How did the model performance in terms of prediction accuracy?
#### Plot 8: Model Performance on Training Data
![performance_train](https://user-images.githubusercontent.com/120674894/227739391-2575e565-7e59-40f2-9cfa-0bfa12443271.png)

#### Plot 9: Model Performance on Validation Data
![performance_test](https://user-images.githubusercontent.com/120674894/227739394-22ca8bcd-c5ce-4008-b315-8ef1557ad589.png)

### 2. What are the most important features, or the most relevant factors to predicting mental health trends?
#### Plot 10: Relative Importance of Variables
![overall_feature_importances](https://user-images.githubusercontent.com/120674894/227739400-bf1b407d-06a8-4fd9-8723-e76458f420a7.png)

### 3. What are some factors that influence model performance?
### Learning Rate
#### Plot 11: Model Performance under Different Learning Rates
![performance_learning_rate](https://user-images.githubusercontent.com/120674894/228962677-79c7cb81-c428-42dd-a756-6dd1e889f718.png)

### Train-Test Ratio
#### Plot 12: Model Performance under Different Train-Test Ratios
![performance_train_test_ratio](https://user-images.githubusercontent.com/120674894/228962693-8085f505-e442-4c2c-b880-cd6d1165f9b2.png)

### Stationarity
#### Plot 17: Model Performance on Stationary vs Nonstationary Data
![performance_stationarity](https://user-images.githubusercontent.com/120674894/228962749-ef80871c-e261-4c63-bfc3-6fe104014515.png)


## Question 3: Which demographics have been worst influenced by mental health issues?
To answer this question, data is divided into categories based on the variables of interest (i.e. age, sex, education level, disability status). Line plots are created to visualize how mental health trends differ for different subgroups.

#### Plot 13: Mental Health Trend Grouped by Age
![health_age](https://user-images.githubusercontent.com/120674894/218912211-7ab70a16-cd68-4780-9d22-9fc64ac51204.png)

#### Plot 14: Mental Health Trend Grouped by Sex
![health_sex](https://user-images.githubusercontent.com/120674894/218912221-e6ac1330-0424-4314-919a-3491d84cc96c.png)

#### Plot 15: Mental Health Trend Grouped by Education Level
![health_education](https://user-images.githubusercontent.com/120674894/218912238-fba167ef-b347-47ef-852b-e329caacc360.png)

#### Plot 16: Mental Health Trend Grouped by Disability Status
![health_disability](https://user-images.githubusercontent.com/120674894/218912252-f09c5601-d778-45f1-97cd-c06ee0095c48.png)


# Limitations
There are several limitations to this study that need to be acknowledged. First, the entirely analysis is based on data gathered from a rather short period of only two years. This largely reduces the reliability of our result. Moreover, the majority time-series data is highly nonstationary, meaning that the data fluctuate with no observable pattern. This could mean that there are some larger trends aside from Covid-19 that affect the prevalence of mental health issues that can only be identified through analysis on long spans of time, such as economic growth and social sentiment. Due to limited data, our analysis might not capture such trends. 

#### Table 2
<img width="690" alt="Screen Shot 2022-12-24 at 1 20 41 PM" src="https://user-images.githubusercontent.com/120674894/209451294-41974605-25b7-455d-b381-dc88b7d0f90b.png">

#### Table 3
<img width="690" alt="Screen Shot 2022-12-24 at 1 19 26 PM" src="https://user-images.githubusercontent.com/120674894/209451275-d04eef73-eb53-4ff7-bc3d-17898941a05c.png">
