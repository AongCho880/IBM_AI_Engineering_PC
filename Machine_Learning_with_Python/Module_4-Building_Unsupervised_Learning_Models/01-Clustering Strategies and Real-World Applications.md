# Clustering Strategies in Real-World Applications

### Learning Objectives

After completing this lecture, students should be able to:

* Explain the concept of clustering and its applications.
* Apply k-means clustering for customer segmentation.
* Differentiate between partition-based, density-based, and hierarchical clustering.
* Analyze agglomerative and divisive hierarchical clustering approaches.
* Interpret dendrograms and clustering results.

---

## 1. Introduction to Clustering

<img width="1910" height="1056" alt="image" src="https://github.com/user-attachments/assets/cba30972-bf74-4020-be81-eefddc4979fa" />

### Definition

Clustering is a machine learning technique that automatically groups data points into clusters based on similarities.

* It works with **unlabeled data**.
* It discovers patterns independently.
* It can use **single or multiple features** to form clusters.

### Clustering vs Classification

| Aspect           | Classification             | Clustering                           |
| ---------------- | -------------------------- | ------------------------------------ |
| Learning Type    | Supervised                 | Unsupervised                         |
| Data Requirement | Labeled data               | Unlabeled data                       |
| Goal             | Predict categorical labels | Discover natural groupings           |
| Example          | Predict loan default       | Segment customers by characteristics |

In classification, a model (e.g., decision tree) is trained using labeled historical data to predict loan default status.

In clustering, a model such as k-means segments customers into groups without knowing default status.

---

## 2. Applications of Clustering

Clustering has multiple practical applications:

### 2.1 Exploratory Data Analysis

* Customer segmentation for targeted marketing.
* Discovering natural groupings in data.

### 2.2 Pattern Recognition

* Grouping similar objects.
* Image segmentation (e.g., detecting medical abnormalities).

### 2.3 Anomaly Detection

* Detecting fraud.
* Identifying equipment malfunctions.
* Detecting outliers.

### 2.4 Feature Engineering

* Creating new features.
* Reducing dimensionality.
* Improving model performance and interpretability.

### 2.5 Data Summarization

* Summarizing data into representative clusters.
* Replacing data points with cluster centers.
* Useful in image compression.

### 2.6 Feature Identification

* Identifying essential features distinguishing clusters.

---

## 3. Types of Clustering Methods

Clustering methods are categorized into three major types:

1. Partition-Based Clustering
2. Density-Based Clustering
3. Hierarchical Clustering

---

## 4. Partition-Based Clustering

### Definition

Partition-based algorithms divide data into **non-overlapping groups**.

### k-Means Clustering

* Identifies **k clusters**.
* Minimizes within-cluster variance.
* Efficient and scalable for large datasets.

### Visualization Example

<img width="1910" height="1052" alt="image" src="https://github.com/user-attachments/assets/e26b2601-c893-4e33-9e86-420147142401" />

**Figure 1:** Example of partition-based clustering generating three color-coded clusters. Each point belongs to exactly one cluster.

### Key Characteristics

* Requires predefined number of clusters (k).
* Works well when clusters are spherical and well-separated.
* Efficient for large datasets.

---

## 5. Density-Based Clustering

### Definition

Density-based clustering forms clusters based on dense regions of data points.

### Example: DBSCAN

* Can form clusters of **arbitrary shape**.
* Suitable for **irregular clusters**.
* Handles **noisy datasets** well.

### Visualization Example (Interlocking Shapes)

<img width="1908" height="1053" alt="image" src="https://github.com/user-attachments/assets/8969d63f-54f0-4227-9ea7-0c7bd88cc735" />


**Figure 2:** Partition-based clustering struggles with interlocking half-circles, while density-based clustering successfully separates irregular shapes (though may form small extra clusters).

### Key Characteristics

* Detects non-spherical clusters.
* Identifies noise points.
* Does not require specifying number of clusters in advance (depending on parameters).

---

## 6. Hierarchical Clustering

### Definition

Hierarchical clustering organizes data into a **tree of nested clusters**.

* Produces a **dendrogram**.
* Each node represents a cluster composed of child clusters.
* Effective for small to mid-sized datasets.

### Example Application

Genetic data analysis of over 900 dogs across 85 breeds and 200 wild grey wolves using 48,000 genetic markers. Animals are grouped by genetic similarity into a tree-like structure.

### Dendrogram Visualization

<img width="1903" height="1052" alt="image" src="https://github.com/user-attachments/assets/ef6af093-1340-468f-b212-4d87c512a213" />
<img width="979" height="531" alt="image" src="https://github.com/user-attachments/assets/5e5359d6-e5b8-440a-8584-5866e8c0b573" />


**Figure 1:** Example of hierarchical clustering represented as a dendrogram. The height indicates the distance at which clusters are merged or split.

---

## 7. Strategies in Hierarchical Clustering

There are two main strategies:

| Strategy      | Approach       | Process Direction |
| ------------- | -------------- | ----------------- |
| Agglomerative | Merge clusters | Bottom-up         |
| Divisive      | Split clusters | Top-down          |

---

## 8. Agglomerative Hierarchical Clustering

### Approach: Bottom-Up

#### Algorithm Steps

1. Select a distance metric (e.g., distance between centroids).
2. Initialize N clusters (each data point is its own cluster).
3. Compute an N × N distance matrix.
4. Repeat until stopping condition:

   * Merge the two closest clusters.
   * Update distance matrix.

### Distance Matrix

The distance matrix contains distances ( d_{ij} ) between each pair of points.

### Canadian Cities Example

* Start with six cities (six clusters).
* Identify closest pair (e.g., Montreal and Ottawa).
* Merge them into a parent cluster.
* Update distance matrix.
* Continue merging closest clusters.
* Final result: single cluster with full dendrogram.

Distance to new cluster calculated as midpoint between merged cities.

---

## 9. Divisive Hierarchical Clustering

### Approach: Top-Down

#### Algorithm Steps

1. Start with entire dataset as one cluster.
2. Partition into smaller clusters based on similarity.
3. Continue splitting until:

   * Desired number of clusters, or
   * Minimum cluster size reached.

---

## 10. Comparison of Clustering Methods

| Method          | Cluster Shape     | Scalability           | Handles Noise | Tree Structure   |
| --------------- | ----------------- | --------------------- | ------------- | ---------------- |
| Partition-Based | Usually spherical | High                  | Limited       | No               |
| Density-Based   | Arbitrary shapes  | Moderate              | Yes           | No               |
| Hierarchical    | Any               | Small–Medium datasets | Depends       | Yes (Dendrogram) |

---

## 11. Key Concepts and Terms

* Cluster: Group of similar data points.
* Distance Matrix: Matrix of pairwise distances.
* Dendrogram: Tree-like diagram showing hierarchical relationships.
* Bottom-Up: Start with individual points and merge.
* Top-Down: Start with all points and split.

---

## 12. Summary of Key Takeaways

* Clustering is an unsupervised learning technique that groups similar data points.
* It differs from classification because it does not use labeled data.
* Major types:

  * Partition-based (e.g., k-means)
  * Density-based (e.g., DBSCAN)
  * Hierarchical (agglomerative and divisive)
* k-means is efficient and scalable but assumes spherical clusters.
* Density-based clustering handles irregular shapes and noise.
* Hierarchical clustering produces a dendrogram representing nested cluster relationships.
* Agglomerative clustering follows a bottom-up merging approach.
* Divisive clustering follows a top-down splitting approach.
* Clustering is widely used in segmentation, anomaly detection, image processing, and data summarization.

---
