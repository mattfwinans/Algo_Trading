# Algo_Trading
The purpose of this project is to create an automated trading platform. The project is broken out into 3 categories, corresponding to the 3 files. 

1. Picking the stocks to trade - I chose to use Yahoo Finance's top rated stocks (analysts rank every stock in Yahoo finance), and I scrape the ticker symbols of the 20 top rated stocks. This can be easily modified if you wanted to input your own tickers or if you wanted to focus on a specific industry.

2. Gathering the data, creating and training our model. In this file, which is the meat of our project, we use our top 20 tickers and get all of their candlestick data as well as other technical indicators to determine moving averages, overbought or oversold, variance, etc. This data is pulled on an hourly basis (as opposed to another interval, such as daily, every 15 minutes, etc). All of this data for each ticker is then input into a deep learning model, which leverages time-distrubted Convolutioal layers and an LSTM layer which excels at time-series data. The best model is saved to your local machine in the form of an H5 file. 

3. This is where we execute trades based on our models predictions. Currently, I have the model using the past 59 hours (approx 1 week) of data to predict the 60th hour. If the predicted high and low prices of a stock are higher than the current high and lows, we automatically purchase the stock. If we own the stock and the high and low predicted prices are lower than the current high and low prices, we sell the stock. Otherwise, we do not perform any action. In this step we rely on the Alpaca trading platform, but I believe there are many other trading platforms that can be used instead. 
