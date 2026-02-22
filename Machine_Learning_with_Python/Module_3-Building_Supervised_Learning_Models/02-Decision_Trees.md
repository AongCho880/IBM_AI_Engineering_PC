# 📘 Decision Trees in Machine Learning — Complete Notes

## 1. What is a Decision Tree?

<img width="1914" height="1053" alt="image" src="https://github.com/user-attachments/assets/8db4fced-3fe4-4e41-ae58-9b97e95f0fec" />


A **Decision Tree** is a supervised machine learning algorithm used for **classification and prediction**.

It looks like a **flowchart**:

* **Root Node** → Starting point
* **Internal Nodes** → Decision based on a feature
* **Branches** → Result of a decision
* **Leaf Nodes** → Final prediction (class)

### Structure

| Part          | Meaning            |
| ------------- | ------------------ |
| Root Node     | First feature used |
| Internal Node | Decision rule      |
| Branch        | Outcome of rule    |
| Leaf Node     | Final class        |

👉 Each path from root to leaf represents a **decision rule**.


## 2. Example: Medical Drug Prediction

<img width="1917" height="1058" alt="image" src="https://github.com/user-attachments/assets/6f64919d-8f02-4c05-94c6-186fbb5df87a" />

<img width="1909" height="1055" alt="image" src="https://github.com/user-attachments/assets/7f4fe313-79fb-4a91-8cdf-6637c9a66830" />



### Problem

We want to predict whether a patient should receive:

* **Drug A** or
* **Drug B**

### Features (Input Data)

* Age (Young / Middle / Senior)
* Gender (Male / Female)
* Blood Pressure
* Cholesterol

### Target (Output)

* Drug A or Drug B

### Example Rules

The tree may learn rules like:

* If **Middle-aged** → Drug B
* If **Young + Male** → Drug B
* If **Senior + High Cholesterol** → Drug A
* If **Young + Female** → Drug A

👉 The model learns these rules from past patient data.


## 3. How is a Decision Tree Trained?

<img width="1907" height="1056" alt="image" src="https://github.com/user-attachments/assets/8fed836d-d465-49ae-8ded-ab50dbb5a808" />

<img width="499" height="338" alt="image" src="https://github.com/user-attachments/assets/02ffd0dd-1a1a-422d-af1a-c55e0e0dfbd1" />

Decision Trees are built using **recursive partitioning**.

### Training Steps

1. Start with all data at the root.
2. Select the **best feature** to split.
3. Divide data into groups.
4. Create child nodes.
5. Repeat for each node.
6. Stop when a condition is met.

### Stopping Conditions

The tree stops growing when:

* Maximum depth reached
* Too few samples remain
* Node is already pure
* Maximum leaves reached

This process is called **Pre-pruning (Pre-emptive pruning).**

👉 Goal: Make each leaf as **pure** as possible (only one class).


## 4. Tree Pruning (Avoiding Overfitting)

<img width="1910" height="1049" alt="image" src="https://github.com/user-attachments/assets/52f6cf86-3d4e-4133-91c4-00dcfb0e10b7" />

<img width="2308" height="1023" alt="image" src="https://github.com/user-attachments/assets/1059af66-40fd-4e7c-b64e-2a6f6de9f8d3" />

### What is Pruning?

Pruning means **cutting unnecessary branches** from a tree.

It prevents the tree from becoming too complex.


### Why Pruning is Needed

Without pruning:

❌ Tree becomes very deep
❌ Learns noise
❌ Overfits training data
❌ Poor performance on new data

With pruning:

✅ Simpler model
✅ Better generalization
✅ Easier to understand
✅ Higher accuracy

<img width="1906" height="1056" alt="image" src="https://github.com/user-attachments/assets/296085bc-06ad-4d11-9d47-7ae0f5b41c35" />

### Types of Pruning

#### 1. Pre-pruning

Stop early using limits:

* Max depth
* Min samples
* Max leaves

#### 2. Post-pruning

* Grow full tree
* Remove weak branches later


## 5. Feature Selection and Split Criteria

