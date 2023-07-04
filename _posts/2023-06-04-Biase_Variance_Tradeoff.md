---
title: Biase Variance Tradeoff
author: Bhoomeendra 
date: 2023-06-04
category: Jekyll
layout: post
comments: true
---
[Visit](https://www.cs.cornell.edu/courses/cs4780/2018fa/lectures/lecturenote12.html)

When we talk about the Biase and Variance tradeoff we are talking about the error in the model and these are calculated on multiple(infinte) train and test splits of the data as these measures are statical in nature.

__Bias :__ 

Bias is the difference between the average prediction of all the models and the expected Label. The Dataset is also obtained from the a distribution $$P(X,y)$$ so for a feature vectors X we a distribution of y which comes from $$P(\frac{Y}{X})$$ which means we have to get the expected label from the distribution $$P(\frac{Y}{X})$$. 

The reason for High bias could be that the model is too simple. Being High bias means that the model is not able to capture the general trend in the data. Low Bias means that the model is able to capture the general trend in the data and is a good situtation to be in.


__Variance :__

Let's say we have 50 models and we have to calculate the variance of the models. We calculate the variance of the model by calculating the variability in the output of the models with the formula of variance.

High variance means that the model is not able to generalize well on the data and is overfitting. This mean that if the model is trained on a different the predictions would change drastically. Low variance means that the model is able to generalize well on the data and is a good situation to be in.

__Tradeoff :__

Pursuing low bias requires increasing complexity which increases variance as now the model has room to overfit the data, and pursuing low variance requires decreasing complexity which increases bias. 