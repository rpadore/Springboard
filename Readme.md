# Hospital inpatient bed occupancy predictor
Can we predict how many beds will need to be present for patients based off covid cases?

In 2020 the world got hit with something so unforseeable that it sent shockwaves around the world. We were unsure about our safety and those near us. The COVID-19 pandemic had hit the world and taken the lives of many around us. After receiving multiple different guidelines and precautions, many were still unsure as to how they would be able to recieve treatment for such a deadly virus. Hospitals were overfilled and there was no way to account for the amount of traffic that a hospital were to face. COVID did not stop in the path of the previous needs of the hospitals and many were forced to give up their beds in order to house patients who were in dire need of treatment. However with data I knew it was possible to help hospitals get a clearer outlook of how they would need to allocate their resources in order to provide for those in need. In this project I created a model to predict the amount of beds that a hospital would need to allocate in order to keep up with the case count.

## Data
The CDC is in charge of the disease control in the United States and took over the front line when the virus hit. They collected data on the cases and deaths present in every state across the United States and were in charge of making recommendations to citizens. I pulled in data off the CDC Website with the COVID Case count and death count in every state. The CDC was also storing hospital bed occupancy data and I was able to pull in the hospital ICU Bed occupancy as well as the inpatient bed occupancy data from the CDC website. 

![image](https://user-images.githubusercontent.com/69598569/157113781-73c9a0e1-ed72-46e6-a5da-8be76538099f.png)

## Method
I decided that we needed to perform a regression model in order to predict exactly how many beds we would need based on the date, the amount of cases and the icu occupancy. We would use the model that provided us the best predicting power and one that would have low error since hospitals would need a specific number in regards to their bed occupancy with such times.

## Data Cleaning
The data was collected from two different sources and therefore needed to be matched up on a key. This key would be the state as well as the date. We did not run into any null value problems since the data provided by the CDC was thorough and mostly clean. In order to parse our data through to the model we split up the date column in to the month and day column and since it was all in one year we dropped the year column. In regards to handling the state names we used a get dummies function in order to split this categorical data into numeric data to incorporate into our regression model.

## EDA
Covid cases were increasing at an alarming rate so we were aware that the cases and deaths would be highly related and the time would be correlated to the cases. New Jersey was leading the death count during our time period of study and California was leading the case count during the same period of time. 

Most of our data was skewed to the right as seen by the histogram plots of our data here. Therefore the data needed to be scaled in order to perform modeling.

![image](https://user-images.githubusercontent.com/69598569/157115489-136dd330-8917-4a7d-a8fb-bdabc1a30867.png)

There was a high correlation between cases and deaths as well as the ICU Bed occupancy and the inpatient bed occupany as portrayed by the heatmap here

![image](https://user-images.githubusercontent.com/69598569/157115657-40191b90-e95c-46eb-a661-e0f2e9a30940.png)

## ML and Algorithms

I decided to work with scikit learn library and incorporate three different machine learning algorithms. I used an OLS regressor model, a ridge regression model and a randomforest regressor model. 

Here we see the results of the OLS model
![image](https://user-images.githubusercontent.com/69598569/157117548-ce5160c1-bd3d-4655-a304-76826ac7a9d9.png)
We achieved a high score and the mean squared error was 0.02177872242733578. 

The randomforest regressor model also provided us with a very high rsquared value of 0.991758420741848, a MSE of 0.01235097215788602 and a RMSE of 0.00617548607894301.

The Ridge regressor received a r2 squared score of 0.9768725205675259 and a RMSE of 0.14770625972825185. 

Keeping these numbers in mind it was clear that the randomforest regressor had the best metrics and did a wonderful job of predicting the hospital bed occupancy based on the other factors present.

The hyperparameters for the randomforest regressor is showed as below

![image](https://user-images.githubusercontent.com/69598569/157118502-2e1ddea5-34e4-4cf7-b533-73c4dd874de4.png)

## Recommendations

I would recommend that we use this regressor in order to finance the budgets around the beds in order to allow for smoother business decisions with covid funds. Hospital managers can move beds and patients around in order to accomodate for the anticipated influx of patients should there be a new strain of the virus that would bring a lot of patients to the hospital

I would also recommend incorporating new covid 19 case data in order to get more accuracy with current developments regarding the virus.



