## Supervised Learning with K-Nearest Neighbors (KNN)

### Learning Objectives

After this lecture, you should be able to:

* Explain what K-Nearest Neighbors (KNN) is
* Describe how the KNN algorithm works
* Discuss how the value of **K** affects the outcome of the algorithm

---

## 1. Introduction to K-Nearest Neighbors (KNN)

### 1.1 Definition

**K-Nearest Neighbors (KNN)** is a **supervised machine learning algorithm** that:

* Uses a group of **labeled data points**
* Learns from them
* Predicts the label of new, unseen data points

KNN can be used for:

* **Classification**
* **Regression**

---

### 1.2 Core Idea of KNN

<img width="1907" height="1053" alt="image" src="https://github.com/user-attachments/assets/e08cd8eb-1e00-440b-b10c-9cec39238c24" />

In KNN:

* Data points close to each other are called **neighbors**.
* Points that are close usually have **similar features**.
* Therefore, they are likely to belong to the **same class** (in classification).

To apply KNN, we must define mathematically what is meant by “nearest” (distance between data points).

---

## 2. How KNN Works

### 2.1 KNN for Classification

<img width="1905" height="1045" alt="image" src="https://github.com/user-attachments/assets/e07f59f0-51cd-4b24-8d84-5674e6396b8c" />

The steps are:

1. Choose a value for **K**
2. Calculate the distance between the query (unlabeled) point and all labeled training points
3. Find the **K nearest neighbors**
4. Predict the class using **majority voting**

---

### 2.2 KNN for Regression

In regression:

* Instead of majority voting,
* The prediction is calculated using the **average** or **median** of the target values of the K nearest neighbors.

---

## 3. Iris Dataset Example

<img width="1905" height="1049" alt="image" src="https://github.com/user-attachments/assets/85faea4f-cbb4-46bb-a888-5b3e5b0d230a" />

The lecture uses the **Iris dataset**, which contains:

* 50 samples of each species:

  * Iris setosa
  * Iris versicolor
  * Iris virginica

Each sample has four features (in cm):

* Sepal length
* Sepal width
* Petal length
* Petal width

We train KNN to classify iris types using these features.

---

## 4. Visual Understanding of KNN

### Figure 1: KNN Neighbor Selection (K = 3)

<img width="1906" height="1051" alt="image" src="https://github.com/user-attachments/assets/101f4e65-46ad-467e-8bfd-bada16f31d24" />
<img width="1909" height="1052" alt="image" src="https://github.com/user-attachments/assets/490ee18f-39fc-464d-bf7a-38f33a1627d8" />
<img width="850" height="521" alt="image" src="https://github.com/user-attachments/assets/817fedbe-c721-4a0b-a052-c84b534f7498" />

**Explanation:**
For a query point (inside the circle), the algorithm:

* Finds the 3 nearest neighbors
* Checks their class labels
* Assigns the class with the majority vote

If 2 out of 3 neighbors belong to "virginica", the new point is classified as virginica.

However, if neighbors are mixed, misclassification may occur.

---

### Figure 2: Decision Boundary for K = 3

<img width="1902" height="1049" alt="image" src="https://github.com/user-attachments/assets/6eeb00f6-2cc1-4898-88ad-c3a6a781c122" />
<img width="1200" height="500" alt="image" src="https://github.com/user-attachments/assets/86c33a4c-49bf-4792-b4b1-25684b99d752" />

**Explanation:**
The colored regions represent predicted classes.

* Each region corresponds to a predicted iris type.
* The boundary between colors is the **decision boundary**.
* In the lecture example, the model achieved **93% accuracy**.

---

## 5. Choosing the Optimal Value of K

<img width="1897" height="1051" alt="image" src="https://github.com/user-attachments/assets/c720c55b-895f-4b39-b370-8fc3a3d634e4" />

To find the best K:

1. Choose a range of K values (e.g., 1, 2, 3, 4, ...)
2. Train the model
3. Evaluate accuracy on a test dataset
4. Select the K with the highest accuracy

Example from lecture:

<img width="1907" height="1047" alt="image" src="https://github.com/user-attachments/assets/c171c37e-e86c-4777-8fa6-25b17cda4aff" />

* K = 4 gave the best accuracy.

---

## 6. KNN as a Lazy Learner

<img width="1904" height="1050" alt="image" src="https://github.com/user-attachments/assets/626ba4ad-7c4c-4c38-86cb-cb51b6069adf" />

KNN is called a **lazy learner** because:

* It does not build a model during training.
* It simply stores the training data.
* For each new query:

  * It computes distance to all training points
  * Sorts them
  * Selects the top K

Thus, prediction time can be computationally expensive.

---

## 7. Effect of K on Model Behavior

| Value of K | Model Behavior           | Problem             |
| ---------- | ------------------------ | ------------------- |
| Small K    | Sensitive to noise       | Overfitting         |
| Large K    | Smooth decision boundary | Underfitting        |
| Moderate K | Balanced                 | Optimal performance |

### Explanation

* **Small K** → Predictions fluctuate → Overfitting
* **Large K** → Oversmoothing → Underfitting
* Best K lies somewhere in between

---

## 8. Challenges in KNN

<img width="1908" height="1048" alt="image" src="https://github.com/user-attachments/assets/e78d7a87-227a-4170-a293-5fea6f290768" />

### 8.1 Skewed Class Distribution

When one class has many more samples:

* Majority voting becomes biased.
* Frequent classes dominate predictions.

#### Solution:

* Use **distance-weighted voting**
* Closer neighbors have more influence

---

### 8.2 Feature Scaling Problem

If features have very large values:

* They dominate the distance calculation.
* This leads to biased predictions.

#### Solution:

* Apply **standardization**
* Scale features to comparable ranges

---

### 8.3 Irrelevant and Noisy Features

* Irrelevant features add noise.
* Noise increases optimal K.
* Higher K increases computational cost.
* Accuracy may decrease.

#### Solution:

* Keep only **relevant features**
* Use domain knowledge
* Compare performance:

  * With feature
  * Without feature

---

## 9. Feature Relevance and Model Performance

| Feature Type | Effect on Model               |
| ------------ | ----------------------------- |
| Relevant     | Improves accuracy             |
| Irrelevant   | Adds noise                    |
| Redundant    | Increases computation         |
| Scaled       | Improves fairness in distance |

To test feature importance:

* Tune K with the feature
* Tune K without the feature
* Compare performance

<img width="1907" height="1052" alt="image" src="https://github.com/user-attachments/assets/0c8b40c1-0d04-4b32-ac16-0d4fd7822c99" />

---

## 10. Summary of Key Concepts

### Key Points

* KNN is a **supervised learning algorithm**
* Used for **classification and regression**
* Works by finding the **K nearest neighbors**
* Classification uses **majority voting**
* Regression uses **average or median**
* Optimal K is found using test accuracy
* Small K → Overfitting
* Large K → Underfitting
* KNN is a **lazy learner**
* Feature scaling is essential
* Distance-weighted voting helps in skewed datasets
* Removing irrelevant features improves performance and efficiency

---

## Final Takeaways

* KNN predicts based on similarity.
* Choosing the correct K is crucial.
* Feature scaling and feature selection significantly affect performance.
* KNN is simple but computationally intensive.
* Balanced class distribution and relevant features improve results.
