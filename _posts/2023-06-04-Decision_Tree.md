---
title: Decision Tree
author: Bhoomeendra 
date: 2023-05-08
category: Jekyll
layout: post
comments: true
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
6. Normalization and scaling of data is not required.


__Cons__

1. Decision tree is prone to overfitting.
2. Decision tree is unstable, small changes in the data can lead to large changes in the structure of the decision tree.
3. Decision tree can create biased trees if some classes dominate.

### Regression Tree
We minimize the sum of squared error at each split. And the prediction is the mean of the data points in the leaf node.

1. For the first node the mean of the data would be the prediction. Now we will select a feature and threshold combination which will reduce the sum of squared error the most.

2. We repeat the above step for all the child nodes until we reach the maximum depth of the tree or we reach the minimum number of data points in a leaf node.

## Interview Questions

**1. What is impact of outliers on decision tree?**

Decision tree by design is not intrested in the actual values but it is intrested in the features and thresholds. So the outliers will not have much impact on the decision tree.

**2. What is the difference between Gini Index and Entropy?**

Gini Index is a measure of impurity and Entropy is a measure of randomness. Gini Index is faster to calculate compared to Entropy also Gini index is bounded between 0 and 1 whereas Entropy is not bounded.

**3. What is the impact of data imbalance on decision tree?**

Decision tree is prone to bias if the data is imbalanced as it will impact the information gain calculation. 

**4. What is the impact of data preprocessing on decision tree?**

Decision tree is not impacted by data preprocessing like normalization and scaling.

**5. Time complexity of decision tree?**

The time complexity for decision trees is $$O(Nkd)$$ where n in the number of datapoints k is number of features and d is the depth . $$O(NK)$$ is the complexity for finding the best split at a level and we had d such levels . This means that it’s actually somewhere in between being in O(NklogN) and O(N2k) as best possible depth for binary tree is log(N) and worst is N.

**6. What is the Inductive Bias of Decision Trees?**

ID3 Algorithm prefers shorter trees over longer trees.
    
**7. Why do we require Pruning in Decision Trees?**
    
Pruning is a technique in which we remove the nodes which do not add any value to the model. Decision tree is prone to overfitting and pruning helps in reducing the overfitting. Pruning can be done in two ways pre-pruning and post-pruning. In pre-pruning we stop the tree from growing when we reach the maximum depth of the tree or when we reach the minimum number of data points in a leaf node or when we reach the minimum information gain. In post-pruning we grow the tree to the maximum depth and then we remove the nodes which do not add any value to the model.

**8. What kind of decision boundary does decision tree create?**

Decision tree creates a piecewise constant decision boundary. The boundary is parallel to the axis.


