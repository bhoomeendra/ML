---
title: Hierarchical Clustring
author: Bhoomeendra 
date: 2023-06-04
category: Jekyll
layout: post
comments: true
---
Hierarchical Clustering is of two types which are Divisive and Agglomerative.

 __Agglomerative:__ This is a "bottom-up" approach: Each observation starts in its own cluster, and pairs of clusters are merged as one moves up the hierarchy.

 We start with each observation in its own cluster. Then, we merge the two closest clusters, and repeat until only one cluster remains.

 Merging Clusters: How do we define the distance between two clusters?

 1. Closest points (Single Link): Compute all pairwise distances between the observations in cluster A and the observations in cluster B, and record the closest distance.

 2. Furthest points (Complete Link): Compute all pairwise distances between the observations in cluster A and the observations in cluster B, and record the furthest distance.

 3. Average distance (Average Link): Compute all pairwise distances between the observations in cluster A and the observations in cluster B, and record the average distance.

 4. Ward's method: Merge the two clusters such that the increase in the SSE (sum of squared errors) is minimized. This is the same objective function that k-means tries to minimize!(Need to understand this)

 __Divisive:__ This is a "top-down" approach: All observations start in one cluster, and splits are performed recursively as one moves down the hierarchy. We start with all observations in the same cluster and calculate the distance matrix and after that we form a MST (Minimum spanning tree) and then we cut the tree at edges that have the largest distance till no edges are left.

## Interview Questions

1. How do you select the select the number of clusters which are optimal?
    We have several methods to select the optimal number of clusters.
    
    The most common method is the __elbow method__. In this method we plot the number of clusters on the x axis and the sum of squared distances of the points from the cluster centers on the y axis. We select the number of clusters where the curve starts to flatten out. This is the elbow point. We can also use the silhouette score to select the optimal number of clusters.
    
    The silhouette score is a measure of how similar a point is to its own cluster compared to other clusters. The silhouette score is calculated as follows: $$ s = \frac{b - a}{max(a,b)} $$ Where $$a$$ is the mean distance between a point and all other points in the same cluster and $$b$$ is the mean distance between a point and all other points in the next nearest cluster. The silhouette score is between -1 and 1. A score of 1 means that the point is very similar to its own cluster and very dissimilar to other clusters. A score of 0 means that the point is on the boundary of two clusters. A score of -1 means that the point is assigned to the wrong cluster. We take the average silhouette score for all the points in the dataset and select the number of clusters that gives the highest average silhouette score.

    Dendograms can also be used to select the optimal number of clusters. We draw 2 parallel horizontal lines and select the number of clusters where the distance between the two lines is the largest such that both the lines intersect the dendogram same number of times (Same number of clusters). [__Ref__Q15](https://www.analyticsvidhya.com/blog/2017/02/test-data-scientist-clustering/)

2. What is the of the following metrics do we have for finding Similarity/Dissimilarity between two clusters in hierarchical clustering?

    1. Single Linkage
    2. Complete Linkage
    3. Average Linkage
    4. Ward's Method

3. Is it important to do feature scaling in K-Means?
    
    Yes, it is important to do feature scaling in K-Means. If we do not do feature scaling then the features with larger values will dominate the distance metric. For example, if we have two features, age and income, then the distance will be dominated by income. So, we need to scale the features to bring them to a similar scale.

4. How is SSE (Sum of Squared Errors) calculated in Clusting and how it helps in deciding best clusters?
    
        SSE is calculated as the sum of squared distance between each member of the cluster and its centroid. It is calculated as follows: $$ SSE = \sum_{i=1}^{n} (x_i - \mu_i)^2 $$ Where $$x_i$$ is the data point and $$\mu_i$$ is the centroid of the cluster. We try to minimize the SSE to get the best clusters. The SSE is minimized when the number of clusters is equal to the number of data points. So, we need to select the number of clusters such that the SSE is minimized but the number of clusters is not too large.