<img width="1200" height="747" alt="image" src="https://github.com/user-attachments/assets/e87ce64a-93e9-4e4d-9333-35ec830ec521" />
<img width="1127" height="567" alt="image" src="https://github.com/user-attachments/assets/61b31b54-8b8c-4b1a-85ca-9b997e44d714" />
<img width="800" height="482" alt="image" src="https://github.com/user-attachments/assets/d2d73a64-aa90-45b6-b888-e8933603f508" />


At every node, the algorithm must choose:

👉 **Which feature gives the best split?**

This is done using **split criteria**.


## 6. Entropy (Measure of Disorder)

<img width="1915" height="1056" alt="image" src="https://github.com/user-attachments/assets/42b35ac4-2729-4ac0-b3b5-f8f1e53dcbed" />

### What is Entropy?

Entropy measures **uncertainty or randomness** in data.

* High entropy → Mixed classes
* Low entropy → Pure classes

### Range

```
0 ≤ Entropy ≤ 1
```

| Situation      | Entropy |
| -------------- | ------- |
| All same class | 0       |
| 50%–50% mix    | 1       |

### Formula

$$
Entropy = - (p_A \log_2 p_A + p_B \log_2 p_B)
$$

Where:

* $p_A$ = proportion of Drug A
* $p_B$ = proportion of Drug B

👉 Libraries calculate this automatically.


## 7. Information Gain

<img width="1911" height="1050" alt="image" src="https://github.com/user-attachments/assets/07f5c2cc-ed56-45ce-8380-7dc73e9a38b0" />

### What is Information Gain?

Information Gain tells:

> How much uncertainty is reduced after splitting.

### Formula

$$
Information\ Gain = Entropy(before) - Entropy(after)
$$

### Interpretation

* High IG → Good split
* Low IG → Bad split

👉 The algorithm always chooses the feature with **maximum information gain**.


### Relationship

| Entropy | Information Gain |
| ------- | ---------------- |
| High    | Low              |
| Low     | High             |

They are opposites.


## 8. Gini Impurity (Alternative Measure)

Besides entropy, another common metric is **Gini Impurity**.

### Formula

$$
Gini = 1 - \sum p_i^2
$$

### Meaning

* 0 → Perfectly pure
* Higher → More mixed

### Comparison

| Metric  | Used In   |
| ------- | --------- |
| Entropy | ID3, C4.5 |
| Gini    | CART      |

👉 Both work well in practice.


## 9. Example: Choosing the Best Split

### Step 1: Try Cholesterol

* High / Normal
* Still mixed
* Low confidence

❌ Not best

### Step 2: Try Gender

* Male / Female
* Females mostly Drug B
* Males still mixed

Better

### Step 3: Split Male by Cholesterol

* Creates pure leaves

✅ Best

👉 Algorithm continues until stopping condition.


## 10. Advantages of Decision Trees

### 1. Easy to Understand

* Works like human logic
* Visual structure

### 2. Interpretable

* You can trace decisions
* No black box

### 3. Feature Importance

* Shows which features matter most

### 4. Works with Mixed Data

* Categorical + Numerical

### 5. Little Preprocessing

* No normalization needed


## 11. Limitations

| Problem     | Description                        |
| ----------- | ---------------------------------- |
| Overfitting | Learns noise                       |
| Unstable    | Small data change → big tree       |
| Bias        | Biased toward multi-level features |

👉 Often solved using **Random Forests** and **Boosting**.


## 12. Summary (Key Points)

### ✔ Definition

* Decision Tree = Flowchart-like classifier

### ✔ Training

* Recursive splitting
* Best feature at each node

### ✔ Stopping

* Depth, samples, leaves

### ✔ Pruning

* Removes overfitting
* Improves generalization

### ✔ Split Measures

* Entropy
* Information Gain
* Gini Impurity

### ✔ Benefits

* Interpretable
* Visual
* Simple


## 📌 Final Takeaway

> A Decision Tree learns **if–then rules** from data to make predictions.
> It selects features that best reduce uncertainty, grows recursively, and is pruned to avoid overfitting.
