# K-Means Clustering

### Learning Objectives

After completing this lecture, students should be able to:

* Describe K-Means clustering.
* Explain how the K-Means algorithm works.
* Discuss how to determine the appropriate value of K.
* Analyze strengths and limitations of K-Means.

---

## 1. Introduction to K-Means Clustering

### Definition

K-Means is an **iterative, centroid-based clustering algorithm** that partitions a dataset into similar groups based on the distance between their centroids.

* It divides data into **k non-overlapping clusters**.
* The value of **k is a chosen parameter**.
* Clusters are constructed to:

  * Minimize variance within clusters.
  * Maximize dissimilarity between clusters.

---

## 2. Core Concept: Centroid and Cluster Formation

A **centroid** is the average position of all data points in a cluster.

* Data points closest to a centroid are assigned to that cluster.
* The centroid represents the center of the cluster.

<p align="center">
  <img width="420" alt="image" src="https://github.com/user-attachments/assets/d3297c09-5f9d-468e-b600-df4070bc42a9" />
  <img width="420" alt="image" src="https://github.com/user-attachments/assets/bf785a58-72ce-4228-adf3-2a5986fed49d" />
</p>

**Figure 1:** A cluster of data points with its centroid marked by an “X”. The centroid represents the mean location of all points in the cluster.

### Effect of K Value

* Higher K → Smaller clusters, more detail.
* Lower K → Larger clusters, less detail.

---

## 3. The K-Means Algorithm: Step-by-Step

### Step 1: Initialization

* Choose the number of clusters (K).
* Randomly select K initial centroid locations.

  * These can be data points or arbitrary points in feature space.

### Step 2: Assignment

* Compute the distance between each point and each centroid.
* Form a distance matrix.
* Assign each data point to the nearest centroid.

### Step 3: Update

* Recalculate each centroid as the mean of its assigned points.

### Step 4: Repeat

* Repeat Assignment and Update steps.
* Stop when:

  * Centroids stop moving, or
  * Maximum iterations are reached.

The algorithm **converges** when centroids stabilize.

<img width="1912" height="1050" alt="image" src="https://github.com/user-attachments/assets/83df73fa-b443-4f6d-9c43-ed336ea9f6fe" />

---

## 4. Iterative Convergence Behavior

In iterative demonstrations:

* Initial centroids are randomly placed.
* With each iteration:

  * Points are reassigned.
  * Centroids move closer to optimal positions.
* When two consecutive iterations are identical, convergence is reached.

Even after convergence:

* A few mislabeled points may remain.
* K-Means generally separates well-formed clusters effectively.

---

## 5. Assumptions and Limitations

### 5.1 Imbalanced Clusters

K-Means does not perform well when clusters differ significantly in size.

<img width="1902" height="1052" alt="image" src="https://github.com/user-attachments/assets/bd1e84d5-420d-4268-a018-07d43fa3b909" />

Example:

* One cluster: 200 points
* Another cluster: 10 points

Observation:

* Smaller cluster centroid may drift toward larger cluster.
* Larger cluster may absorb smaller cluster’s points.

---

### 5.2 Convex Cluster Assumption

K-Means assumes clusters are **convex**.

Convex cluster:

* Any line between two points remains inside the cluster.

Non-convex clusters:

* K-Means struggles to represent them correctly.

<img width="1911" height="1054" alt="image" src="https://github.com/user-attachments/assets/f6904c76-e17d-4b32-97f9-477f2b7f060b" />

**Figure 1:** Non-convex clusters (blue points). The red boundary represents the convex hull. K-Means assumes convex cluster shapes.

---

### 5.3 Sensitivity to Noise

* K-Means minimizes variance.
* Variance is sensitive to outliers.
* Noise can significantly distort cluster centroids.

---

### 5.4 Equal Cluster Size Assumption

K-Means assumes clusters contain approximately equal numbers of points.

---

## 6. Objective Function of K-Means

The goal is to minimize the **within-cluster variance** for all clusters simultaneously.

Mathematically:

$$
\sum_{i=1}^{k} \sum_{x \in C_i} ||x - \mu_i||^2
$$

Where:

* $( C_i )$ = Cluster i
* $( x )$ = Data point
* $( \mu_i )$ = Centroid of cluster i
* $( ||x - \mu_i||^2 )$ = Squared distance between point and centroid

This is a **double summation** over:

1. Each cluster
2. Each point within that cluster

---

## 7. Experimental Observations

### Effect of Standard Deviation

Using three blobs with increasing standard deviation:

* Std = 1 → Clusters well-separated → K-Means performs well.
* Std = 4 → Some overlap → Some errors appear.
* Std = 15 → Heavy overlap → Clusters visually indistinguishable.

Observations:

* As dispersion increases:

  * Cluster centroids move closer together.
  * Separation becomes difficult.
* When features cannot separate classes, clustering fails.
* Additional features may be required.

<img width="1911" height="1051" alt="image" src="https://github.com/user-attachments/assets/28071a63-ee0b-4264-9945-af2174b235ff" />

**Figure 1:** K-Means clustering results for three blobs with varying standard deviations. Increased dispersion reduces separability.

---

## 8. When K Is Incorrect

### Case 1: K Too Small (e.g., K = 2, True Classes = 3)

<img width="1903" height="1052" alt="image" src="https://github.com/user-attachments/assets/37f9f807-04d6-407d-a350-d806c5cff0d6" />

* K-Means merges two blobs.
* The centroid is placed between them.

### Case 2: K Too Large

<img width="1912" height="1056" alt="image" src="https://github.com/user-attachments/assets/8cb82ea2-56bc-4b4d-bce6-b340b2267b3d" />

* K-Means forces additional clusters.
* Results may become meaningless.

As standard deviation increases:

* Blobs gradually merge.
* A blob can have only one centroid.

---

## 9. Choosing the Best Value of K

Choosing K is challenging, especially in high-dimensional spaces.

### 9.1 Data Separability

* Easy to visualize in 2D or 3D.
* Hard to detect in higher dimensions.
* Use pairwise scatter plots for insight.

---

### 9.2 Heuristic Techniques

| Method               | Description                                                                                  |
| -------------------- | -------------------------------------------------------------------------------------------- |
| Silhouette Analysis  | Measures cohesion (within-cluster similarity) and separation (between-cluster dissimilarity) |
| Elbow Method         | Plots objective function vs K; look for “elbow” point                                        |
| Davies-Bouldin Index | Measures cluster similarity ratio; lower values indicate better clustering                   |

These techniques help evaluate clustering performance for different K values.

---

## 10. Strengths and Limitations Summary

### Strengths

* Efficient and scalable.
* Works well for large datasets.
* Simple to implement.
* Effective for well-separated convex clusters.

### Limitations

* Requires predefined K.
* Assumes convex clusters.
* Struggles with imbalanced clusters.
* Sensitive to noise and outliers.
* Performs poorly with overlapping clusters.

---

## 11. Key Takeaways

* K-Means is an iterative, centroid-based clustering algorithm.
* It partitions data into K non-overlapping clusters.
* It minimizes within-cluster variance.
* The algorithm alternates between assignment and centroid update.
* Convergence occurs when centroids stop moving.
* Assumes convex clusters and similar cluster sizes.
* Sensitive to noise and imbalanced clusters.
* Choosing K requires heuristic techniques such as:

  * Silhouette analysis
  * Elbow method
  * Davies-Bouldin index

---
