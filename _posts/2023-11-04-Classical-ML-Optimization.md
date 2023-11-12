---
title: Classical ML Optimization Pipeline
author: Bhoomeendra 
date: 2023-05-08
category: ML
layout: post
comments: true
---

## Data Preprocessing
This step includes manly two things
- Data Cleaning
- Feature Engineering/Extraction

**Data Cleaning:**
- Duplicate Values
    - Drop the rows with duplicate values
- Data Type Conversion
    - Convert the data type of the features to the correct data type
- Missing Values
    - Drop the rows with missing values
    - Impute the missing values ( Mean , Median , Mode , KNN , MICE , New Category )
- Outliers Detection and Treatment 
    - Outliers Detection ( Z-Score , IQR , DBSCAN , Local Outlier Factor , Isolation Forest )
    - Drop the rows with outliers
    - Transform the outliers ( Log , Square , Square Root , Cube , Cube Root , Box Cox , Yeo Johnson )
- Data Normalization
    - Standardization ( Z-Score )
    - Min-Max Normalization
    - Robust Normalization
- Data Imbalance
    - Resampling Techniques ( Oversampling , Undersampling , SMOTE )
    - Class Weights ( This is used in the model and impacts the loss function )

**Feature Engineering/Extraction:**
- Categorical Data
    - One Hot Encoding
    - Label Encoding
    - Ordinal Encoding
- Numerical Data
    - Scaling ( Standardization , Min-Max Normalization , Robust Normalization )
    - Binning
    - Transformation ( Log , Square , Square Root , Cube , Cube Root , Box Cox , Yeo Johnson )
- Date and Time
    - Extracting the Year , Month , Day , Hour , Minute , Second
    - Extracting the Day of the Week , Week of the Year , Quarter of the Year
    - Extracting the Time Difference between two dates
- Text Data
    - Text Cleaning ( Removing Punctuations , Removing Stopwords , Stemming , Lemmatization )
    - Vectorization ( Bag of Words , TF-IDF , Word2Vec , GloVe , BERT )
- Time Series Data
    - Time Series Decomposition ( Trend , Seasonality , Residual )
    - Time Series Smoothing ( Moving Average , Exponential Smoothing , Holt’s Linear Trend Model , Holt-Winters’ Seasonal Model )
    - Time Series Forecasting ( ARIMA , SARIMA , SARIMAX , VAR , VARMA , VARMAX , LSTM , GRU , RNN )

## Feature Selection
- Filter Methods : It uses statistical methods for evaluation of a subset of features. It selects features based on their scores in various statistical tests for their correlation with the outcome variable. 
    - Correlation
    - Chi-Square
    - ANOVA
    - Mutual Information
- Wrapper Methods : It follows a greedy search approach by evaluating all the possible combinations of features against the evaluation criterion. The evaluation criterion is simply the performance measure which depends on the type of problem.
    - Forward Selection
    - Backward Elimination
    - Recursive Feature Elimination    
- Embedded Methods : It uses algorithms that have built-in feature selection methods. Some of the most popular examples of these methods are LASSO and RIDGE regression which have inbuilt penalization functions to reduce overfitting.
    - LASSO
    - RIDGE
    - Elastic Net

## Regularization
- L1 Regularization ( LASSO )
- L2 Regularization ( RIDGE )
- Elastic Net

## Hyperparameter Tuning
- Grid Search
- Random Search
- Bayesian Optimization
- Genetic Algorithms

## Model Monitoring

## Missing Values
There are three types of missing values
- Missing Completely at Random (MCAR): 
    The missing values are not related to any other feature or the target variable.
- Missing at Random (MAR): 
    This type of missing data systematically differs from the data you’ve collected, but it can be fully accounted for by other observed variables.The likelihood of a data point being missing is related to another observed variable but not to the specific value of that data point itself.
- Missing Not at Random (MNAR): 
    Data missing not at random (MNAR) are missing for reasons related to the values themselves. For example, MNAR may occur when people with higher salaries are less likely to reveal their incomes.

Methods to handle missing values
- MICE (Multivariate Imputation by Chained Equations)
    The methods is iterative in nature and works by filling in the missing data multiple times. In each iteration, the missing values are imputed using the values predicted by the previous iteration. The steps are as follows:
    - A dependent variable is chosen which has missing values.
    - A regression model is fitted on other variables as predictors to predict the missing values.
    - The missing values are then replaced with the predicted values.
    - The above steps are repeated for each variable having missing values.
    The above steps are repeated for a set number of iterations as the values that were missing in the first iteration are marked we can update them in the next iteration.

## Outliers

**RANDOM SAMPLE CONSENSUS (RANSAC)** is an iterative method where we fit a the model on the subset of the data and then marks the points within a $\epsilon$ error margin as inliers. The process is repeated for a set number of iterations and the model with the highest number of inliers is selected. The algorithm is robust to outliers as it only considers the points that are close to the line. Also ones we have the best model we can use the inliers to fit the model again. The method is computationally expensive as we need to fit the model multiple times.


**Local Outlier Factor (LOF)** is an algorithm for identifying density-based local outliers. It computes the local density deviation of a given data point with respect to its neighbors. The idea is to detect the samples that have a substantially lower density than their neighbors. These are considered to be outliers.

## Data Imbalance

**SMOTE** Synthetic Minority Oversampling Technique (SMOTE) is an oversampling technique that generates synthetic samples from the minority class. It is used to obtain a synthetically class-balanced or nearly class-balanced training set, which is then used to train the classifier.


SMOTE works by selecting examples that are close in the feature space, drawing a line between the examples in the feature space and drawing a new sample at a point along that line. Specifically, a random example from the minority class is first chosen. Then k of the nearest neighbors for that example are found (typically k=5). A randomly selected neighbor is chosen and a synthetic example is created at a randomly selected point between the two examples in feature space. As described in the paper, it suggests first using random undersampling to trim the number of examples in the majority class, then use SMOTE to oversample the minority class to balance the class distribution.

SMOTE Does not work on categorical data because we are interpolating between data points to create new data points. If we have a categorical variable, we cannot interpolate between the values of that variable.



