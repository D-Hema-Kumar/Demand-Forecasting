# Demand-Forecasting

The Notebook will try to explore and forecast demand of 50 different articles at 10 different locations of a big retail chain. We are given 5 years of store-item sales data, and asked to predict 3 months of sales for 50 different items at 10 different stores.


## SARIMA(X) Notebook

This Notebook focused on implementation of statistical models like ARIMA & SARIMA(X) on the Supply Chain data. The below observations were found during the experiments.

- The models are very fast to train and the optimal parameters can be found using various statistical tests such as Dickey-Fuller test, data visualization technique on Homosedasticity.

- Considerable amount of time is required for finding the right/ optimal parameters Of ARIMA and SARIMAX(p,d,q) (P,D,Q)S (X). Best performing parameters were <b>order=(6,1,0), seasonal_order=(0,1,1,7)</b>

- Significant improvement in results were observed when US holiday External data was imported and merged with the main data set. This reduced the MAPE score by 6%. 
<b> Drawbacks</b>
Implementing statistical models such as ARIMA, SARIMA, SARIMAX on a data like this, where we have 500 combinations of Store & Item, will require considerable time. As each combination will have to be trained separately for Store-Article prediction. Meaning 500 models needs to be trained and for each model specific optimal parameters will have to be found and trained upon.

- One solution can be to use the Hierarchical clustering methodology suchh as the one provided in the paper from <b>Jakob Huber et al. 2017</b>(link below). Another way is to modify the problem from a pure time series into Supervised machine learning by generating  time lag, time shift features and using powerful algorithms such as LightGBMs. <b>I have uploaded another Notebook with LightGBM implemetation where the MAPE was reduced by further 12% points.</b>
https://www.sciencedirect.com/science/article/pii/S0957417417300313
