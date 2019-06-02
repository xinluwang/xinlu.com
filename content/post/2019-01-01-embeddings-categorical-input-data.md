---
title: 'Embeddings: Categorical Input Data'
author: ''
date: '2019-01-01'
slug: embeddings-categorical-input-data
categories: []
tags: []
---



Category data can be represented by fixed effect, all called **sparse tensors**. However this kind of representations will results in much higher dimensions of input, and are less meaningful. It can memorize the training data without providing prediction powers for the out of sample data. When training the neural network, This representation needs: 1) huge amount of data, and 2) huge amount of computation. 

Therefore, we need *embedding*: using a much lower dimension vector to represent Category data. This process will increase the power of the model. In the same time, we can compute the similarity of different categories. Those embeddings can be utilized in other models as well.

### 1. the words in real estate ad to predict house price

<img src="http://ww4.sinaimg.cn/large/006tNc79gy1g3mu9pu5lmj30xg0i8td9.jpg" alt="post ads for house price" width="90%"/>

### 2. classification of hand drawing

<img src="http://ww1.sinaimg.cn/large/006tNc79gy1g3muaqzpeij315a0kcqac.jpg" alt="hand-drawing classifications " width="95%"/>

### 3. movie recommendations 

![](http://ww4.sinaimg.cn/large/006tNc79gy1g3mub97wbyj314u0jsjyi.jpg)

## Rule of Thumb for Choosing Dimensions

![](http://ww3.sinaimg.cn/large/006tNc79gy1g3mubrrqgrj318s0d6jtq.jpg)


 
