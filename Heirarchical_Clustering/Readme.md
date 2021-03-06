# Hierarchical Clustering Algorithm

Also called Hierarchical cluster analysis or HCA is an unsupervised clustering algorithm which involves creating clusters that have predominant ordering from top to bottom.

For e.g: All files and folders on our hard disk are organized in a hierarchy.

The algorithm groups similar objects into groups called **clusters** . The endpoint is a set of clusters or groups, where each cluster is distinct from each other cluster, and the objects within each cluster are broadly similar to each other.

<p align="center"> 
<img src="gif1.gif">
</p>

This clustering technique is divided into two types:

1. Agglomerative Hierarchical Clustering
2. Divisive Hierarchical Clustering

## Agglomerative Hierarchical Clustering
 
The Agglomerative Hierarchical Clustering is the most common type of hierarchical clustering used to group objects in clusters based on their similarity. It’s also known as **AGNES (Agglomerative Nesting)** . It's a “**bottom-up**” approach: each observation starts in its own cluster, and pairs of clusters are merged as one moves up the hierarchy.

### How does it work?

1. Make each data point a single-point cluster → forms N clusters
2. Take the two closest data points and make them one cluster → forms N-1 clusters
3. Take the two closest clusters and make them one cluster → Forms N-2 clusters.
4. Repeat step-3 until you are left with only one cluster.

There are several ways to measure the distance between clusters in order to decide the rules for clustering, and they are often called Linkage Methods. Some of the common linkage methods are:

### Complete Linkage
For each pair of clusters, the algorithm computes and merges them to minimise the maximum distance between the clusters (in other words, the distance of the farthest elements)

<p align="center"> 
<img src="complete.jpeg">
</p>

### Average Linkage
It’s similar to complete linkage, but in this case, the algorithm uses the average distance between the pairs of clusters

<p align="center"> 
<img src="average.jpeg">
</p>

### Ward’s Linkage
In this method, all clusters are considered, and the algorithm computes the sum of squared distances within the clusters and merges them to minimise it. From a statistical viewpoint, the process of agglomeration leads to a reduction in the variance of each resulting cluster

<p align="center"> 
<img src="ward.jpeg">
</p>

## Measures of distance (similarity)
We define affinity, a metric function of two arguments with the same dimensionality as of dataset. The most common metrics (also supported by scikit-learn) are :
### Euclidean or L2
Euclidean distance is the “ordinary” straight-line distance between two points in Euclidean space. With this distance, Euclidean space becomes a metric space

<p align="center"> 
<img src="euclidean.jpeg">
</p>

### Manhattan or L1
Similar to Euclidean, but the distance is calculated by summing the absolute value of the difference between the dimensions. For eg., Manhattan distance implies moving straight, first along one axis and then along with the other.

<p align="center"> 
<img src="manhattan.jpeg">
</p>

The choice of linkage method entirely depends on you and there is no hard and fast method that will always give you good results. Different linkage methods lead to different clusters.

The point of doing all this is to demonstrate the way hierarchical clustering works, it maintains a memory of how we went through this process and that memory is stored in Dendrogram.

## What is a Dendrogram?

A Dendrogram is a type of tree diagram showing hierarchical relationships between different sets of data.

<p align="center"> 
<img src="img1.png">
</p>
As already said a Dendrogram contains the memory of hierarchical clustering algorithm, so just by looking at the Dendrgram you can tell how the cluster is formed.

**Note**:- 

Distance between data points represents dissimilarities.
Height of the blocks represents the distance between clusters.
So you can observe from the above figure that initially P5 and P6 which are closest to each other by any other point are combined into one cluster followed by P4 getting merged into the same cluster(C2). Then P1and P2 gets combined into one cluster followed by P0 getting merged into the same cluster(C4). Now P3 gets merged in cluster C2 and finally, both clusters get merged into one.

<p align="center"> 
<img src="gif2.gif">
</p>

A dendrogram can be a column graph (as in the image below) or a row graph. Some dendrograms are circular or have a fluid-shape, but the software will usually produce a row or column graph. No matter what the shape, the basic graph comprises the same parts:

The Clades are the branch and are arranged according to how similar (or dissimilar) they are. Clades that are close to the same height are similar to each other; clades with different heights are dissimilar — the greater the difference in height, the more dissimilarity.
Each clade has one or more leaves.
Leaves A, B, and C are more similar to each other than they are to leaves D, E, or F.
Leaves D and E are more similar to each other than they are to leaves A, B, C, or F.
Leaf F is substantially different from all of the other leaves.
A clade can theoretically have an infinite amount of leaves. However, the more leaves you have, the harder the graph will be to read with the naked eye.

<p align="center"> 
<img src="img4.jpeg">
</p>

One question that might have intrigued you by now is **how do you decide when to stop merging the clusters?**

You cut the dendrogram tree with a horizontal line at a height where the line can traverse the maximum distance up and down without intersecting the merging point.

<p align="center"> 
<img src="img2.png">
</p>

For example in the below figure L3 can traverse maximum distance up and down without intersecting the merging points. So we draw a horizontal line and the number of verticle lines it intersects is the optimal number of clusters.

![](img3.png)
