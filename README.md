### Data Preprocessing

- We obtained the one minute-averaged level one data from the resources (links attached).

- We also obtained the Kp-index data, whose data points were 3 hours apart each other, with each data point having an hour start and an hour end, covering an interval of 1.5 hours.

- Because of this Kp-index data, we averaged the 1-minute data points for a period of 90 minutes (1.5 hours) so that they match with the 1.5 hr interval Kp-index value observed.

- We then downsampled this data by skipping the intermediate data points, so as we could obtain data points that have the same intervals between them just like the Kp-index data, maintaining the lower bounds time intervals as shown in the notebooks.

- We created a new column in the Kp-index data, which combined the Year, Month, day, and hour start, which became the axis we used to merge the Kp-index data and the data from the faraday cup and the magnetometer.

- We imputed missing data using the last observed value. This approach is suitable for handling missing data caused by anomalies because it provides a reasonable estimate that doesn't introduce artificial patterns into the data. We did not use the mean as it would bring in an abrupt value so different from the neighboring values.

### Feature Engineering

- We assessed feature importance using a Linear Regression model from scikit-learn to identify trends and significant variables in the data.

- We also did a stationarity test using adfuller from the statsmodels.tsa.stattools library and also plotted an autocorrelation function (ACF) curve which showed us that our data was not just a random walk, thus it was justifiable to be predicted.

### Model Selection

- Both the LSTM RNNs and the simple neural network gave a comparatively good performance close to each other.

### Model Training

- We used TensorFlow and Keras to build and train both models. GridSearch was employed to optimize the LSTM's hyperparameters on Google Colab's T4 GPU.

- LSTM was trained using 50 epochs, while the Simple neural network was trained using 500 epochs with early stopping.

### Evaluation

- We evaluated the model's performance using appropriate metrics such as mean squared error (MSE), Mean Absolute error, and Root Mean Squared Error to ensure its accuracy in forecasting geomagnetic storms.

### Correlation of Predicted and Actual Values

- We displayed both the predicted Kp-index values and the actual observed Kp-index values for the same input test data which the model had never seen, and below is a sample screenshot of what we obtained.

### Data

- DSCOVR PlasMAG 2016 Data
- DSCOVR PlasMAG 2017 Data
- DSCOVR PlasMAG 2018 Data
- DSCOVR PlasMAG 2019 Data
- DSCOVR PlasMAG 2020 Data
- DSCOVR PlasMAG 2021 Data
- DSCOVR PlasMAG 2022 Data
- DSCOVR PlasMAG 2023 Data
- SPACE WEATHER PREDICTION CENTER, NATIONAL OCEANIC AND ATMOSPHERIC ADMINISTRATION
- GFZ German Research Centre for Geosciences
- National Oceanic and Atmospheric Administration (NOAA), DSCOVR Space Weather Data Portal
