---
title: Naive Bayes
author: Bhoomeendra 
date: 2023-07-04
category: Jekyll
layout: post
comments: true
---

Given a problem instance to be classified represented by a vector $$x = (x_1, x_2, ..., x_n)$$ representing some $$n$$ features and a class label $$y$$, it assigns to this instance probabilities $$ P(y\|x_1, x_2, ..., x_n) $$ for each of $$k$$ possible outcomes or classes $$y$$.

The problem with above formulation is that if the no. of features is large or if a feature can take on a large no. of values then basing such a model on probability tables is infeasible.

To get around this problem, we make the assumption that the value of a particular feature is independent of the value of any other feature, given the class variable. This is called the **naive Bayes assumption**.

$$ P(C_k|x_1, x_2, ..., x_n) = \frac{P(C_k)P(x_1, x_2, ..., x_n|C_k)}{P(x_1, x_2, ..., x_n)} $$

For a given sample $$ P(x_1, x_2, ..., x_n) $$ will remain constant, so we can ignore it. So we have:

$$ P(C_k|x_1, x_2, ..., x_n) \propto P(C_k)P(x_1, x_2, ..., x_n|C_k) $$

$$ P(C_k|x_1, x_2, ..., x_n) \propto P(C_k)P(x_1|C_k)P(x_2|C_k)...P(x_n|C_k) $$

Now we pick the class $$C_k$$ that maximizes the above probability.
## Numeric Data

We can use Gaussian distribution to model the probability of a feature given a class. So we have: 

$$ P(x_i|C_k) = \frac{1}{\sqrt{2\pi\sigma_{C_k}^2}}e^{-\frac{(x_i - \mu_{C_k})^2}{2\sigma_{C_k}^2}} $$

$\mu_{C_k} , \sigma_{C_k}$ for the give feature. 

The PDF(X) is the probability density function of the normal distribution but can be used to calculate the probability of a given value of $$x_i$$ because we are not interested in calculating the exact probability but only the relative probability and for sufficiently small intervals the probability density is proportional to the probability.


## Text Data

Each word is treated as a feature and its frequency in a given class is used to calculate the probability.

How to handle unseen words? We can use Laplace smoothing.

$$ P(w_i|C_k) = \frac{count(w_i, C_k) + \alpha}{count(C_k) + \alpha |V|} $$

Where $$\|V\|$$ is the size of the vocabulary and $$\alpha$$ is the smoothing parameter. The smoothing parameter is generally set to 1. If $$\alpha$$ is infinity then we probability of all the words will be the same. $$\alpha$$ acts as a regularizer and prevents overfitting.

Another thing to keep in mind is that the product of probabilities can be very small and can lead to underflow. To avoid this we can take the log of the probabilities and add them.

## Limitations 
1. The assumption that the features are independent is not true in most cases.
2. Class imbalance can lead to poor performance as the model will be biased towards the majority class.
