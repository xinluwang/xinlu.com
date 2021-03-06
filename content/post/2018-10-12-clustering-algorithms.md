---
title: Clustering Algorithms
author: xinlu wanag
date: '2018-10-12'
slug: clustering-algorithms
categories:
  - Programming
tags:
  - ML
---

## Problem Statements

> Given a set of data points, group them into a clusters so that:    
> &nbsp;&nbsp;&nbsp; 1. points within each cluster are similar to each other    
> &nbsp;&nbsp;&nbsp; 2. points from different clusters are dissimilar    
> Usually, points are in a high-dimensional space, and similarity is defined using a distance measure, such as Euclidean, Cosine, Jaccard, edit distance, ...

## Examples

1. Cluster customers based on their purchase histories
2. Cluster products based on the sets of customers who purchased them
3. Cluster documents based on similar words or shingles
4. Cluster DNA sequences based on edit distance


## Methods 
 
- Hierarchical (AgglomeraHve):
    1. Initially, each point in cluster by itself.
    2. Repeatedly combine the two “nearest” clusters into one.
- Point Assignment:
    1. Maintain a set of clusters.
    2. Place points into their “nearest” cluster.
    
