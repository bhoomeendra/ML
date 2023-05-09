---
title: Logistic Regression
author: Bhoomeendra 
date: 2023-05-08
category: Jekyll
layout: post
---
<!-- #### What is Logistic Regression? -->
Logistic regression is linear regression over the log odds or logit of the probability of input belonging to a class. The model choice in logistic regression is the logits of the probability are linearly dependent on the independent variable. But the problem we solve with this is the __classification problem__. The output of the model is the probability of the input belonging to a class.
$$ logit(p) = log(\frac{p}{p+1}) $$

The model is as follows:

$$ logit(p) = w^Tx + b$$

$$ p = \frac{1}{1+e^{-(w^Tx+b)}}$$

$$ p = \sigma(w^Tx+b)$$

What sigmoid does is that it constrains the output between 0 and 1. This is one of the definitions of logistic regression. We can have a geometric explanation as well. We start with a classification boundary which is $$ w^Tx +b $$. We want a w such that $$ \forall i \; y_i(w^Tx_i+b)>=0  $$ this means that the predicted class and the actual class should be as for the term to be positive but using this as the objective function as some limitation. The problem is that when an outlier comes, the loss value will be very high, and the model will try to fit the outlier. To solve the problem sigmoid function is used as it constrains the values between 0 and 1.

#### Formulation of the loss function
The purpose of the loss function is to maximize the probability of the correct class. Logistic regression is a binary classification problem; hence we have two classes, 0 and 1. Higher probability is associated with class 1, and low probability is associated with class 0. The objective function is as follows:

$$ L = \prod_{i=1}^n p_i^{y_i}(1-p_i)^{1-y_i} \; where \; p = \sigma(w^Tx+b) $$

$$ L = \prod_{i=1}^n \sigma(w^Tx_i+b)^{y_i}(1-\sigma(w^Tx_i+b))^{1-y_i} $$

As all the values are always positive, taking log will not affect the optimization problem. Also will help with numerical stability as the probability values are very small and the product will be even smaller. Hence the loss function is as follows:

$$ L = \sum_{i=1}^n y_i log(\sigma(w^Tx_i+b)) + (1-y_i)log(1-\sigma(w^Tx_i+b)) $$ 

$$ w^* = argmax_w L(w)$$

But still, we have a problem which is that if when w tends to infinity, the we would have the maximum value of the objective function, which is not what we want. Hence we add a regularization term to the objective function. The objective function is as follows:

$$ L = - \sum_{i=1}^n y_i log(\sigma(w^Tx_i+b)) + (1-y_i)log(1-\sigma(w^Tx_i+b)) + \lambda ww^T$$ 

<!-- This theme supports rendering beautiful math in inline and display modes using [MathJax 3](https://www.mathjax.org/) engine. You just need to surround your math expression with `$$`, like `$$ E = mc^2 $$`. If you leave it inside a paragraph, it will produce an inline expression, just like $$ E = mc^2 $$. -->

<!-- To use display mode, again surround your expression with `$$` and place it as a separate paragraph. Here is an example: -->

<!-- $$\sum_{k=1}^\infty |\langle x, e_k \rangle|^2 \leq \|x\|^2$$ -->

# Interview Questions