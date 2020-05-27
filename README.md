# COVID19 Global Forecasting

## Summary
The purpose of this project is to forecast the gobal confirmed and fatal cases for the period 11-17 May 2020 during the COVID-19 pandemic. The dataset is obtained from a kaggle competition. Instead of forecasting the confirmed and fatal casies by region and country as required in the kaggle competition, I appoached the problem at the global aggregated level. The key method is based on time series modelling techniques and the main forecasting model used is SARIMA. All code is developed with Python in the Google Colaboratory environment with GitHub integration. 

## Methodology
Once the training data is read into a pandas dataframe, it is divided into train, test, and forecast sets by confirmed and fatal cases. By applying the seasonal decompose technique, the trend, seasonal, and residual components are separated. The adfuller test results show P-Value > 5%, which suggests both the confirmed and fatal cases time series are non-stationary. 

The autocorrelation plots show the lag P values for confirmed and fatal cases are 21 and 19 days respectively. The ACF and PACF plots show the 1st order differencing is the most dominant factor for both, which means the D and Q values will all be 1. The seasonal order S value is chosen to be 7 based on previous seasonal component plots and P, D, Q are all set to 1. The forecast results on the test set shows reasonable match. The final predictions on the forecast date range is then obtained by refitting the model on the combined training and test sets with the same hyperparameter setting. 

## Discussion
As the analysis is performed at the global aggregated level, the quantile weights provided in the dataset cannot be applied to calculate the Weighted Pinball Loss. While time series modelling technique can capture the trend and seasonal components, it does not consider other factors that contribute to the spread and diagnosis of the disease, such as social distancing, population density, sample collection, and diagnosis bottlenecks. 

## References:
1. https://www.kaggle.com/c/covid19-global-forecasting-week-5/overview
2. https://www.analyticsvidhya.com/blog/2016/02/time-series-forecasting-codes-python/
3. https://towardsdatascience.com/arima-forecasting-in-python-90d36c2246d3
4. https://www.digitalocean.com/community/tutorials/a-guide-to-time-series-forecasting-with-arima-in-python-3
5. https://medium.com/@kfoofw/seasonal-lags-sarima-model-fa671a858729

