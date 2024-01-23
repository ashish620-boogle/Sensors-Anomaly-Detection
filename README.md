# Sensors-Anomaly-Detection

In the IIoT, billions of devices continually provide information that is extremely diverse, variable, and large-scale and presents significant hurdles
for interpretation and analysis. Additionally, issues with data transmission, scaling, computation, and storage can result in data
anomalies that significantly affect IIoT applications. This module presents an anomaly detection framework for the IIoT in the context of
the challenges posed by vast, heterogeneous, and complex data streams. This paper proposes a hybrid approach employing a composition of Long
Short-Term Memory (LSTM) and a Random Forest (RF) Classifier. Our approach leverages the LSTM’s superior temporal pattern recognition
capabilities in multi-variate time-series data and the high classification accuracy of the RF model. By integrating the strengths of LSTM
and RF models, our method provides not only precise predictions but also effectively discriminates between anomalies and normal occurrences,
even in imbalanced datasets. We evaluated our model on two real-world datasets comprising periodic and non-periodic, short-term, and
long-term temporal dependencies.

## Data Visualisation
Download the Skoltech Anomaly Benchmark(SKAB) data from [Kaggle](https://www.kaggle.com/datasets/yuriykatser/skoltech-anomaly-benchmark-skab).
For Labeled Anomaly Detection TS follow [The ACM_research article](https://dl.acm.org/doi/abs/10.1145/3178876.3185996).

<img src="https://github.com/ashish620-boogle/Sensors-Anomaly-Detection/assets/56781746/55975aeb-2ae5-4e62-9e93-49a67063a154" alt="image" wifth="200"/>

`
periodic data of Labeled Anomaly Detection TS dataset
`

## LSTM-RF technique architecture
<img src="https://github.com/ashish620-boogle/Sensors-Anomaly-Detection/assets/56781746/d55ac537-4043-4ead-9952-327244face7a" alt="image" width="200"/>

The multi-feature prediction LSTM-RF technique makes use
of the exceptional time series prediction performance of LSTM-NN and the
high classification accuracy of the RF model for IIoT. The LSTM model, which
predicts the future values of every feature, was initially trained using the training
set. Then, the error dataset was created from the test set’s prediction
error from the LSTM model. The Random Forest model for anomaly classification was further
developed utilizing the error training set. Tests on various datasets
demonstrated that the model yields encouraging outcomes with 98.4% accuracy,
0.981 precision, 0.980 f1-score, 0.984 recall, and 0.91 AUC.

## LSTM prediction using the model

The validation dataset is utilized to find the hyper-parameters of the LSTM
predictor, which can only be trained using the non-anomalous training dataset.
The following figure depicts the LSTM Model’s predictions with an orange line. The trained
model is augmented with test sets containing non-anomalous and anomalous
data, respectively. Both normal and anomalous data yield respective forecasting
results. The error set (which includes the error of non-anomalous and
anomalous data) can then be formed after computing the error value between
the true and predicted data.
The quantitative feature of the prediction-error dataset is then created
by taking the error from test sets that include both normal and anomalous
data. Three sets make up the error dataset (error training, error
validation, and error testing). So, if our original data have three features:
`{Temperature, Pressure, RPM}` then our Error Dataset will have these six
features: `{AbsoluteErrorTemperature, SquaredErrorTemperature, AbsoluteErrorPressure,
SquaredErrorPressure, AbsoluteErrorRPM, SquaredErrorRPM}`.
And corresponding to each time point there will be a label, with the value y,
which can be 0 for a normal sample and 1 indicates anomalous.


The blue lines show the actual findings,
while the orange lines show the results as predicted
The red arrow shows potential abnormalities.

### Non-anomalous
<img src="https://github.com/ashish620-boogle/Sensors-Anomaly-Detection/assets/56781746/cdd578ee-6180-4fee-9ed4-af7c9057c008" alt="image" width="200"/>
<img src="https://github.com/ashish620-boogle/Sensors-Anomaly-Detection/assets/56781746/51697806-df26-4c87-977a-f78f550df5ee" alt="image" width="200"/>
<img src="https://github.com/ashish620-boogle/Sensors-Anomaly-Detection/assets/56781746/887b0df4-e602-4731-86b5-8cbb591b7721" alt="image" width="200"/>

### Anomalous
<img src="https://github.com/ashish620-boogle/Sensors-Anomaly-Detection/assets/56781746/55ce58a0-8d9b-4a58-a816-210e6e65a15c" alt="image" width="200"/>

## Results and Analysis
### Benchmark data analysis
<img src="https://github.com/ashish620-boogle/Sensors-Anomaly-Detection/assets/56781746/6af19099-d301-4e3e-a496-5d670ba6ede3" alt="image" width="200"/>

`AUC and ROC analysis of Uni-variate models on Benchmark dataset`

### Analysing SKAB Dataset
<img src="https://github.com/ashish620-boogle/Sensors-Anomaly-Detection/assets/56781746/32a94167-eb75-4b55-90e2-a7ea9624d2a4" alt="image" width="200"/>

`ROC and AUC analysis of Multi-variate models on SKAB dataset`
