---
title: Objectt Detection
author: Bhoomeendra 
date: 2023-07-11
category: Jekyll
layout: post
comments: true
published: false
---

Sliding window approch is not scalable becuase first we have to check for all the possible locations and then for all the possible scales. This is computationally expensive.

We have smartly reduce the number of posible windows that we check things like edges and corners. Then we get object proposals. Then we run the classifier on these proposals.

Object proposals should have high recall and can have low precision. We can use selective search to get object proposals.

Object detection coarse to refine approch.

RCNN: Region based CNN. We use selective search to get object proposals. Then we run the classifier on these proposals. We use a CNN to extract features from the image. Then we use a SVM to classify the object. Then we use a regressor to refine the bounding box.

NMS : Non maximal supression is used to remove the duplicate bounding boxes based on the IOU.

Take the maxiaml score box kill other box in the local neighborhood.

First we have to decive which bounding box in +ve and which is -ve. We use IOU to do this. If IOU is greater than 0.7 then it is +ve else -ve. Still not very good so we calculate precisionand recall for all possible thresholds and then we use the average precision.

RCNN and Fast RCNN.

Region Proposal from Feature Maps.