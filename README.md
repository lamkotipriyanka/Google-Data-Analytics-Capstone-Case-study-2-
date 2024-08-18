# Google-Data-Analytics-Capstone-Case-study-2
# How can a Wellness Technology Company play it smart? - Bellabeat
#### Author - Priyanka Lamkoti,
#### Date : 15 August, 2024
_The data analysis process consists of the following steps:_
### Step 1 - ASK 
### Step 2 - PREPARE
### Step 3 - PROCESS
### Step 4 - ANALYZE
### Step 5 - SHARE
### Step 6 - ACT
#### Scenario : Urška Sršen and Sando Mur founded Bellabeat, a high-tech company that manufactures health-focused smart products.Since it was founded in 2013, Bellabeat has grown rapidly and quickly positioned itself as a tech-driven wellness company for women.By 2016, Bellabeat had opened offices around the world and launched multiple products. The 5 bellabeat products are Bellabeat app, Time,Spring,Leaf,Bellabeat membership. Our team has been asked to focus on one of Bellabeat’s products and analyze smart device data to gain insight into how consumers are using their smart devices.
# 1. ASK 
### Business Task : Analyze the FitBit Fitness Tracker Data to gain insights on bellabeat products and help guide marketing strategy with recommendations to grow as a global player .
#### Primary stakeholders : Urška Sršen and Sando Mur,executive team members
#### Secondary stakeholders: Bellabeat marketing analytics team
# 2. PREPARE 
#### Source : FitBit Fitness Tracker Data (CC0: Public Domain, dataset made available through Mobius): This Kaggle data set contains personal fitness tracker from 30 fitbit users.
#### This dataset has 18 CSV files. It follows ROCCC:
#### 1. R for Reliability :Reliability: The data is from 30 FitBit users who consented to the submission of personal tracker data and generated by from a distributed survey via Amazon Mechanical Turk.
#### 2. O for Original : The data is from 30 FitBit users who consented to the submission of personal tracker data via Amazon Mechanical Turk.
#### 3. C is for Comprehensive : Data minute-level output for physical activity, heart rate, and sleep monitoring. While the data tracks many factors in the user activity and sleep, but the sample size is small and most data is recorded during certain days of the week.
#### 4. Another C is for urrent :Data is from March 2016 to May 2016.
#### 5. Last C is for Cited : Unknown.
#### Limitations : 1. Data for only 30 people is available. A larger sample size is preferred for the analysis.

# 3. PROCESS
#### First we import our zip file into our R cloud(Posit cloud), make a new R script and start cleaning our data. To do so we first import 3 csv file datasets: daily_activity, sleep_day, weight. Installing packages and loading it is our next step.
```
install.packages('tidyverse')
library(tidyverse)
install.packages('here')
library(here)
install.packages('skimr')
library(skimr)
install.packages('janitor')
library(janitor)
install.packages('dplyr')
library(dplyr)
```
#### We find the NA values in the columns for daily_activity and sleep_day and eliminate them. We also find the missing or duplicate values and do some transformations to bring the datset into a correct format.
```
dim(sleep_day)
sum(is.na(sleep_day))
sum(duplicated(sleep_day))
sleep_day <- sleep_day[!duplicated(sleep_day), ]
```

#### Next we combine the sleep_day and daily_activity into a single combined_data and then merge this with the weight data to form merged_data.
```
merged_data <- merge(merged_activity_sleep, weight, by = c("Id"), all=TRUE)
```
#### Visualization helps non-technical users understand our data easier.
![scatter plot case study](https://github.com/user-attachments/assets/a908b0bb-1454-4c7c-9308-2c0c1fdbb63a)

![2nd plot- scatterplot](https://github.com/user-attachments/assets/ccb371ff-48d8-44ff-ac0a-4ee0bcb11621)

# 4.ANALYZE
#### Summary - We get to check the 1st quartile ,median ,mean, median, minimum, maximum,3rd quartile, NAs etc. 
```
merged_data %>%
dplyr::select(Weekday,
              TotalSteps,
              TotalDistance,
              VeryActiveMinutes,
              FairlyActiveMinutes,
              LightlyActiveMinutes,
              SedentaryMinutes,
              Calories,
              TotalMinutesAsleep,
              TotalTimeInBed,
              WeightPounds,
              BMI
) %>%
  summary()
```
#### Next we plot a Pie chart to display Activity level minutes:
![newplot](https://github.com/user-attachments/assets/b92de514-e3cc-4acc-b676-80136e44c93b)
Most users spent 81.3% of their daily activity in sedentary minutes and only 1.74% in very active minutes.






