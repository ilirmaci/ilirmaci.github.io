---
title       : An app to illustrate clustering
subtitle    : 
author      : Ilir Maci
job         : 
framework   : io2012        # {io2012, html5slides, shower, dzslides, ...}
highlighter : highlight.js  # {highlight.js, prettify, highlight}
hitheme     : tomorrow      # 
widgets     : []            # {mathjax, quiz, bootstrap}
mode        : selfcontained # {standalone, draft}
---

## Introduction

Clustering data into groups of similar observations is a very
intuitive concept, but the possible approaches can cause 
confusion.

[This app](https://ilir.shinyapps.io/Assignment1/) illustrates the 
alternative approaches and how to set them up using simple plots that 
the user can control in real time. The code can be found [here](https://github.com/ilirmaci/ShinyClustering).

------------

## The approach

This app uses 90 simulated datapoints of two dimensions. The data is
designed to have several centroids but no clear boundaries between them.

Two popular approaches are shown and contrasted
- K-means clustering, a greedy stochastic algorithm
- Hierarchical clustering, an exhaustive deterministic approach

------------

## The data


```r
x1 <- rep(c(1, 2, 4), c(30, 25, 35))
x2 <- rep(c(1, 5, 2, 5, 3), c(10, 12, 28, 15, 25))
set.seed(1235)  ## fixed for consistency between instances
x1 <- x1 + 0.5 * rnorm(x1)
x2 <- x2 + 2 + 0.4 * rnorm(x2)
data <- data.frame(x1, x2)
```


![plot of chunk unnamed-chunk-2](figure/unnamed-chunk-2.png) 


------------

## K-means clustering

The app explains and illustrates how to run _K-means clustering_ analysis.

1. The user needs to pick a target **number of clusters** beforehand
2. The **seed** can be changed to show that the process is stochastic
3. The **number of iterations** can be increased to ensure a better 
   (more robust) solution

All of this updates the scatterplot with observations colored by cluster.
Cluster centroids are shown on the plot too.

-------------

## Hierarchical clustering

If the user chooses _Hierarchical clustering_ the app shows how this 
approach works on the same data.

1. Hierarchical clustering is a deterministic procedure
2. It produces a dendrogram that shows the distances between
   any two observations in the dataset
3. The number of clusters can be chosen afterwards using two
   equivalent methods:
   - Picking the target number of clusters directly
   - Choosing the distance threshold where to cut the tree
   
Both the clustered data and the dendrogram are updated automatically.


