Stock Price Forecasting for ADANI PORTS using Python and SARIMA

In this project, I take the daily closing prices of ADANI PORTS and work through a complete time series forecasting process, from preparing the data to predicting future prices.

The notebook starts by loading the price data, sorting it and keeping the closing price. Before building a model, I check whether the series is stationary using the Augmented Dickey-Fuller (ADF) test, and break it down into its trend, seasonal and residual components to better understand how it behaves.

I then use the first 80% of the data for training and hold back the remaining 20% for testing. A SARIMA(1,1,1)(1,1,1,12) model is fitted on the training data and used to forecast the test period, and I measure how close it gets using MAE and RMSE. Finally, the notebook produces a 180-day forecast and looks at how the price changed in percentage terms from year to year.

Results:

The ADF test returned a p-value of 0.0087. On the test data, the model had a mean absolute error (MAE) of about 61.7 and a root mean squared error (RMSE) of about 108.4. In the yearly analysis, 2021 saw the highest increase in average price, while 2011 saw the lowest.

Data and libraries:

The project uses daily ADANI PORTS price data from `ADANIPORTS.csv`, which the notebook loads directly. It is built with pandas, NumPy, Matplotlib, statsmodels and scikit-learn.

Limitations and next steps:

There is still room to improve this work. Although the data is daily, the SARIMA model uses a seasonal period of 12 and the decomposition uses a period of 365. I would like to try other seasonal periods and compare the models using AIC or cross-validation.

The stationarity result also deserves a closer look. The ADF test indicated that the price series is stationary (p = 0.0087), but stock prices usually follow trends. A good next step would be to check the differenced series and compare the model against a simple baseline, such as a naive forecast.

Lastly, stock prices are strongly influenced by news and market events. Since this model learns only from past prices, it cannot anticipate them, which limits how accurate its forecasts can be.
