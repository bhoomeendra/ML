---
title: Decision Tree
author: Bhoomeendra 
date: 2023-05-08
category: Jekyll
layout: post
---

<!-- #### What is Decision Tree? -->
Decision tree is a type of supervised learning algorithm that can be used for classification and regression the the algorith tries to split the data into different groups based on the features such that it maximizes the information gain or minimizes the entropy. We will take the example of classification to understand the decision tree.
### Algorithm:

1. We start with the root node which has all the data points. Now the first step is to split the root node based on the feature the question is how do we decide which feature is a good feature? We use the concept of information gain to decide which feature is a good feature.

    __Information Gain__
    Let's say we have a feature called color which has 3 values red, blue and green. Now we want to split the data based on this feature. When we split the node based on color we would get three children. We calculate the entropy of the root node and then we calculate the entropy of the child nodes. The entropy of the root node is calculated as follows:

    $$Entropy = -\sum_{i=1}^{n} p_i \log_{2}(p_i)$$

    where $p_i$ is the probability of the class $i$ in the root node. Now we calculate the entropy of the child nodes. The entropy of the child nodes is calculated as follows:

    $$Child Entropy =   - \sum_{j=1}^{C}\frac{n_j}{n}*\sum_{i=1}^{n_j} p_{ji} \log_{2}(p_{ji})$$

    where $p_{ji}$ is the probability of the class $i$ in the child node $$j$$. $$\frac{n_j}{n}$$ gives the fraction of data points in a given child node compared to the root node. Now we calculate the information gain as follows:

    $$Information Gain = Entropy - Child Entropy$$


2. We calculate the information gain for all the features and we select the feature which has the highest information gain. We split the root node based on this feature.

3. We Repeat the above steps for all the child nodes until we get pure or mixed node to a certain amount or we reach the maximum depth of the tree.

__Spliting Criteria for Numerical features__

Let's say we have a feature which is numerical and we want to split the data based on this feature. We first find all the unique values numerical data and sort them, then we find all the mid points between the consecutive values these would be cadidate threshold values. We calculate the information gain for all the threshold values and we select the one which gives the highest information gain. 

__Stopping Criteria__
1. We stop when we reach the maximum depth of the tree.
2. We stop when we reach the minimum number of data points in a leaf node.
3. We stop when we reach the minimum information gain.

__Pruning__
Pruning is a technique in which we remove the nodes which do not add any value to the model.

__Gini Index__
Gini index is a measure of impurity. It is calculated as follows:

$$Gini Index = 1 - \sum_{i=1}^{n} p_i^2$$

where $p_i$ is the probability of the class $i$ in the node.


__Pros__

1. Decision tree is easy to interpret.
2. Decision tree can handle both numerical and categorical data.
3. Minimal impact of outliers.
4. Decision tree can be used for feature selection.
5. Decision tree can be used for regression and classification.

__Cons__

1. Decision tree is prone to overfitting.
2. Decision tree is unstable, small changes in the data can lead to large changes in the structure of the decision tree.
3. Decision tree can create biased trees if some classes dominate.
