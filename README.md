# GBDi_Microsoft_CodeWithoutBarriers_2022
Analyzing and Predicting road accidents in Thailand 

To view demo video: https://www.youtube.com/watch?v=es37bLE8r0U

This dashboard currently requires user to clone this repository and run the jupyter notebook to use it interactively. 

https://github.com/elainekhoo1/GBDi_Microsoft_CodeWithoutBarriers_2022/blob/main/GBDi_Dashboard_and_Model.ipynb 

# Executive Summary
## Analyzing accidents reported by region

1. Khoan Kaen, Chiang Rai, Chiang Mai has the highest reported number of accidents for 3 consecutive years from 2018 to 2020. Chiang Mai has not appeared as top 3 in 2021 which might suggest that government officials have preventative measures in Chiang Mai.
It is rather surprising to observe that Chiang Rai still remained top 3 in 2021 even though by Chiang Mai is the closest province by proximity.

2. When comparing accidents reported across gender, occupation, type of vehicle involved, alcohol consumption, drug consumption of injured person, safety measures taken by injured person, cell phone usage of injured person, it is generally found that the following population has relatively higher number of accidents reported in the past 4 years:
a) Males (relative to Females)
b) Labourer, Student and Unemployed (relative to other occupations)
c) Motorbike and bike (relative to other types of vehicles like sedan)
d) Vehicle overturned or fell off road as well as accidents involving motorbike (relative to other means of injuries)
e) Not taking safety measures like putting on safety belt

Most of the accidents reported that stakeholder involved in accidents hadn't consumed alcohol, drug, use cell phone during traveling. However, this does not mean that consumption of alcohol, drug and cell phone are encouraged when commuting.


## Modeling trends of accidents
In this use case, accidents in Thailand by region are modeled using time series modeling.
Multiple smoothing effects, modeling techniques have been tested out but only of them are included in this production website due to simplicity and performances. They are:
a) Double exponential smoothing modeling
b) Triple exponential (Holt-Winters model with the anomalies detection using Brutlag method)

User of this dashboard has the flexibility to choose whether they want to model:
1. Daily, Weekly or Monthly
2. By Province or all provinces
3. Predict next N time (daily, weekly or monthly)

Further select which optimization method they want to use

Documentation on optimization method: https://docs.scipy.org/doc/scipy/reference/generated/scipy.optimize.minimize.html

## Challenges and Limitations:
1. Model Performances:
Models above can be further fine tuned using different minimization methods as well as seasonality and autoregressive parameters
2. Feature Engineering:
Rather than using time series modeling, new features (external factors like humidity in that province, initiatives by government officials to bring down accident rates, daily traffic in that province etc) can be added into the dataset and be modeled as a multivariate time series model or regression problem. Note: There was an attempt done to model it through linear regression where features are generated based on lagging of its own features but performance of the model is worse than the above.
