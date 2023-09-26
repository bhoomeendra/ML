---
title: CNN Architectures
author: Bhoomeendra 
date: 2023-07-10
category: Jekyll
layout: post
comments: true
published: false
---
Tasks

 Image classification
 Object detection
 Semantic segmentation
 Image captioning
 Visual question answering
 Image text retrieval

Architectures
 LeNet (1989)
 AlexNet (2012)

MLP is not good with Invariance
 Translation
 Rotation
 Scale
 Illumination
 Viewpoint
 Deformation

Equivariance ?

Pooling and stride helps in downsampling the image.

Normalization
X = (X - mean(X))/ std(X)

Batch Normalization
Good for deep networks

Parameters Initialization
Xavier Initialization
He Initialization

AlexNet
2 GPU

GoogLeNet

 Inception Module

VGGNet


ResNet
    Skip connections

    No dense layers till the end that too is 1x1 convolution

    Sharpe decrease in error would mean that the learning rate in decreased (scheduler)

Inseption V3

Densenet
Seems to work better on medical images


SENet 

 Spatial Seprable Convolution

MobileNet

 Depth Seprable Convolution


EfficientNet
 Compound Scaling

ViT
 Vision Transformer

SWIN (Shifted windows transformer)

ConvNext (2022)

Neural Architecture Search 

NASNet

