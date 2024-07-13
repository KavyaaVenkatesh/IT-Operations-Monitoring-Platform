# IT-Operations-Monitoring-Platform
The platform is designed to monitor key performance metrics, detect anomalies, and predict incidents using  machine learning algorithms.


**Anomaly Detection**
   
**Isolation Forest:**

Purpose: Detect anomalies in network latency data.

Method: Isolation Forest isolates observations by randomly selecting a feature and then randomly selecting a split value between the maximum and minimum values of the selected feature. The fewer random splits required to isolate an observation, the more likely it is an anomaly.

Implementation: The algorithm is trained on selected features (network latency, rolling mean of network latency, and network latency spikes). Anomalies are identified where the Isolation Forest algorithm predicts a negative value (-1).

**Rolling Mean Calculation:**

Purpose: Smooth the time-series data and detect spikes in CPU and memory usage.

Method: A rolling mean (or moving average) is calculated over a specified window (24 hours in this case) to smooth out short-term fluctuations and highlight longer-term trends. Spikes are identified by subtracting the rolling mean from the actual usage values.

Implementation: Rolling means are calculated for CPU usage, memory usage, and network latency. Spikes are then identified by comparing the actual values with the rolling mean values.

**Predictive Analytics**

**ARIMA Model:**

Purpose: Forecast future CPU usage based on historical data.

Method: ARIMA (AutoRegressive Integrated Moving Average) is a popular time-series forecasting method that uses past values (auto-regression), differencing of raw observations (integration), and a moving average model to forecast future points in the series.

Implementation: The time-series data is split into training and testing sets. The ARIMA model is fitted on the training set and then used to forecast future CPU usage for the testing set.

**Random Forest Classifier:**

Purpose: Predict incidents based on system metrics.

Method: Random Forest is an ensemble learning method that constructs multiple decision trees during training and outputs the mode of the classes for classification. It improves accuracy and controls overfitting.

Implementation: The model is trained using various features, including CPU usage, memory usage, network latency, and their respective spikes. The trained model is then used to predict incidents on the test set, and the performance is evaluated using metrics like precision, recall, and F1-score.

**Hyperparameter Tuning**

Grid Search with Cross-Validation:

Purpose: Optimize the hyperparameters of the Random Forest classifier to improve its performance.

Method: Grid Search exhaustively searches over a specified parameter grid, and cross-validation ensures the model is evaluated on different subsets of the data to prevent overfitting and provide a robust performance estimate.

Implementation: Various hyperparameters of the Random Forest classifier (such as the number of trees, maximum depth, and minimum samples split) are tuned using Grid Search with cross-validation. The best parameters are selected based on the cross-validation performance.



