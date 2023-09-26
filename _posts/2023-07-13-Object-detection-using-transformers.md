---
title: Object detection using transformers
author: Bhoomeendra
date: 2023-07-13
category: Jekyll
layout: post
comments: true
published: false
---

Transformater in Vision

## Introduction
Let us try ot add attention to the existing CNN.

Transformers attentions grows quadratically with the input size.

Local Relation Networks forimage Recognition ICCV 2019 Ramachandran et al.

Idea #4 Standard Transformer on patches 

Still the size of patch is large hence we apply some resnet on top of it to get embeddings. Similar to the idea of embedding in NLP. We also add positional encoding to the patches.

ICLR 2021 An image is worth a 16x16 words: Transformers for image recognition at scale.

Interaction between the proposal is nessacry for object detection.

for interaction between the patches of proposal we have to get the predtion for all the patches and then we can apply the self attention after that.

DETR Model: 

K V for the cross attention can be computed on the side of encoder only because all the information is encoded 

Why does key have poistion encoding through out the arctircture?

DINO:
defomable attention
dynamic anchor boxes

Noisy Querys and manipulation in attention maps to stablize the 

Contranstive learning



