# Bias, Variance, and Ensemble Models

### Learning Objectives

After studying this lecture, you should be able to:

* Analyze the impact of bias and variance on accuracy and precision
* Explain prediction bias and prediction variance
* Describe the bias–variance tradeoff in relation to model complexity
* Evaluate techniques to mitigate bias and variance
* Analyze the outcomes of bagging and boosting methods 

---

## Understanding Bias and Variance

### Dartboard Analogy

<img width="1912" height="1053" alt="image" src="https://github.com/user-attachments/assets/58896adf-1dcb-4bd4-aa2b-4565c1ecb3cf" />
<img width="1908" height="1052" alt="image" src="https://github.com/user-attachments/assets/07ca5865-802a-4851-9628-af1e1dc759c5" />
<img width="1151" height="411" alt="image" src="https://github.com/user-attachments/assets/14d7fdb0-4db8-4b69-92b7-76bf0a679c37" />

**Figure 1: Dartboard illustration of bias and variance.**
Closely grouped darts near the center indicate low bias (high accuracy) and low variance (high precision). Spread-out darts indicate high variance. Darts far from the center indicate high bias.

Bias and variance can be understood using dartboards:

* **Bias** refers to how far predictions are from the true target (center of the board).

  * Low bias → darts near center (high accuracy)
  * High bias → darts far from center (low accuracy)

* **Variance** refers to how spread out predictions are (precision).

  * Low variance → darts tightly grouped
  * High variance → darts widely scattered

To achieve a high score, we need **low bias and low variance**. 

---

## Prediction Bias

### Definition

Prediction bias is the **average difference between model predictions and actual target values**.

* A perfect model has **zero bias**.
* Higher bias means predictions consistently deviate from true values. 

### Example Illustration

<img width="1909" height="1053" alt="image" src="https://github.com/user-attachments/assets/4a53f417-3589-4d41-bbc4-bf62890c35bb" />
<img width="1912" height="1054" alt="image" src="https://github.com/user-attachments/assets/5819998c-fd75-4951-9f54-4dc71b020891" />

**Figure 2: Illustration of prediction bias.**
The blue line represents a fitted regression model with small bias. The red shifted line has much larger bias.

* A linear ordinary least squares fit may have small bias (e.g., 0.22).
* Shifting the same model downward increases bias significantly (e.g., 4.22). 

---

## Prediction Variance

<img width="1909" height="1057" alt="image" src="https://github.com/user-attachments/assets/19afcf54-4f8b-4d61-ae35-7f997787fc49" />

### Definition

Prediction variance measures how much a model’s predictions **change when trained on different subsets of the same dataset**. 

* High variance → Model is sensitive to small changes in training data

* Leads to **overfitting**

* Tracks noise and outliers

* Low variance → Model is stable

* Generalizes better to unseen data 

### Example Explanation

When multiple models are trained on different random samples of nonlinear data:

* If curves align closely → Low variance
* If curves differ significantly → High variance

This instability reflects prediction variance. 

---

## Bias–Variance Tradeoff

<img width="1907" height="1056" alt="image" src="https://github.com/user-attachments/assets/87116ad9-453d-4c3d-a318-6ce8c125fb63" />

**Figure 3: Bias–variance tradeoff curve.**
As model complexity increases, bias decreases and variance increases. The optimal model lies near the crossover point.

As model complexity increases:

| Model Complexity | Bias     | Variance | Outcome       |
| ---------------- | -------- | -------- | ------------- |
| Low              | High     | Low      | Underfitting  |
| Medium           | Balanced | Balanced | Optimal model |
| High             | Low      | High     | Overfitting   |

Key observations:

* Increasing complexity → Bias decreases
* Increasing complexity → Variance increases
* There is always some unavoidable **generalization error** (e.g., random noise). 

---

## Underfitting and Overfitting

* **Underfitting**

  * High bias
  * Poor performance even on training data

* **Overfitting**

  * High variance
  * Good training performance
  * Poor unseen data performance 

---

## Weak and Strong Learners

### Weak Learner

* Performs slightly better than random guessing
* High bias
* Low variance
* Tends to underfit 

### Strong Learner

* Low bias
* High variance
* Tends to overfit 

---

## Ensemble Methods

Ensemble methods combine multiple models to balance bias and variance. 

Decision or regression trees are often used as base learners because:

* Their bias and variance can be adjusted by changing tree depth. 

---

## Bagging (Bootstrap Aggregating)

<img width="1909" height="1051" alt="image" src="https://github.com/user-attachments/assets/dca42cce-ab27-468e-abd5-f814d1240062" />

### Concept

Bagging trains the same model multiple times on **bootstrapped subsets** of data and averages predictions. 

### Effect

* Reduces prediction variance
* Lowers risk of overfitting
* Slightly increases bias 

### Random Forests

Random forests:

* Train multiple decision trees on bootstrapped datasets
* Trees do not need to be very deep
* Aggregation reduces high variance of shallow trees 

---

## Boosting

### Concept

Boosting builds a sequence of weak learners:

* Each new learner corrects errors of the previous one
* Final model is a **weighted sum** of weak learners 

### Reweighting Process

* Increase weights of misclassified samples
* Decrease weights of correctly classified samples
* Update model weights based on performance 

### Popular Boosting Algorithms

* Gradient Boosting
* XGBoost
* AdaBoost 

---

<img width="1907" height="1054" alt="image" src="https://github.com/user-attachments/assets/c5e97172-6056-4eae-a985-e658ca22e8f5" />

## Bagging vs Boosting

| Feature       | Bagging                 | Boosting                |
| ------------- | ----------------------- | ----------------------- |
| Main Goal     | Reduce variance         | Reduce bias             |
| Training      | Parallel                | Sequential              |
| Base Learners | High variance, low bias | Low variance, high bias |
| Data Sampling | Bootstrapped subsets    | Reweighted data         |
| Effect        | Mitigates overfitting   | Mitigates underfitting  |

Bagging reduces variance.
Boosting increases model complexity and reduces bias. 

---

## Key Takeaways

* Bias measures prediction accuracy; variance measures prediction stability.
* High bias → Underfitting.
* High variance → Overfitting.
* Increasing model complexity reduces bias but increases variance.
* The bias–variance tradeoff determines optimal model complexity.
* Weak learners have high bias; strong learners have high variance.
* Bagging reduces variance through averaging.
* Random forests apply bagging to decision trees.
* Boosting reduces bias by sequentially correcting errors. 

---
