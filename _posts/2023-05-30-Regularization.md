---
title: Regularization
author: Bhoomeendra 
date: 2023-05-08
category: Jekyll
layout: post
comments: true
---
Regularization is a technique to reduce overfitting in a model. It discourages learning a more complex model, so as to avoid the risk of overfitting. Regularization somtime is introduced for sparcity i.e in the case of L1 regularization and in others for faster and stable convergence (Batch and layer norm). 

__L1, L2 Regularization:__

L1 and L2 regularization are the most common type of regularization techniques. These regularization techniques are also known as shrinkage methods. This is because they shrink the coefficient estimates towards zero. The difference between L1 and L2 regularization is that some of the coefficients can be exactly zero in the case of L1 regularization [ref](http://localhost:4000/ML/jekyll/2023-05-08-Linear-Regression.html#interview-questions). This means that L1 regularization can be used for feature selection as well. 

__Early Stopping :__

Early stopping is a type of regularization technique that uses validation data to check the model performance. It stops the training of the model when the performance on the validation data starts decreasing or no improvment apperes for a specified number of epochs. This is an indication that the model is maylead to overfit the training data.

__Weight Decay__: Differece between weight decay and l2. 

__Dropout__

The idea of droupout as the name imply is to drop out some of the neurons in the network. This is done by randomly selecting a set of neurons and setting their weights to zero(partically the output). This is done for each training sample/batch. The neurons that are dropped out are not used for forward and backward propagation. This can be seen as ensemble of neural networks as each time a different set of neurons are dropped out. This also prevents co-adaptation of neurons. Ones the training is done the weights are scaled by the probability of the neurons being active. The intuition behind this is that the neurons that are dropped out are not used for training and hence the weights of the neurons that are used for training should be scaled by the probability of the neurons being active.

__Batch Normalization [ref](https://www.pinecone.io/learn/batch-layer-normalization/)__

If the model is trained on features on different scales, we observe longer train times because it takes longer to converge when the input features are not all on the same scale. Additionally, such high values can also propagate through the layers of the network leading to the accumulation of large error gradients that make the training process unstable, called the problem of exploding gradients. Hence their is a need for normalization of the input features. With the same anology the exploding of gradient can happend between the layers to prevent this we add a normzalization layer between the layers on the batch level. This is called batch normalization. The basic ideas is that we want to prevent the drastice changes in the distribution between the batches unless neccaesary. This is also called internal covariate shift. This is the reason when the traning process becomes slow. 

Lets say the first mini-batch as 16 samples and the embedding at kth layer is of size 100 then we will normalize 16 embedings along the 100 dimention to zero mean and unit variance so all the 100 dimentions are normalized. But this can also lead to problems because some time mean and varices are need for good performance. So they are reintroduced as leranable parameters.

$$\mu_b=\frac{1}{B}\sum_{i=1}^{B}x_i$$

$$\sigma_b=\frac{1}{B}\sum_{i=1}^{B}(x_i-\mu_b)^2$$

$$\hat{x_i} = \frac{x_i-\mu_b}{\sigma_b}$$

$$y_i = \hat{x_i}.\gamma + \beta$$
Limitations:

1. Batch size should be large enough to get a good estimate of the mean and variance.
2. Not suitable for task like sequence modeling where the length of the sequence is not fixed.

__Layer Normalization__

The process of layer normalization is same as batch normalization but the difference is that it is done along the embedding dimention. Continuing the previous example the normalization is done along the 16 samples so that the a single vector of 100 has zero mean and unit variance. This is done to all the samples that i.e 16 in the example.



