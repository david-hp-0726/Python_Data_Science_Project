# Emory Data Science Club Project
### Description
This project aims to study the influence of Covid-19 on mental health. Specifically, we want to answer the following questions.
1. Since the start of Covid-19, has there been an overall increase in the prevalence of mental health?
2. What socioeconomic factors have been correlated with mental health?
3. Which demographics have been the most vulnerable to mental health issues?


### Data Sources
- [Mental Health Data] from the Household Pulse Survey Conducted by Center for Disease Control 
- [Economic Indicators Data] from the Bureau of Economic Analysis 
- [Covid-19 Data] from New York Times

[Mental Health Data]: https://www.cdc.gov/nchs/covid19/pulse/mental-health.htm
[Economic Indicators Data]: https://www.bea.gov/itable/
[Covid-19 Data]: https://github.com/nytimes/covid-19-data 


# Code Book
![test](https://user-images.githubusercontent.com/120674894/218905515-7ec068d8-7468-4113-b30c-16fa3f3ecfe9.png)

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

# Plots & Tables
### Plot 1
![Plot 1](https://user-images.githubusercontent.com/120674894/209451176-704cd66f-3f29-4e52-92e5-051587c90121.png)

### Plot 2
![Plot 2](https://user-images.githubusercontent.com/120674894/209451178-c2d5a907-e701-4a57-9fc0-a5bf96c50cc9.png)

### Plot 3
![Plot 3](https://user-images.githubusercontent.com/120674894/209451190-2ceaa222-bd2f-431b-96d1-228468ac7533.png)

### Plot 4
![Plot 4](https://user-images.githubusercontent.com/120674894/209451194-4824d31f-5edb-461d-b3b9-5fde59c71819.png)

### Plot 5
![Plot 5](https://user-images.githubusercontent.com/120674894/209451196-34266eb9-cdb5-4780-8e8d-83839ec27957.png)

### Table 1
<img width="718" alt="Screen Shot 2022-12-24 at 1 22 14 PM" src="https://user-images.githubusercontent.com/120674894/209451316-7db9b566-ccb3-426a-9fdd-0f6875b5f26c.png">

### Table 2
<img width="690" alt="Screen Shot 2022-12-24 at 1 20 41 PM" src="https://user-images.githubusercontent.com/120674894/209451294-41974605-25b7-455d-b381-dc88b7d0f90b.png">

### Table 3
<img width="690" alt="Screen Shot 2022-12-24 at 1 19 26 PM" src="https://user-images.githubusercontent.com/120674894/209451275-d04eef73-eb53-4ff7-bc3d-17898941a05c.png">

# Next Tasks
1. Come up with more research questions
2. Add descriptions to the plots
3. Build statistics models for data (maybe?)

