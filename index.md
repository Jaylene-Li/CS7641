---
layout: default
---

This is Group 16 project for 2022 Fall, CS 7641.


# Proposal


## Introduction/Background

## Problem Definition


## Methods

We may start our training from the simplest linear model (Ridge regression). However, the dataset of stocks contains a lot of noise and the prices of the stocks are not linearly distributed. Therefore, we may need a more complex model to train the dataset.
The most intuitive method is using a decision tree. However, the stock dataset is so complex that we need to avoid overfitting. There are two kinds of advanced decision tree model:

+ Random Forest
+ XGBoost

The basic idea of Random Forest is building several trees and merging them together. The advantage is, the Random Forest model can almost fit any data, including linear and nonlinear models. Also, it behaves well when there is lots of missing data. In the meanwhile, the disadvantages also exist: the Random Forest models are easy to become overfit when there are too much noises in the dataset.

The XGBoost model is also an advanced decision tree model. Compared to the CART decision tree model, it’s less likely to be overfitting by adding regularization criteria. It’s more flexible and more accurate compared to the Random Forest model. However, XGBoost model is of high time complexity and space complexity. Parameter tuning is also difficult in the XGBoost model.

Another method that we can experiment on predicting stock prices is by using a deep neural network and natural language processing based on different types of events that are important to the stock markets. We can initially divide events into 3 different types: short-term, mid-term and long-term. This idea is expected to take in different external variables in using natural language processing (like some repetitive keywords to represent an event) and eventually train our model to associate certain events with increased stock prices or decreased stock prices. The model can generally be pictured as a proof-of-concept model and needs to be trained over time and compared with real life results. 

For our unsupervised learning model, we will try clustering stocks using both GMM and K-means clustering. For each stock, we will calculate the percent change in price for each day. This gives a more meaningful comparison compared to the absolute change in price. Each day will correspond to a unique variable, so a single distance computation will always be done for the same corresponding day. 


## Potential Results and Discussion

## Datasets

We will be collecting stock data from Yahoo Finance[3] and Alpha Vantage[4]. Other than the numerical data, we will collect the text data from the New York Times API for our NLP implementation.

## References

[1] Obthong, M., Tantisantiwong, N., Jeamwatthanachai, W., & Wills, G. (2020). A survey on machine learning for stock price prediction: algorithms and techniques.

[2] Ding, X., Zhang, Y., Liu, T., & Duan, J. (2015, June). Deep learning for event-driven stock prediction. In Twenty-fourth international joint conference on artificial intelligence.

[3] Yahoo! Finance. Yahoo! https://finance.yahoo.com/, 2022.

[4] Alpha Vantage. Alpha Vantage Inc. https://www.alphavantage.co/, 2022.

[5]Khaidem, L., Saha, S., & Dey, S. R. (2016, April). Predicting the direction of stock market prices using random forest. 

[6]Zolotareva, E. (1970, January). Aiding long-term investment decisions with XGBoost machine learning model. 

