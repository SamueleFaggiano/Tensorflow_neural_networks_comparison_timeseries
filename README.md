# Weather historical time series for pollution prediction

The aim of this study is to compare different algorithms in time series modelling.
This is a dataset that reports on the weather and the level of pollution each hour for five years at the US embassy in Beijing, China.
The data includes the date-time, the pollution called PM2.5 concentration, and the weather information including dew point, temperature, pressure, wind direction, wind speed and the cumulative number of hours of snow and rain. PM2.5 concentration is used to label each time step: 1 if the pollution threshold has been passed at that hour, othrewise 0.
The list of features used to train the model is the following:
* dew: Dew Point
* temp: Temperature
* press: Pressure
* wnd_spd: Cumulated wind speed
* snow: Cumulated hours of snow
* rain: Cumulated hours of rain
* pollution: 1 (yes) or 0 (no), threshold=80

The algorithms are compared below:

1) LSTM, accuracy=82.7%  
![alt text](https://github.com/SamueleFaggiano/pollution_timeseries/blob/main/lstm.png)

2) 
