# Machine-learning-Anomaly-Detection-Task
This problem is a typical anomaly detection task. We build various Unsupervised Learning models to detect whether the dataset contains anomalies or not. 
# Data
The dataset for the study contains the temperatures (in Fahrenheit degrees) of a device through time. Namely, on specific dates and specific times throughout the day. It contains only two columns, the date/time portion and the corresponding temperature of the device. 
# Tasks performed:
1. Plot / Visualize the 'original' dataset (this is a Time Series object)
2. Performed Feature Engineering on the dataset such that new features are to be added. Specifically, creates a feature that will indicate the day of the week and time of the day. Namely, four (4) categories (clusters?) for the feature, named 'dtcat' (date-time-category):
- Weekday Day
- Weekday Night
- Weekend Day
- Weekend Night
Note: Some features such as ‘dayofweek’, ‘hours’, ‘day’, etc. may remain in the dataset.
We define the duration of ‘Day’ and Night’ as follows: <br>
Duration of 'Day' should be defined: 7:00am - 7:00pm <br>
Duration of 'Night' should be defined: 7:01pm - 6:59am <br>
Ultimately, we would like to figure out when (weekday, weekend, day or night) the device fails!
3. Applied the K-Means algorithm to the revised dataset and determined the best value for K. We tested the value of K in the range of [1, 20] and plotted a graph showing the number of clusters (K) concerning the score of each K-Means model.
4. After determining the best value of K, plot (scatter plot) all these K clusters by choosing 2 features from the dataset. Should the dataset have more than 2 features (which most likely will be the case), apply PCA to derive those 2 features (2 Principal Components) [pca = PCA(n_components=2), then 'fit' PCA into the dataset]
5. Applied the Gaussian distribution (EllipticEnvelope) algorithm, as defined at step 2. (Using this command: from sklearn.covariance import EllipticEnvelope) List anomalies (if any) in each category and show them graphically.
6. Applied the Isolation Forest algorithm at each category, as defined step 2. (Using this command: from sklearn.ensemble import IsolationForest) List anomalies (if any) in each category and show them graphically.
# Comparison and Conclusion (Which of the two models perform better on detecting anomalies):
## Upon analysis of the two models—Elliptic Envelope and Isolation Forest, here are the observations:
### Elliptic Envelope:
This method detected a broader range of anomalies throughout the dataset. Notably, there were multiple detections around 2013-11 to 2014-02. The anomalies detected include both upward spikes and downward drops. From a visual standpoint, this method seems to be more sensitive, capturing both minor and major potential anomalies.

### Isolation Forest:
This model detected fewer anomalies overall. The main detections were around the end of the dataset, particularly in the period from 2014-03 to 2014-05. These anomalies were primarily upward spikes in the data. Visually, this model appears more conservative, highlighting only the most prominent deviations. <br>

To capture a comprehensive range of potential anomalies, including minor ones, the Elliptic Envelope may be preferable.
