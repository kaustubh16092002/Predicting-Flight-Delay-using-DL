# Predicting-Flight-Delay-using-DL

## 1. Planning and preparation
The first stage is to generate ideas on where we may look for the data that foretells the aforementioned scenario. I map the motives and prospective information using the table below. [] (https://github.com/ryanhao1115/DL Predict Flight Delays/blob/main/p2.png)
I made the decision to employ weather data and flight data for this solution based on the table above.
## 2. Data preparation and exploratory analysis.
One of the most crucial jobs in an ML project is feature selection. Over 50 data fields are present in the data downloaded from the Flights API. Only nine associated fields—carrier, flight number, flight date, departure airport, departure time, arrival airport, arrival time, flight distance, and delay in minutes—can be selected in accordance with the mapping table above. [] (https://github.com/ryanhao1115/DL Predict Flight Delays/blob/main/p3.png)
I selected the top 10 airports using the monthly flight count for each airport. The top 10 lists for both origin and destination are identical ( chart above). The lists of origin airports and destination airports, however, differ when comparing the top 10 average delays (see chart below). [] (https://github.com/ryanhao1115/DL Predict Flight Delays/blob/main/p4.png)
![](https://github.com/ryanhao1115/DL Predict Flight Delays/blob/main/p4.png)
Although the distribution of average delays figure below shows that the top 10 average delays are horrendous, they are only outliers.
[]
(https://github.com/ryanhao1115/DL Predict Flight Delays/blob/main/p5.png)
I select six weather features from the Weather API: temperature, wind speed, visibility, wind gust, cloud cover, and ice, in addition to airport, date, and hour.
The next stage is to link weather information with flight information. The airport, day, and hour are the joining keys. It is necessary to do the merge process twice. One combines the airports of origin, the time of departure, and the weather; the other combines the airports of destination and arrival. Each flight record has two sets of weather features following the merge. [] (https://github.com/ryanhao1115/DL Predict Flight Delays/blob/main/p6.png)
## 3. Feature Engineering
The upper bound of machine learning is determined by the data features in the field of data science, and the algorithm only aspires to this upper bound.
The project's feature engineering is divided into two key categories. The first is target fields engineering, and the second is categorical fields encoding.
There are hundreds, maybe thousands, of classes in the category fields, such as flight number and airports. The standard One-hot-encoding is inapplicable to them. I selected the target encoding, which substitutes the target variable's mean for a category value. [] (https://github.com/ryanhao1115/DL Predict Flight Delays/blob/main/p7.png)
Arr dealy is the project's target field. Minutes are involved. Therefore, since this is a regression problem, we attempt to forecast the delay in minutes. [] (https://github.com/ryanhao1115/DL Predict Flight Delays/blob/main/p8.png)
Delay in minutes has a long tail, as seen in the diagram above, and a lot of data goes into negative values. This is due to the fact that these figures represent discrepancies between expected and actual arrival times. On the one hand, it is exceedingly challenging for the algorithm to forecast an exact delay in minutes using such data. Customers, on the other hand, might not care exactly how many minutes of delay there is. So, I divided the minutes into the following 5 categories:! [] (https://github.com/ryanhao1115/DL Predict Flight Delays/blob/main/p9.png)
This project evolved into a problem of categorization prediction. Additionally, it benefits customers more.
## 4. Deep Learning Model training
For this project, I built deep learning using Tensorflow Keras.
[]
(https://github.com/ryanhao1115/DL Predict Flight Delays/blob/main/p10.png)
I set an early-stop during the training to save time.
[]
(https://github.com/ryanhao1115/DL Predict Flight Delays/blob/main/p11.png)
In training data, the accuracy score is 75.77%, and in validation data, it is 72.06%. Since I just utilised one month's worth of data for training, it is not high. The model should perform better if I add additional data. [] (https://github.com/ryanhao1115/DL Predict Flight Delays/blob/main/p12.png)
