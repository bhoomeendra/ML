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


