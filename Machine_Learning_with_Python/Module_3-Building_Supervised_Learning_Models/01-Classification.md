# 📘 Comprehensive Notes on **Classification in Machine Learning**


## 1️⃣ What is Classification?

**Classification** is a **supervised machine learning** method used to predict **categories (labels)** from data.

### 📌 Key Idea

* Input → Features (age, income, marks, etc.)
* Output → Label (Yes/No, Spam/Not Spam, Class A/B/C)

> ✅ Classification predicts **discrete values**, not numbers.

### 📍 Example

| Input         | Output                 |
| ------------- | ---------------------- |
| Email text    | Spam / Not Spam        |
| Customer data | Will Leave / Will Stay |


## 2️⃣ Supervised Learning in Classification

In classification:

✔ Data is **labeled**
✔ Model learns from examples
✔ Then predicts new data

### Learning Process

<img width="850" height="505" alt="image" src="https://github.com/user-attachments/assets/6b882862-74d7-4f77-81e3-948a9596a5d0" />

<img width="1240" height="924" alt="image" src="https://github.com/user-attachments/assets/8a672fd1-7062-4622-82bb-f0331bf0a5e6" />

<img width="846" height="543" alt="image" src="https://github.com/user-attachments/assets/789600e7-c224-4b98-a874-461b028d8f80" />

<img width="656" height="439" alt="image" src="https://github.com/user-attachments/assets/f85379ef-12e4-4247-97fe-8f73985be1ae" />

<img width="418" height="278" alt="image" src="https://github.com/user-attachments/assets/c6087260-2c09-4469-844a-a111728c3246" />


### Steps

1. Give labeled data to model
2. Model learns patterns
3. New data is classified
4. Output label is predicted


## 3️⃣ Applications of Classification

Classification is used in many real-life problems.

### 📈 Common Uses

| Area       | Example           |
| ---------- | ----------------- |
| Email      | Spam filtering    |
| Banking    | Loan default      |
| Business   | Churn prediction  |
| Healthcare | Disease detection |
| Marketing  | Ad response       |
| Security   | Biometric ID      |

### 📌 Examples from Lecture

* Customer churn
* Customer segmentation
* Loan default prediction
* Drug recommendation


<img width="1019" height="493" alt="image" src="https://github.com/user-attachments/assets/0db170ce-8d51-43c4-a25a-70e0e2c75107" />


## 4️⃣ Types of Classification Problems

### (A) Binary Classification

Has **two classes** only.

Example:

* Yes / No
* Pass / Fail
* Default / Not Default

### 📍 Example: Bank Loan

<img width="1023" height="573" alt="image" src="https://github.com/user-attachments/assets/5fc857c3-3b6e-4ff8-ab81-c5f2cfd44baa" />

Output:

* Will Default
* Will Not Default


### (B) Multi-Class Classification

Has **more than two classes**.

Example:

* Drug A / B / C
* Grade A / B / C / D
* Animal: Cat / Dog / Bird

### 📍 Example: Drug Prediction

<img width="1918" height="1061" alt="image" src="https://github.com/user-attachments/assets/2c23ba03-67f1-4e5e-acd1-a1d5b2758fe0" />

Output:

* Drug X
* Drug Y
* Drug Z


## 5️⃣ Common Classification Algorithms

Many algorithms can perform classification.

### 📌 Popular Algorithms

| Algorithm           | Use             |
| ------------------- | --------------- |
| Naive Bayes         | Text, spam      |
| Logistic Regression | Binary problems |
| Decision Tree       | Rule-based      |
| KNN                 | Distance-based  |
| SVM                 | High accuracy   |
| Neural Network      | Deep learning   |

> ✅ Some work naturally for multi-class, some need special methods.

<img width="1918" height="1057" alt="image" src="https://github.com/user-attachments/assets/c8aadcd0-871e-4431-823e-e934c69d8b92" />


## 6️⃣ Multi-Class Classification Strategies

Many algorithms are **binary by nature**.
So, special techniques are used for multi-class problems.


## 7️⃣ One-Versus-All (OVA) Strategy

### 📌 Idea

If there are **k classes**, create **k binary classifiers**.

Each classifier checks:

> “Is this class or not?”

### Example: 3 Classes (A, B, C)

| Classifier | Task      |
| ---------- | --------- |
| C1         | A vs Rest |
| C2         | B vs Rest |
| C3         | C vs Rest |

### Working Diagram

<img width="700" height="438" alt="image" src="https://github.com/user-attachments/assets/01ec7025-de92-470a-895d-6ffc563032d3" />

<img width="2849" height="3869" alt="image" src="https://github.com/user-attachments/assets/c8ea3273-dcb1-486e-97ef-c8c9982f50ea" />

<img width="630" height="338" alt="image" src="https://github.com/user-attachments/assets/66b52854-f40b-4502-82ec-87b83fdb3925" />


### Prediction

* Run all classifiers
* Choose class with highest score

### ⚠ Limitation

Some points may not match any class → Outliers


## 8️⃣ One-Versus-One (OVO) Strategy

### 📌 Idea

Train classifiers for **every pair of classes**.

For k classes:

$$
\frac{k(k-1)}{2} \text{ classifiers}
$$

### Example: A, B, C

| Classifier |
| ---------- |
| A vs B     |
| A vs C     |
| B vs C     |

### Working Diagram

<img width="566" height="226" alt="image" src="https://github.com/user-attachments/assets/f082710e-3038-4975-9e29-813340e8be8c" />

<img width="705" height="296" alt="image" src="https://github.com/user-attachments/assets/c8f4a072-9995-4b93-9cd9-fb6d2a143c2f" />

### Prediction Method

* Each classifier votes
* Most votes = final class

### ⚠ Tie Case

If votes are equal:

* Use confidence scores
* Or switch to OVA


## 9️⃣ OVA vs OVO Comparison

| Feature     | One-Versus-All | One-Versus-One |
| ----------- | -------------- | -------------- |
| Classifiers | k              | k(k−1)/2       |
| Speed       | Faster         | Slower         |
| Accuracy    | Medium         | Higher         |
| Complexity  | Low            | High           |


## 🔟 Summary of Classification Process

### Overall Flow

<img width="900" height="500" alt="image" src="https://github.com/user-attachments/assets/1616a0b4-1e9e-45e1-8406-32776375aec5" />

### Steps

1. Collect labeled data
2. Choose algorithm
3. Train model
4. Test model
5. Predict new data


## 📌 Final Key Points (Exam-Oriented)

### ✔ Important Facts

* Classification = Supervised learning
* Output = Categorical label
* Uses labeled data
* Two types: Binary & Multi-class
* Popular algorithms: KNN, SVM, DT, NN
* Multi-class methods: OVA, OVO

### ✔ One-Line Definition

> Classification is a supervised learning method that predicts categorical labels using trained models.


## 📝 Quick Revision Table

| Topic          | Key Idea        |
| -------------- | --------------- |
| Classification | Predicts labels |
| Binary         | Two classes     |
| Multi-class    | More than two   |
| OVA            | One vs Rest     |
| OVO            | Pairwise voting |
| Output         | Category        |


