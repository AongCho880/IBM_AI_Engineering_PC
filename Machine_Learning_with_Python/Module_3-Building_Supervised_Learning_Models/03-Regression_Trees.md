# 📘 Comprehensive Notes on **Regression Trees** (with Corrections)

## 📌 Introduction

A **Regression Tree** is a type of decision tree that is used to **predict continuous values** (numbers), such as:

* House prices
* Temperature
* Salary
* Revenue

Unlike classification trees, regression trees do **not** predict categories. They predict **numerical values**.

These notes are based on the lecture content , including the important corrections mentioned in the errata.


## 1️⃣ Classification Trees vs Regression Trees

<img width="1908" height="1051" alt="image" src="https://github.com/user-attachments/assets/f02e4b85-28db-4f2e-9514-6859a3c0aaed" />


| Feature              | Classification Tree                 | Regression Tree                 |
| -------------------- | ----------------------------------- | ------------------------------- |
| Target Type          | Categorical (Yes/No, Spam/Not Spam) | Continuous (Price, Score, Temp) |
| Output               | Class label                         | Number                          |
| Leaf Node Prediction | Majority class                      | Average value                   |
| Main Metric          | Entropy / Gini                      | MSE / Variance                  |

### ✅ Example

* **Classification**: Is this email spam? → Yes / No
* **Regression**: What is the house price? → ৳45,00,000

So:

> 📌 Regression trees are used when output is a **number**, not a category.


## 2️⃣ Structure of a Regression Tree

A regression tree looks like an **upside-down tree**:

* Root node → First split
* Internal nodes → More splits
* Leaf nodes → Final prediction (number)

### 🌳 Example Structure

<img width="1910" height="1050" alt="image" src="https://github.com/user-attachments/assets/fb7d9338-15a4-418d-94f1-ac2d395215ea" />
<img width="713" height="258" alt="image" src="https://github.com/user-attachments/assets/e63924dd-7c1d-48cf-be64-17bbec0a0106" />
<img width="500" height="400" alt="image" src="https://github.com/user-attachments/assets/d6545b2b-c387-4913-9332-b36eb56ee8fd" />

### 📍 How Prediction Works

<img width="1899" height="1049" alt="image" src="https://github.com/user-attachments/assets/1260b8c4-4a03-4a95-a512-f626912124b4" />

At each **leaf node**, prediction is:

$$
\hat{y} = \frac{1}{n}\sum y_i
$$

That means:

> ✅ Take the **average** of target values in that node.

Example:

If a leaf contains prices:
40, 45, 50 → Prediction = 45


## 3️⃣ How Regression Trees Are Built (Main Idea)

### ❌ Wrong Statement (From Video)

The video said:

> “Minimizes randomness of classes”

This is **wrong** for regression.

### ✅ Correct Statement

> Regression trees split data to **minimize variance / MSE** of target values.

### 📌 Correct Goal

Regression trees try to:

✔ Make values in each node **as similar as possible**
✔ Reduce spread (variance)
✔ Improve prediction accuracy

So the main objective is:

> 🎯 **Minimize Mean Squared Error (MSE)**


## 4️⃣ Mean Squared Error (MSE) in Regression Trees

<img width="1915" height="1058" alt="image" src="https://github.com/user-attachments/assets/a0867ec3-7163-4d48-ac6c-a455645989b3" />
<img width="1888" height="1033" alt="image" src="https://github.com/user-attachments/assets/f4b92d87-be66-4b0b-b0e1-6dfeec89ff8e" />

### 📐 What is MSE?

MSE measures how far predictions are from actual values.

$$
MSE = \frac{1}{n}\sum (y_i - \hat{y})^2
$$

Where:

* $(y_i)$ = actual value
* $(\hat{y})$ = predicted value
* $(n)$ = number of samples

### 📌 Interpretation

| MSE Value | Meaning         |
| --------- | --------------- |
| Low       | Good prediction |
| High      | Poor prediction |

Lower MSE = Better split ✅


### 📊 Visualizing MSE-Based Splitting

