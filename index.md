---
layout: default
---

This is Group 16 project final report for 2022 Fall, CS 7641.

# Final Report


## Introduction/Background

Stock market investment requires an understanding of several metrics and indicators to make decisions about when to buy, sell, and hold. It often requires the work of many analysts evaluating factors impacting several industries and businesses. A machine learning approach enables a more efficient and robust analysis of a much larger set of data. Such algorithms can be utilized to make predictions about stock prices in advance. 

## Problem Definition

Existing machine learning models like Random Forest used to predict values of S&P500 [1] and XGBoost used to predict Vangaurd (VTI) returns [2] aim to predict changes in stock prices to assist financial decisions. However, prediction models have proven to be limited in their own way. Even so, models can be constantly trained on an ever increasing volume of data. A finely tuned machine learning model is better suited to illuminate the predictive value of historical market activity on future trends.

Given a set of numeric data about the past stock performance and text data from news outlets, by using Random forest, XGBoost decision tree models and clustering models, we aim to better fit, tune datasets and to outperform traditional prediction models.


## Data 

![AmazonPlot](image/amzn.png)

In our project, we used the historical stock data for all current S&P 500 companies. The data collection process is different from what we have proposed. Instead of extracting the stocks data from Yahoo finance, we have downloaded the 5 years records of S&P 500 companies stock data from kaggle.
 
We used “price change” to measure the movement of the stock price. The figure above shows an example of the plot for AMZN stock, with moving average applied.

## Methods
### Unsupervised Model: KMeans
We normalized our dataset to format it to a standardized version and used Principal Component Analysis to reduce the amount of features in our data set, into 2 components. After preprocessing our dataset, we used unsupervised learning model KMeans to cluster different types of stocks. For each stock, we will calculate the percent change in price for each day. This gives a more meaningful comparison compared to the absolute change in daily price. Each day will correspond to a unique variable, so a single distance computation will always be done for the same corresponding day.

### Supervised Model: LSTM
Suppose that the opening and ending price of a stock will depend on the prices in the previous days, then the Long Short Term Memory (LSTM) Model can be used in this situation. LSTM is a special Recurrent Neural Network (RNN), mainly used to solve the problem of vanishing gradient and explosion gradient during training models with long sequences. LSTM can perform better in longer sequences than ordinary RNNs.

In our model, we focus on one of the stocks and calculate its absolute price change. We initialized a week as a time sequence in our model. By predicting the absolute price change in the future, we are able to predict the stock prices and its tendency.


## Results and Discussion
### Data Cleaning and Preprocessing
The dataset contains 5 years of stock data from 505 companies. The start date is at 2013-02-08 and the end date is at 2018-02-07. We excluded the stocks that had a different start date or missing dates. The dataset has 7 features for each stock, the date, open price, highest price of the day, lowest price of the day, close price, and volume (number of shares traded). For classifying and predicting stocks, we aimed to find the difference between the close price and the open price for each stock for everyday value. 
 
After checking the data, we found that there is no empty value. Therefore, we used normalization and PCA for our data preprocessing.

![NormalizationPlot](image/PCAimprovement.png)

Normalization of our dataset is also one important factor. If we don’t normalize all stocks data, the classification model will cluster based on price of the stock instead of the movement of stock. As you can see the plot of two stocks “AMZN” and “PCAR”. After normalization, the movements are more even and are much less noisy.
The plot above shows an example of the normalization for the data. 
 
### Principal Component Analysis
In order to reduce the number of features and to find out the most correlated features to the price, we applied PCA to the normalized data. We selected the top 2 features and checked with our algorithm. We compared the model with and without data after PCA by using silhouette score, and found that PCA significantly improved the model performance.

## KMeans Implementation
### Choose K
We used Elbow’s method to choose the K value. The figure is shown as below:

![ElbowPlot](image/Elbowmethod.png)

Therefore, according to the figure, we chose K=10 in our KMeans implementation.

### Clustering Results
![Clustering](image/clustering.png)

The figure above shows the result with ten clusters in different colors.
The plots below show 10 random stocks in our ten clusters respectively within S&P 500. By looking at the price fluctuations of the stocks in the image, we can clearly see that there is a certain similarity in the cyclical movements of stocks in each cluster. 

![individualstocks](image/individualstocks.png)

![individualstocks1](image/individualstocks1.png)

