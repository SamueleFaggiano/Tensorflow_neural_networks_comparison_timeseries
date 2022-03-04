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
Long short-term memory (LSTM) is an artificial recurrent neural network (RNN) architecture used in the field of deep learning. Unlike standard feedforward neural networks, LSTM has feedback connections. It can process not only single data points (such as images), but also entire sequences of data (such as speech or video). For example, LSTM is applicable to tasks such as unsegmented, connected handwriting recognition, speech recognition and anomaly detection in network traffic or IDSs (intrusion detection systems).

![alt text](https://github.com/SamueleFaggiano/pollution_timeseries/blob/main/lstm.png)

2) CNN (over features), accuracy=82.5%
Deep CNNs have been quite popular in areas such as Image Processing, Computer Vision, etc. Recently, the research community has been showing a growing interest in using CNNs for time-series forecasting problems. In this case the filters of the Convolutional Layer will slide over the feature to get significant patterns.

![alt text](https://github.com/SamueleFaggiano/pollution_timeseries/blob/main/cnn_over_features.png)

3) Multi-head CNN, accuracy=82.5%
Unlike the previous approach, this time the CNN has different inputs, one for each features. Each of the Convolutional Layer will try to find patterns over time for each features, before going into the Fully-Connected-Layer.

![alt text](https://github.com/SamueleFaggiano/pollution_timeseries/blob/main/Multi-head-CNN.png)

4) Dense Neural Network, accuracy=78.8%
Here I tried to flatten the timesteps considering each of them as single feature, and all of them go inside a Fully Connected Layer of a DNN. The dimensionality increases and the performance decreased. 

![alt text](https://github.com/SamueleFaggiano/pollution_timeseries/blob/main/nn.jpg)

5) LSTM + DNN + Month Embedding, accuracy=71.1%
In this test, I tried to add the average of each feature into a DNN to outline the peaks of variation that causes pollution closely to the LSTM. Moreover, the information about the month has been vectorize thanks to the Embedding Layer before being used as feature.

The LSTM seems to be the best approach for this task with 82.7% accuracy.