<img width="1024" height="576" alt="image" src="https://github.com/user-attachments/assets/9dddca67-f2f9-4f3c-ba94-8e98415421b2" />
<img width="907" height="826" alt="image" src="https://github.com/user-attachments/assets/9cb4e21e-139b-4ca9-aa60-0bb0ab3c8d80" />
<img width="672" height="480" alt="image" src="https://github.com/user-attachments/assets/134cf6d1-bc86-441f-bfa0-48c23f202812" />
<img width="1456" height="899" alt="image" src="https://github.com/user-attachments/assets/d49d6896-cdb2-4a67-8bc3-17bfd3874906" />


## 5️⃣ How Splits Are Evaluated (Weighted MSE)

When a node is split into:

* Left node
* Right node

We compute:

$$
Weighted\ MSE =
\frac{n_L}{n}MSE_L + \frac{n_R}{n}MSE_R
$$

Where:

| Symbol | Meaning               |
| ------ | --------------------- |
| (n_L)  | Samples in left node  |
| (n_R)  | Samples in right node |
| (n)    | Total samples         |

### 📌 Why Weighted?

Because:

* Bigger nodes should influence more
* Small nodes should influence less

So:

> 🎯 Best split = **Lowest weighted MSE**


## 6️⃣ Splitting Continuous Features

<img width="1904" height="1052" alt="image" src="https://github.com/user-attachments/assets/480a3017-dd6b-4075-9f22-d9a654cb04fb" />

For continuous features (like age, income):

### Step-by-Step Method

1️⃣ Sort values:

$$
x_1 \le x_2 \le x_3 \le ...
$$

2️⃣ Remove duplicates

3️⃣ Find midpoints:

$$
\alpha_i = \frac{x_i + x_{i+1}}{2}
$$

4️⃣ Try each α as threshold

5️⃣ Choose α with lowest MSE

### 📌 Example

Ages: 20, 25, 30

Thresholds:

* (20+25)/2 = 22.5
* (25+30)/2 = 27.5

Test both → Pick best

### ⚠ Limitation

This method is:

❌ Slow for big data
❌ Needs optimization

So in large datasets, only some thresholds are sampled.


## 7️⃣ Splitting Categorical Features (Corrected)

### ❌ Wrong Statement (From Video)

The video said:

> Use one-vs-one or one-vs-all

This is for **classification**, not regression.

### ✅ Correct Statement

> Evaluate different binary partitions of categories and choose the one with lowest MSE.


### 📌 Correct Method

Suppose feature = Color:

{Red, Blue, Green}

Possible splits:

| Left    | Right         |
| ------- | ------------- |
| {Red}   | {Blue, Green} |
| {Blue}  | {Red, Green}  |
| {Green} | {Red, Blue}   |

For each:

1. Split data
2. Compute MSE
3. Choose best

So:

> ✔ No classification strategy is used
> ✔ Only MSE minimization


## 8️⃣ Training Process of Regression Tree

During training:

### Algorithm Steps

1️⃣ Start with all data at root
2️⃣ Try all possible splits
3️⃣ Compute weighted MSE
4️⃣ Select best split
5️⃣ Repeat recursively
6️⃣ Stop when condition met

### Stopping Conditions

Tree stops when:

✔ Max depth reached
✔ Node has few samples
✔ MSE is already small
✔ No improvement

This avoids **overfitting**.


## 9️⃣ Applications of Regression Trees

### 📈 Real-Life Uses

| Field       | Example            |
| ----------- | ------------------ |
| Finance     | Revenue prediction |
| Environment | Temperature        |
| Insurance   | Risk estimation    |
| Real Estate | House price        |
| Forestry    | Wildfire risk      |


## 🔟 Summary of Key Corrections (Errata)

| Video Part  | Wrong                  | Correct                        |
| ----------- | ---------------------- | ------------------------------ |
| 01:26–01:39 | Talks about “classes”  | Should talk about MSE/variance |
| 04:09–04:20 | One-vs-All, One-vs-One | Use binary partitions          |

### ✅ Correct Understanding

> Regression trees minimize **variance**, not class impurity.


## 📌 Final Key Points (Exam-Friendly)

### ✔ Important Notes

* Regression trees predict **numbers**
* Leaf output = **Average value**
* Main metric = **MSE**
* Best split = **Lowest weighted MSE**
* No classification strategies
* Continuous → Thresholds
* Categorical → Binary partitions

### ✔ One-Line Definition

> A regression tree is a decision tree that predicts continuous values by recursively splitting data to minimize mean squared error.

---

