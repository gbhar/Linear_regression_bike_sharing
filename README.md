# Bike Sharing Assignment

> This assignment is a programming assignment wherein you have to build a multiple linear regression model for the prediction of demand for shared bikes. You will need to submit a Jupyter notebook for the same. 


## Table of Contents
* [General Info](#general-information)
* [Technologies Used](#technologies-used)
* [Conclusions](#conclusions)
* [Acknowledgements](#acknowledgements)

<!-- You can include any other section that is pertinent to your problem -->

## General Information
- A bike-sharing system is a service in which bikes are made available for shared use to individuals on a short term basis for a price or free. Many bike share systems allow people to borrow a bike from a "dock" which is usually computer-controlled wherein the user enters the payment information, and the system unlocks it. This bike can then be returned to another dock belonging to the same system.
-A US bike-sharing provider **BoomBikes** has recently suffered considerable dips in their revenues due to the ongoing Corona pandemic. The company is finding it very difficult to sustain in the current market scenario. So, it has decided to come up with a mindful business plan to be able to accelerate its revenue as soon as the ongoing lockdown comes to an end, and the economy restores to a healthy state. 
- we have required to model the demand for shared bikes with the available independent variables. It will be used by the management to understand how exactly the demands vary with different features. They can accordingly manipulate the business strategy to meet the demand levels and meet the customer's expectations. Further, the model will be a good way for management to understand the demand dynamics of a new market. 
- You can observe in the dataset that some of the variables like 'weathersit' and 'season' have values as 1, 2, 3, 4 which have specific labels associated with them (as can be seen in the data dictionary). These numeric values associated with the labels may indicate that there is some order to them - which is actually not the case (Check the data dictionary and think why). So, it is advisable to convert such feature values into categorical string values before proceeding with model building. Please refer the data dictionary to get a better understanding of all the independent variables.
 You might notice the column 'yr' with two values 0 and 1 indicating the years 2018 and 2019 respectively. At the first instinct, you might think it is a good idea to drop this column as it only has two values so it might not be a value-add to the model. But in reality, since these bike-sharing systems are slowly gaining popularity, the demand for these bikes is increasing every year proving that the column 'yr' might be a good variable for prediction. So think twice before dropping it

## Conclusions
- Conclusion 1 from the Feature analysis
  - instant: record index This column acts just as serieal number and is thus redundant. it will be dropped in next step.
- dteday : date as in data we have been given the day of week, month, year, holiday data in seperate columns. so I will dropped the next step.
	- season : season (1:spring, 2:summer, 3:fall, 4:winter) This feature will be converted to season names so that proper dumies can be created.
	- yr : year (0: 2018, 1:2019) this column signifies the boolean form as inicated.
	- mnth : month ( 1 to 12) this feature will be converted into month name so that proper dumies can be created.
	- holiday : weather day is a holiday or not (extracted from http://dchr.dc.gov/page/holiday-schedule) this is a binary variable
	- weekday : day of the week This feature will be converted to weekday names so that proper dumies can be created.
	- workingday : if day is neither weekend nor holiday is 1, otherwise is 0. This variable is an extract of holiday and weekday. during the course of assignment, post visualization, reasearcher will decide on transforming this column further if required.
	+ weathersit : This feature will be converted to weathersit names so that proper dumies can be created.
		- 1: Clear, Few clouds, Partly cloudy, Partly cloudy
		- 2: Mist + Cloudy, Mist + Broken clouds, Mist + Few clouds, Mist
		- 3: Light Snow, Light Rain + Thunderstorm + Scattered clouds, Light Rain + Scattered clouds
		- 4: Heavy Rain + Ice Pallets + Thunderstorm + Mist, Snow + Fog
	- temp : temperature in Celsius
	- atemp: feeling temperature in Celsius
	- hum: humidity
	- windspeed: wind speed
	- cnt: count of total rental (casual + registered) bikes including both casual and registered (This Target Variable)
- Conclusion 2 from the Categorical analysis
- Conclusion 3 from the Numerical Variable analysis
	- There is linear relationship between temp and atemp. Both of the parameters cannot be used in the model due to multicolinearity. We will decide which parameters to keep based on VIF and p-value w.r.t other variables
 	- All the parameters have increased values in 2019 compared to 2018. Thus, year may become a key paratemeter in the model
- Conclusion 4 from the Building the Linear Model analysis
	- **Model 1:** Both temp and atemp has high VIF but atemp has high p-value additionally. We will go ahead with dropping atemp from the equation
 	-  **Model 2:** As workingday has the highest VIF value, we will remove the variable next.
  	-  **Model 3:** Next we will remove hum as it has high VIF.
  	-  **Model 4:** Next we will remove clear to Partly Cloudy as it has high VIF.
  	-  **Model 5:** let's remove Sat due to high p-value.
  	-  **Model 6:** remove holiday due to high p-value.
  	-  **Model 7:** This model looks good, as there seems to be VERY LOW Multicollinearity between the predictors and the p-values for all the predictors seems to be significant. For now, we will consider this as our final model (unless the Test data metrics are not significantly close to this number).
 -  Conclusion 5 from Model Validation analysis.
 	- Linear Relationship : The above plots represents the relationship between the model and the predictor variables. As we can see, linearity is well preserved
	- Homoscedasticity: 
	- Absence of Multicollinearity: All the predictor variables have VIF value less than 5. So we can consider that there is insignificant multicolinearity among the predictor variables. 
	- Normality of Errors: Based on the histogram, we can conclude that error terms are following a normal distribution
 - Conclusion 6 Overall Summary.
As high temperature and good weather positively impacts bike rentals, it is recommended that bike availability and promotions to be increased during summer months to further increase bike rentals.
## Technologies Used
- library - version 1.0
	- import numpy as np
 	- import pandas as pd
	- import matplotlib.pyplot as plt
	- import seaborn as sns 
- library - version 2.0
	- from sklearn.model_selection import train_test_split
	- from sklearn.preprocessing import MinMaxScaler
   	- from sklearn.linear_model import LinearRegression
	- from sklearn.feature_selection import RFE
	- from sklearn.metrics import r2_score
- library - version 3.0
	- from sklearn.model_selection import train_test_split
	- from sklearn.preprocessing import MinMaxScaler
	- from sklearn.linear_model import LinearRegression
	- from sklearn.feature_selection import RFE
	- from sklearn.metrics import r2_score

## Acknowledgements
We would like to extend our gratitude and give credit to the UpGrade institution, various sources like UpgGrad institution,   that contributed to the success of the "Housing Price Prediction" project:



## Contact
Created by [[@githubusername](https://github.com/gbhar)] - feel free to contact me!


<!-- Optional -->
<!-- ## License -->
<!-- This project is open source and available under the [... License](). -->

<!-- You don't have to include all sections - just the one's relevant to your project -->
