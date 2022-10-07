---
layout: default
---

This is Group 16 project for 2022 Fall, CS 7641.


# Proposal


## Introduction/Background

Stock market investment requires an understanding of several metrics and indicators to make decisions about when to buy, sell, and hold. It often requires the work of many analysts evaluating factors impacting several industries and businesses. A machine learning approach enables a more efficient and robust analysis of a much larger set of data. Such algorithms can be utilized to make predictions about stock prices in advance. 

## Problem Definition

Existing machine learning models like Random Forest used to predict values of S&P500 [1] and XGBoost used to predict Vangaurd (VTI) returns [2] aim to predict changes in stock prices to assist financial decisions. However, prediction models have proven to be limited in their own way. Even so, models can be constantly trained on an ever increasing volume of data. A finely tuned machine learning model is better suited to illuminate the predictive value of historical market activity on future trends.

Given a set of numeric data about the past stock performance and text data from news outlets, by using Random forest, XGBoost decision tree models and clustering models, we aim to better fit, tune datasets and to outperform traditional prediction models.


## Methods

Since stock datasets contain a lot of noise and are not linearly distributed, data processing is needed. Hence, we plan to utilize two decision tree models:

*   Random Forest
*   XGBoost

We choose Random Forest as one of our models because it can fit almost any dataset, linear or nonlinear. Random Forest also behaves well when there are missing data, but besides that we also recognize that Random Forest models can overfit when the datasets have too much noise

XGBoost is another decision tree model that we consider, because it is less likely to overfit if we add regularization criteria and it can provide a more flexible and accurate model. There are some disadvantages with XGBoost are its high time complexity, space complexity and its difficult parameters tuning.

For our unsupervised learning model, we plan to cluster different types of stocks using both GMM and K-means clustering. For each stock, we will calculate the percent change in price for each day. This gives a more meaningful comparison compared to the absolute change in price. Each day will correspond to a unique variable, so a single distance computation will always be done for the same corresponding day. 



## Potential Results and Discussion

We plan to use 2 advanced decision tree models (Random Forest and XGBoost) to avoid overfitting and to better tune our parameters. Potentially, we would apply this model with a single S&P 500 index as our starting point, as we get better simulation and prediction we can move forward with other stock indexes and funds. 

We will also evaluate our clustering models using the Silhouette Coefficient and the Davies-Bouldin Index. We expect our clusters to group stocks that move similarly. This can be useful for traders who want to diversify their portfolio or who want to focus on specific sectors. It can also be used as a starting point to better understand the stock market.

## Datasets

We will be collecting stock data from Yahoo Finance [3] and Alpha Vantage [4]. Other than the numerical data, we will collect the text data from the New York Times API for our NLP implementation.

## References

<span style="font-size:0.8em;">[1]Khaidem, L., Saha, S., & Dey, S. R. (2016, April). Predicting the direction of stock market prices using random forest.</span>\
<span style="font-size:0.8em;">[2]Zolotareva, E. (1970, January). Aiding long-term investment decisions with XGBoost machine learning model.</span>\
<span style="font-size:0.8em;">[3] Yahoo! Finance. Yahoo! https://finance.yahoo.com/, 2022.</span>\
<span style="font-size:0.8em;">[4] Alpha Vantage. Alpha Vantage Inc. https://www.alphavantage.co/, 2022.</span>\
<span style="font-size:0.8em;">[5] Obthong, M., Tantisantiwong, N., Jeamwatthanachai, W., & Wills, G. (2020). A survey on machine learning for stock price prediction: algorithms and techniques.</span>\
<span style="font-size:0.8em;">
[6] Ding, X., Zhang, Y., Liu, T., & Duan, J. (2015, June). Deep learning for event-driven stock prediction. In Twenty-fourth international joint conference on artificial intelligence.</span>\

