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

<img src="/post/2019-01-01-embeddings-categorical-input-data_files/Jietu20190101-162726.png" alt="post ads for house price" width="90%"/>

### 2. classification of hand drawing

<img src="/post/2019-01-01-embeddings-categorical-input-data_files/Jietu20190101-162553.png" alt="hand-drawing classifications " width="95%"/>

### 3. movie recommendations 
![](/post/2019-01-01-embeddings-categorical-input-data_files/Jietu20190101-162648.png)

## Rule of Thumb for Choosing Dimensions

<img src="/post/2019-01-01-embeddings-categorical-input-data_files/Jietu20190101-162108@2x.png" alt="" width="120%"/>
