# Demand-Forecasting

The Notebook will try to explore and forecast demand of 50 different articles at 10 different locations of a big retail chain. We are given 5 years of store-item sales data, and asked to predict 3 months of sales for 50 different items at 10 different stores.

## Result Discussion
###  SARIMA(X) Notebook

This Notebook focused on implementation of statistical models like ARIMA & SARIMA(X) on the Supply Chain data. The below observations were found during the experiments.

- The models are very fast to train and the optimal parameters can be found using various statistical tests such as Dickey-Fuller test, data visualization technique on Homosedasticity.

- Considerable amount of time is required for finding the right/ optimal parameters Of ARIMA and SARIMAX(p,d,q) (P,D,Q)S (X). Best performing parameters were <b>order=(6,1,0), seasonal_order=(0,1,1,7)</b>

- Significant improvement in results were observed when US holiday External data was imported and merged with the main data set. This reduced the MAPE score by 6%. 
<b> Drawbacks</b>
Implementing statistical models such as ARIMA, SARIMA, SARIMAX on a data like this, where we have 500 combinations of Store & Item, will require considerable time. As each combination will have to be trained separately for Store-Article prediction. Meaning 500 models needs to be trained and for each model specific optimal parameters will have to be found and trained upon.

- One solution can be to use the Hierarchical clustering methodology suchh as the one provided in the paper from <b>Jakob Huber et al. 2017</b>(link below). Another way is to modify the problem from a pure time series into Supervised machine learning by generating  time lag, time shift features and using powerful algorithms such as LightGBMs. <b>I have uploaded another Notebook with LightGBM implemetation where the MAPE was reduced by further 12% points.</b>
https://www.sciencedirect.com/science/article/pii/S0957417417300313

###  Light-GBM Notebook
This Notebook is in continuation to the one where statustical models such as SARIMA(X) was applied. The main drawback using the classical method was that we eeded to train 500 models for each Store-Item combination for high forecasting accuracy. A general model was needed whihc could predict all the combinations with high accuracy.

- New features such as Weekends(Friday/Saturday/Sunday) were given high weights as sales in the weekends were generally higher.
- Various Time related features such as Time Lags/Shifts in sales and Rolling means were added to the original dataset.
- One hot encoding of Store-Item combination was done to capture more information. Feature Importance chart shows that top 15 important features are all engineered one
- One of the advantage compared with the SARIMA(X) model was that the LightGBM model it can predict on any of the store-item combination and that too with <b>MAPE of 12%</b> on the test set.
- <b>Drawback</b> for this model is that training and finding right hyper-parameters takes lot of time.
