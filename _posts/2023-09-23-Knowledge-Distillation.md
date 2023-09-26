---
title: Knowledge Distillation
author: Bhoomeendra 
date: 2023-09-23 00:00:00
category: ML
layout: post
comments: true
---
Knowledge distillation is a technique to train a smaller model to mimic the behavior of a larger model. The idea is to transfer the knowledge from a larger model to a smaller model. The larger model is called the teacher model and the smaller model is called the student model. The student model is trained on the same dataset as the teacher model.The loss of the teacher model predictions is used to guide the student model to learn the same behavior as the teacher model. 

Loss of the student model is as follows :

$$ L = \alpha L_{CE}(y_{true},y_{pred}) + (1-\alpha) L_{CE}(y_{pred~teacher},y_{pred}) $$

where $L_{CE}$ is the cross entropy loss, $y_{true}$ is the true label, $y_{pred~teacher}$ is the predicted soft labels by which is the softmax of predicted softmax out of teacher model divided by temprature, $\alpha$ acts as a balancing between the loss from the teacher(soft loss) and loss from ground truth (hard loss)respectively. 
