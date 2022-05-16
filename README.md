# GBDi_Microsoft_CodeWithoutBarriers_2022
Analyzing and Predicting road accidents in Thailand 

This dashboard currently requires user to clone this repository and run the jupyter notebook to use it interactively. 

https://github.com/elainekhoo1/GBDi_Microsoft_CodeWithoutBarriers_2022/blob/main/GBDi_Dashboard_and_Model.ipynb 

Executive Summary
Analyzing accidents reported by region


Khoan Kaen, Chiang Rai, Chiang Mai has the highest reported number of accidents for 3 consecutive years from 2018 to 2020. Chiang Mai has not appeared as top 3 in 2021 which might suggest that government officials have preventative measures in Chiang Mai.
It is rather surprising to observe that Chiang Rai still remained top 3 in 2021 even though by Chiang Mai is the closest province by proximity.

When comparing accidents reported across gender, occupation, type of vehicle involved, alcohol consumption, drug consumption of injured person, safety measures taken by injured person, cell phone usage of injured person, it is generally found that the following population has relatively higher number of accidents reported in the past 4 years:
Males (relative to Females)
Labourer, Student and Unemployed (relative to other occupations)
Motorbike and bike (relative to other types of vehicles like sedan)
Vehicle overturned or fell off road as well as accidents involving motorbike (relative to other means of injuries)
Not taking safety measures like putting on safety belt
Most of the accidents reported that stakeholder involved in accidents hadn't consumed alcohol, drug, use cell phone during traveling. However, this does not mean that consumption of alcohol, drug and cell phone are encouraged when commuting.


Modeling trends of accidents
In this use case, accidents in Thailand by region are modeled using time series modeling.
Multiple smoothing effects, modeling techniques have been tested out but only of them are included in this production website due to simplicity and performances. They are:

Double exponential smoothing modeling
Triple exponential (Holt-Winters model with the anomalies detection using Brutlag method)
User of this dashboard has the flexibility to choose whether they want to model:

Daily, Weekly or Monthly
By Province or all provinces
Predict next N time (daily, weekly or monthly)
Further select which optimization method they want to use
An example of analysis below is done on Daily data for all province, predicting 60 days ahead using Powell optmization method.

Documentation on optimization method: https://docs.scipy.org/doc/scipy/reference/generated/scipy.optimize.minimize.html

Double exponential smoothing with alpha 0.8 and beta 0.06 seem to be able to capture most of the trends
Note: Prior to this, stationarity check was done using DF test. Examining the seasonality, trends and white noises of trending has been done through acf and pacf.

In the most general sense, the model above shows that there would be an upward trending of accidents to be reported from 2021-12-31 to 2022-03-01 (60 days), peaking near 1300 cases on a daily basis on 2022-03-01.
Challenges and Limitations:
Model Performances:
Models above can be further fine tuned using different minimization methods as well as seasonality and autoregressive parameters
Feature Engineering:
Rather than using time series modeling, new features (external factors like humidity in that province, initiatives by government officials to bring down accident rates, daily traffic in that province etc) can be added into the dataset and be modeled as a multivariate time series model or regression problem. Note: There was an attempt done to model it through linear regression where features are generated based on lagging of its own features but performance of the model is worse than the above.
