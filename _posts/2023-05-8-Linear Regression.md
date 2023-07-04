---
title: Linear Regression
author: Bhoomeendra 
date: 2023-05-08
category: Jekyll
layout: post
comments: true
---

<!-- #### What is Linear Regression? -->
The linear regression establishes a relationship between the dependent variable (y) and one or more independent variables (x) using a best-fit straight line. This means relationship between the dependent and independent variables is linear in nature.

#### Different ways to solve Linear Regression
1. __Normal Equation:__ The normal equation is a closed-form solution for linear regression (Gaussian Elimination). It finds the value of the regression coefficients that minimizes the sum of the squared residuals.  

2. __Gradient Descent:__ Gradient descent is an iterative optimization algorithm that can be used to solve linear regression. It works by finding the minimum of a cost function, which is typically the sum of the squared residuals.

3. __Singular Value Decomposition:__ The SVD is used because the data matrix is non-invertible hence we calcute its pseudo-inverse using SVD this is a great artricle explaning the same [Visit](https://sthalles.github.io/svd-for-regression/).

#### Checks to apply before applying Linear Regression
1. __Linearity:__ Linear relationship between dependent and independent variables that can be done using person correlation coefficient not the spearman correlation coefficient.
2. __Normality:__ The residuals are normally distributed. This means that the residuals follow a bell-shaped curve, with most of the values clustered around the mean. The normality assumption is necessary because it allows us to use the standard techniques of statistical inference, such as hypothesis testing and confidence intervals. Violations of normality can lead to biased and inefficient estimates, and incorrect conclusions about the statistical significance of the independent variables.
3. __Homoscedasticity:__ The distribution of residual should be same for all the values of independent variable because if the errors are dependent on the value of independent variable then the model is uncertain as some inputs and is certian at some inputs. This does not provide us a concrete prediction hence the model is not very reiable.
4. __No multicollinearity:__ There is no high correlation between the independent variables. This means that the independent variables are not too closely related to each other.  If there is high correlation between the independent variables, it can be difficult to separate out their individual effects on the dependent variable, leading to unstable estimates of the regression coefficients.

#### How to deal with multicollinearity?
1. __Remove one of the correlated variables:__ The simplest way to deal with multicollinearity is to remove one of the highly correlated variables from the regression model. The downside of this approach is that it reduces the degrees of freedom of the model, which can weaken the statistical power of your analysis.
2. __Combine the correlated variables:__ Another way to deal with multicollinearity is to combine the correlated variables together to form a single predictor. For example, if you had two highly correlated variables, you could combine them together to form a single predictor by taking their average.
3. __Use principal components:__ Principal components analysis (PCA) is a dimension reduction technique that can be used to reduce a large set of variables to a small set that still contains most of the information in the large set. This technique is useful when you have a large number of correlated predictors, and you want to summarize them with a smaller set of representative variables.
4. __Use regularization methods:__ Regularization methods, such as ridge (L2 regularization) regression and lasso regression( L1 Regularization), are powerful techniques that are designed to deal with multicollinearity by constraining the size of the regression coefficients. These methods work well when you have a large number of correlated predictors.
5. __Do nothing:__ If your goal is to make predictions, and not to understand the role of each individual variable, then multicollinearity might not be a problem. Multicollinearity only affects the interpretation of your model if you care about the specific role of each variable. However, multicollinearity does affect the precision of the estimated regression coefficients, which can cause your predictions to be less reliable.
6. __Use Partial Least Squares Regression:__ Partial least squares regression (PLS regression) is a regression method that is an alternative to ordinary least squares (OLS) regression. PLS regression is useful when you have a large number of correlated predictors, and you want to use them to predict an outcome, but you also want to reduce the number of predictors in your model. PLS regression is similar to principal components regression, but the key difference between the two methods is that PLS regression uses the response variable in the dimension reduction step, while principal components regression does not.

#### What is the difference between L1 and L2 regularization?
L2 regularization is also known as ridge regression. L1 also known as Lasso. The key difference between them is when we take derivative of the loss function for both, In L2 we see the update or change would be 2*coeff but in L1 it would be either 1 or -1. This is the reason why L1 regularization is used for feature selection and drives some of the coefficients to zero. [Visit](https://medium.com/@mukulranjan/how-does-lasso-regression-l1-encourage-zero-coefficients-but-not-the-l2-20e4893cba5d)

# Interview Questions
