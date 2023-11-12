# Project Title:
Machine Learning Time Series Forecasting on Air Quality dataset
#
---
# Project Description:
Task is Time Series Forecasting on Air Quality dataset with endogenious variable (target): CO(GT) and exogeneous variables: 'T' and 'NO2', using ARIMAX, SARIMAX and PROPHET. 
#
---
# Table of Contents:

  1. Data Cleaning
  2. Exploratory data analysis
  3. Data Preprocessing 
  4. Data Engineering
  5. Model Training
  6. Model Hyperparameter Optimization
  7. Model Evaluation
  8. Conclusion and Results
---
#

# CONCLUSION from EDA, Data preprocessing and Data engineering:

---
## Handling missing values (Linear imputation in time-series)
Missing values in a dataset are marked with -200. They were replaced with NaN so that they could be imputed with linear imputation, as most appropriate technique in this type of dataset.    

## Time Series Aggregation
In order to reduce the granularity of the data, we made аggregation of the dataset by day.

## Oultiers inspection
There are no outliers in the endogenous variable from the dataset. Only few outliers not so extreme outliers in the exogenous variables.

## Decomposition of the endogenous variable

Decomposition doesn't shows specific patterns in a time series, which makes forecasting task harder.

**Trend Component**: Does not show persistent increasing or decreasing direction in the data.

**Seasonal Component**: This component captures regular patterns that occur over a period of 7 days.

**Residual Component**: This component represents the remaining random fluctuations in the data after removing the trend and seasonal components. Nothing particular can be seen at this point.      

## Stationarity test: 
Endogenous variable passed the stationarity test, while exogenous variables didn't. I tried few options listed above, but I left only the one that performed best. 

**Without transformations**: Since endogenous variable passed the stationarity test it is not necessary to transform exogenous variables. This model performed best.

**Log transformations on exogenous features**: Log transformation ONLY on exogenous variables gave me lower model performance. I wasn't sure how algorithm is working because I was transforming only exogenous variables, and I'm using enforce_stationarity=True parameter which applies to all features (log transformed and original ones). 

**Log transformations on all features**: I tried this option as well, because stationarity test will fail if critical values of stationarity test is 0.01, instead of 0.05, so it is totaly justified to transform endogenous variable together with others. This model preformed worst of all models. Probably beacuse the function has values near zero, which after log function was applied, become new outliers. So in my opinion is better not to transform endogenous variable.  

#    
---
# RESULTS

![image](https://github.com/VesnaPop-Dimitrijoska/ML-Time-Series-Forecasting---AirQuality-/assets/144008804/ae3f1172-83c5-48de-b426-fe9e1ca731ff)


# CONCLUSION
All of the models demonstrated GOOD forecasting performance on the test dataset, as evidenced by both visual representation of the predictions and the comprehensive evaluation metrics used.     
* ARIMA model was made just for comparson with ARIMAX and as expected this model preformed the worst of all. 
* ARIMAX i SARIMAX perform the same if seasonal parameter was 0 or 7 days.



#
# License
MIT License
#
