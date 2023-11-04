---
title: Logistic Regression
author: Bhoomeendra 
date: 2023-05-08
category: Jekyll
layout: post
comments: true
---
<!-- #### What is Logistic Regression? -->

Logistic regression is linear regression over the log odds or logit of the probability of input belonging to a class. The model choice in logistic regression is the logits of the probability are linearly dependent on the independent variable. But the problem we solve with this is the __classification problem__. The output of the model is the probability of the input belonging to a class.
$$ logit(p) = log(\frac{p}{p-1}) $$

The model is as follows:

$$ logit(p) = w^Tx + b$$

$$ p = \frac{1}{1+e^{-(w^Tx+b)}}$$

$$ p = \sigma(w^Tx+b)$$

What sigmoid does is that it constrains the output between 0 and 1. This is one of the definitions of logistic regression. 
### Geometric Formulation 
We can have a geometric explanation as well. We start with a classification boundary which is $$ w^Tx +b $$. We want a w such that $$ \forall i \; y_i(w^Tx_i+b)>=0  $$ i.e the predicted class and the actual class are of the same sign for the product term to be positive but using a objective function which maximizes $$ \sum y_i(w^Tx_i+b) $$ has some limitation. The problem is that when an outlier comes, the loss value will be very high, and the model will try to fit the outlier. To solve the problem sigmoid function is used as it constrains the values between 0 and 1 which limits the impact of outlier.

### Formulation of the loss function
The purpose of the loss function is to maximize the probability of the correct class. Logistic regression is a binary classification problem; hence we have two classes, 0 and 1. Higher probability is associated with class 1, and low probability is associated with class 0. The objective function is as follows:

$$ L = \prod_{i=1}^n p_i^{y_i}(1-p_i)^{1-y_i} \; where \; p = \sigma(w^Tx+b) $$

$$ L = \prod_{i=1}^n \sigma(w^Tx_i+b)^{y_i}(1-\sigma(w^Tx_i+b))^{1-y_i} $$

As all the values are always positive, taking log will not affect the optimization problem. Also will help with numerical stability as the probability values are very small and the product will be even smaller. Hence the loss function is as follows:

$$ L = \sum_{i=1}^n y_i log(\sigma(w^Tx_i+b)) + (1-y_i)log(1-\sigma(w^Tx_i+b)) $$ 

$$ w^* = argmax_w L(w)$$

But still, we have a problem which is that if when w tends to infinity, the we would have the maximum value of the objective function, which is not what we want. Hence we add a regularization term to the objective function. The objective function is as follows:

$$ L =  \sum_{i=1}^n y_i log(\sigma(w^Tx_i+b)) + (1-y_i)log(1-\sigma(w^Tx_i+b)) + \lambda ww^T$$ 

<!-- This theme supports rendering beautiful math in inline and display modes using [MathJax 3](https://www.mathjax.org/) engine. You just need to surround your math expression with `$$`, like `$$ E = mc^2 $$`. If you leave it inside a paragraph, it will produce an inline expression, just like $$ E = mc^2 $$. -->

<!-- To use display mode, again surround your expression with `$$` and place it as a separate paragraph. Here is an example: -->

<!-- $$\sum_{k=1}^\infty |\langle x, e_k \rangle|^2 \leq \|x\|^2$$ -->

### Interview Questions

* **Should we normailze the data before giving it to the logistice regression algorithim?**

    Yes we should normalize the data it would give use two problems first is the 

- Interpretiblity of the weights/coffecient

    - Interpretiblity of the weights/coffecient as because the coffecient indicats the impact on prediction when we have unit change in the feature but feats with differect scale can not be compaired with each other once we normalize (Min Max) or standardize ($$\mu =0 , \sigma =1$$) the data becomes unitless hence comparative interpretblity is possible which could indicate geniune feature importance.

- Convergence of SGD

    The magnitude of gradient of depends on the values of the inputs which we can see for both squared loss and cross entorpy loss which mean that feature with higher values wil have bigger gradient and features with smaller values will have smaller gradient hence convergence would led to ossilation but when the data is normalized such problem is prevented.

* **What is the decsion boundary of logistic regression?**

    The decision boundary of the logistic regression is $$ w^Tx +b = 0 $$ which we  can see from the formula of the probability of the input belonging to a class. We can see that the probability is 0.5 when $$ w^Tx +b = 0 $$ and the probability is greater than 0.5 when $$ w^Tx +b > 0 $$ and the probability is less than 0.5 when $$ w^Tx +b < 0 $$.

* **Impact of Outliers on Logistic Regression**

    Logistic regression is robust to outliers as the loss function is not affected by the outliers as the loss function is the log of the probability of the input belonging to a class. The probability is always between 0 and 1. Hence the loss function is not affected by the outliers.

* **How do we handle categorical variables in Logistic Regression?**

    We can use one hot encoding to handle categorical variables in logistic regression. We can use one hot encoding to convert the categorical variables into numerical variables. We can also use label encoding to convert the categorical variables into numerical variables. But label encoding is not preferred as it will give the numerical variables some order which is might not be the case in categorical variables.

* **Assumptions of Logistic Regression**

    The assumptions of logistic regression are as follows:

    - The dependent variable should be binary.
    - The independent variables should be linearly related to the log odds.
    - There should not be any multicollinearity among the independent variables.
    - The independent variables should not be correlated with each other.
    - Data should be linearly separable.

* **Why is Logistic Regression termed as Regression and not classification?**

    The idea with classfication model is that most of them output discrete values like 0 or 1 or 1 or 2 or 2 or 3. But logistic regression outputs the probability of the input belonging to a class hence we have infite possible outcome. Hence it is termed as regression and not classification. Along with this logistic regression is a linear model on the log odds of the input belonging to a class.

* **Why can’t we use Mean Square Error (MSE) as a cost function for Logistic Regression?**
    Logistic Regression with MSE as a cost function is a non-convex optimization problem.For problems with non-convex optimization problems, there is no guarantee that the algorithm will converge to the global minimum. Hence we use cross-entropy loss as the cost function for logistic regression which is a convex optimization problem.

* **Disadantages of Logistic regression**
    
    - Doesn't have the ability to handle categorical variables with multiple values (unless you use one-hot encoding to create one feature column per category).
    - Assumption of linearity between dependent and independent variables.
    - It is tough to obtain complex relationships using logistic regression.
    - It requires average or no multicollinearity between independent variables.
    - It requires a large sample size to achieve stable results.

# Chi-Square Test for feature selection and techinques like SMOTE and Near Miss for handling imbalanced data