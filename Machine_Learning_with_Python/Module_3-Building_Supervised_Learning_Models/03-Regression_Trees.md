# 📘 Regression Trees — Complete & Simple Notes

## 1️⃣ What is a Regression Tree?

A **Regression Tree** is a type of Decision Tree used to predict **continuous values** instead of categories.

It is similar to a Decision Tree, but:

* ✅ **Classification Tree → Predicts classes (e.g., Spam / Not Spam)**
* ✅ **Regression Tree → Predicts numbers (e.g., Salary, Temperature)**


## 2️⃣ Classification vs Regression Trees

| Feature              | Classification Tree | Regression Tree          |
| -------------------- | ------------------- | ------------------------ |
| Target Variable      | Categorical         | Continuous               |
| Example Output       | Yes / No            | 25.4°C                   |
| Leaf Node Prediction | Majority class      | Average value            |
| Split Measure        | Entropy / Gini      | MSE (Mean Squared Error) |


## 3️⃣ Structure of a Regression Tree

A regression tree looks just like a decision tree:

* **Internal Node** → Feature test
* **Branch** → Split result
* **Leaf Node** → Predicted numerical value


## 🌳 Example Structure of a Regression Tree

![Image](https://www.researchgate.net/publication/325712556/figure/fig1/AS%3A636637654552580%401528797653733/Example-of-a-regression-tree-Panel-a-with-the-partition-of-the-covariates-space-Panel.png)

![Image](https://explained.ai/decision-tree-viz/images/knowledge-TD-3-X.png)

![Image](https://miro.medium.com/v2/resize%3Afit%3A1400/1%2AjpGw17zZja27t6zNBIyA5g.png)

![Image](https://backend.aionlinecourse.com/uploads/tutorials/2019/05/28_1_Decision_tree_Regression.png)

![Image](https://miro.medium.com/v2/resize%3Afit%3A836/0%2Asyr-lBht29vPjWc8)

At each leaf, the prediction is:

$$
\hat{y} = \text{Average of target values in that node}
$$


## 4️⃣ How Does a Regression Tree Work?

The tree is built by **recursively splitting the dataset**.

### Steps:

1. Start with all training data
2. Choose the best feature and threshold
3. Split the data into two groups
4. Calculate prediction (mean value) for each group
5. Repeat until stopping criteria is met

This reduces **variance** in the target values.


## 5️⃣ How Does It Choose the Best Split?

Unlike classification trees (which use entropy), regression trees use:

 ✅ **Mean Squared Error (MSE)**


## 6️⃣ What is MSE?

MSE measures the average squared difference between:

$$
\text{Actual value} - \text{Predicted value}
$$

$$
MSE = \frac{1}{n} \sum (y_i - \hat{y})^2
$$

### Interpretation:

* Small MSE → Good split (values are close together)
* Large MSE → Bad split (values are scattered)

👉 MSE measures **variance** in a node.


## 7️⃣ Weighted MSE for Splitting

When a node is split into Left and Right:

$$
\text{Weighted MSE} =
\frac{n_L}{n} MSE_L + \frac{n_R}{n} MSE_R
$$

Where:

* ( $n_L$ ) = number of samples in left node
* ( $n_R$ ) = number of samples in right node
* ( $n$ ) = total samples

### Goal:

Choose the split with the **lowest weighted MSE**

Lower MSE = Lower variance = Better prediction


## 📉 MSE-Based Splitting Visualization

![Image](https://miro.medium.com/1%2A62Am0QdlxCq5Vmt5siR-7Q.png)

![Image](https://www.researchgate.net/publication/366879033/figure/fig1/AS%3A11431281111409500%401672963502579/Schematic-diagrams-of-decision-tree-a-and-random-forest-b-models-for-regression-MSE.ppm)

![Image](https://scikit-learn.org/stable/_images/sphx_glr_plot_tree_regression_001.png)

![Image](https://www.researchgate.net/publication/325712556/figure/fig1/AS%3A636637654552580%401528797653733/Example-of-a-regression-tree-Panel-a-with-the-partition-of-the-covariates-space-Panel.png)

![Image](https://christophm.github.io/interpretable-ml-book/tree_files/figure-html/fig-tree-artificial-1.png)

The algorithm tests multiple splits and selects the one that **minimizes prediction error**.


## 8️⃣ How Splitting Works for Different Feature Types

### 🔹 Continuous Feature

Example: Age

1. Sort values
2. Remove duplicates
3. Create thresholds at midpoints:
   $$
   \alpha_i = \frac{x_i + x_{i+1}}{2}
   $$
4. Test each threshold
5. Select threshold with lowest weighted MSE

⚠️ This exhaustive search is slow for very large datasets.

For big data:

* Use fewer sampled thresholds
* Trade accuracy for speed


### 🔹 Binary Feature

Example: Gender (Male / Female)

* Only one possible split
* Separate into two groups
* Compute weighted MSE
* Done


### 🔹 Multi-Class Feature

Example: Region (North, South, East)

Use strategies like:

* One-Versus-All
* One-Versus-One

Convert to binary splits, then compute weighted MSE.


## 9️⃣ Prediction at a Leaf Node

For regression trees:

$$
\hat{y} = \text{Mean of target values}
$$

Alternative:

* Median (better for skewed data)
* Mean (faster & common choice)


## 🔟 Applications of Regression Trees

Used when predicting **numeric values**:

* Revenue prediction
* Salary estimation
* Temperature forecasting
* Wildfire risk prediction
* House price prediction


## 1️⃣1️⃣ Why Minimize Variance?

Variance shows how spread out values are.

* High variance → Poor prediction
* Low variance → Accurate grouping

Regression Trees aim to:

> ✅ Minimize variance
> ✅ Minimize MSE
> ✅ Improve prediction accuracy


## 1️⃣2️⃣ Summary (Quick Revision)

### ✔ Definition

Regression Tree predicts continuous values.

### ✔ Difference from Classification

Classification → Categories
Regression → Numbers

### ✔ Leaf Output

Average value of targets

### ✔ Split Measure

Mean Squared Error (MSE)

### ✔ Best Split

Split with lowest weighted MSE

### ✔ Continuous Feature

Try thresholds between sorted values


## 🎯 Final Conclusion

A Regression Tree is a decision-tree-based algorithm used for predicting continuous values. Instead of using entropy or Gini impurity, it selects splits by minimizing Mean Squared Error (MSE). At each leaf node, it predicts the average of the target values. By recursively splitting data to reduce variance, regression trees improve prediction accuracy and are widely used for numeric forecasting problems.

---