### Evaluation
We used Silhouette score as evaluation criterion for our KMeans algorithm. 

|                   | Without PCA      | With PCA           |
|:------------------|:------------------|:------------------|
|Silhouette Score   |0.05867           |0.39538             |

Without PCA, we got a low Silhouette score for our clustering, which indicates that the object is poorly matched to its own cluster. However, we find that the Silhouette score significantly increases with PCA during our preprocessing, which means feature selection is meaningful for stock prices. 

## LSTM Implementation
There are three parameters we need to tune: learning rate, epochs and day shift.
### Data Splitting
We split the dataset into a training set, validation set and testing set. As shown in the figure below, there are 80% training set, 10% validation set and 10% testing set.

![dataSplitting](image/dataSplitting.png)

### Choose Epoch
Based on the mean absolute error and model loss, we are able to select the epoch. As shown in the figure below, we find that the mean absolute error and the model loss decrease at first and then become stable when epoch increases. 

![meanAbsoluteError](image/meanAbsoluteError.png)

![modelLoss](modelLoss.png)

### Choose Learning Rate and Day Shift
A table of learning rate and day shift with different values are shown as the table below:

| Learning Rate | Day Shift   |       RMSE       |
|:--------------|:------------|:-----------------|
|    0.0001     |      1      |11.219924397749342|
|    0.0001     |      2      |11.563998398476235|
|    0.0001     |      3      |13.732455070584612|
|    0.0001     |      4      |13.991984661427592|
|    0.0001     |      5      |13.077982073405082|
|    0.0001     |      6      |12.562368211956432|
|    0.0001     |      7      |13.892026609545221|
|    0.0005     |      1      |5.1904540326040065|
|    0.0005     |      2      |9.937020536168298 |
|    0.0005     |      3      |12.541220487006475|
|    0.0005     |      4      |11.313232060977418|
|    0.0005     |      5      |11.08854720923466 |
|    0.0005     |      6      |11.272926197366393|
|    0.0005     |      7      |10.175188922299782|
|    0.001      |      1      |7.003182913707992 |
|    0.001      |      2      |11.431891395090343|
|    0.001      |      3      |11.335611077097298|
|    0.001      |      4      |12.568800527659812|
|    0.001      |      5      |11.49217023919506 |
|    0.001      |      6      |10.973688736355788|
|    0.001      |      7      |10.104333956143059|
|    0.005      |      1      |6.13139321007332  |
|    0.005      |      2      |13.600075418599765|
|    0.005      |      3      |15.418351749740014|
|    0.005      |      4      |13.204024678112175|
|    0.005      |      5      |14.10610481292281 |
|    0.005      |      6      |12.983334349280053|
|    0.005      |      7      |12.06756643520013 |
|    0.01       |      1      |9.692777119262127 |
|    0.01       |      2      |15.168702097260322|
|    0.01       |      3      |17.995028339012833|
|    0.01       |      4      |13.720656833774225|
|    0.01       |      5      |16.964364793636175|
|    0.01       |      6      |16.067269058858933|
|    0.01       |      7      |15.643823622417152|

From the table, we can find that day shift = 1 will always lead to minimum RMSE value, which means that the price of stock will be more dependent on the previous day. Overall, we choose learning rate = 0.0005, day shift = 1, and epoch = 50 as our parameters. 
 
### Evaluation

![PredictingOnTesting](image/PredictingOnTesting.png)

![PredictingOnTraining](image/PredictingOnTraining.png)

The plots above show an example for stock price tendency prediction on the training set and testing set respectively. The RMSE on the testing set is 4.711.


## Contribution Table

|    Group Member   |                          Tasks Done                              |
|:------------------|:-----------------------------------------------------------------|
| Dan Nguyen        |Report Writing, GitHub Page, Presentation                         |
| Yilong Tang       |Data cleaning and preprocessing, LSTM Implementation, presentation|
| Alan Yu           |KMeans implementation, LSTM parameter tuning, presentation        |
| Jiaying Li        |GitHub script, report writing, presentation                       |


## References

<span style="font-size:0.8em;">[1] Khaidem, L., Saha, S., & Dey, S. R. (2016, April). Predicting the direction of stock market prices using random forest.</span>\
<span style="font-size:0.8em;">[2] Zolotareva, E. (1970, January). Aiding long-term investment decisions with XGBoost machine learning model.</span>\

