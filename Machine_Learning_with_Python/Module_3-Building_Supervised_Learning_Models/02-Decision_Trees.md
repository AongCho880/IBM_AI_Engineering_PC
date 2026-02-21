# 📘 Decision Trees in Machine Learning — Short Notes with Figures

## 1. What is a Decision Tree?

A **Decision Tree** is a supervised machine learning algorithm used mainly for **classification**.

It works like a **flowchart** that makes decisions step by step.

### Main Parts:

* **Internal Node** → Tests a feature
* **Branch** → Result of the test
* **Leaf Node** → Final class/output

👉 It answers questions like:
“Is age > 40?” → “Is cholesterol high?” → “Which drug?”


## 📊 Structure of a Decision Tree

![Image](https://images.openai.com/static-rsc-3/4I3x11hOXIvss3gkDFVqChfolOGVph1-N96UfzBU0Oy0P_XVfQVSoex6TMmXGxZ_DZJALr3WFW26oTcqz8nIoOjQ1EquVAy1hGDlVt-AbAQ?purpose=fullsize\&v=1)

![Image](https://www.researchgate.net/publication/272666514/figure/fig1/AS%3A612917321953280%401523142285587/Flowchart-of-C45-decision-tree-algorithm.png)

![Image](https://www.researchgate.net/publication/303773171/figure/fig2/AS%3A391407152975874%401470330145270/a-describes-the-components-of-a-decision-tree-the-Nodes-represent-the-possible.png)

![Image](https://www.researchgate.net/publication/382914996/figure/fig2/AS%3A11431281270029901%401723000998849/Structure-of-Decision-Tree-Nodes-Root-Interior-and-Leaf.ppm)

![Image](https://wiki.pathmind.com/images/wiki/decision_tree_nodes.png)

### Example:

For medical data:

* Root: Age
* Next: Gender / Cholesterol
* Leaf: Drug A or Drug B

Each path from top to bottom is a **decision rule**.


## 2. Example: Drug Prediction

### Problem:

Predict whether a patient needs **Drug A or Drug B**.

### Input Features:

* Age
* Gender
* Blood Pressure
* Cholesterol

### Output:

* Drug A
* Drug B

### Working:

The tree checks patient information and follows branches until it reaches a decision.

👉 Decision is based on past patient data.


## 3. How is a Decision Tree Built?

Decision Trees are built using **recursive splitting**.

### Steps:

1. Start with all training data
2. Select the best feature
3. Split data into groups
4. Create new nodes
5. Repeat
6. Stop when conditions are met

This process is called **recursive partitioning**.


## 🌳 Building a Decision Tree (Training Process)

![Image](https://miro.medium.com/0%2Apb-1ufHK-OmR8k7r.png)

![Image](https://images.openai.com/static-rsc-3/1dkR9kvb99D09fHyKjL7H2YFbnX6gAHa1O_9e_52ynR4nHgns1FIDnHwiAkBycIOlaAOEEePpkUmhs18uyDUCZZ5uWcpS0faRuoVdtfQCc0?purpose=fullsize\&v=1)

![Image](https://www.researchgate.net/publication/339716153/figure/fig1/AS%3A865707545878528%401583412171698/Example-of-a-calculated-recursive-partition-decision-tree-Algorithm-Builder-v18.jpg)

![Image](https://www.researchgate.net/publication/51979650/figure/fig3/AS%3A195881040125952%401423713087012/Decision-tree-constructed-by-recursive-partitioning-analysis-test-sample-The-plots-of.png)

![Image](https://www.researchgate.net/publication/330227554/figure/fig5/AS%3A960339940229149%401605974292484/Example-of-decision-tree-recursively-partitioned-predictor-space-left-and-the.png)

### Key Idea:

At every step, the algorithm chooses the **best feature** to divide the data.

Goal: Make each group as **pure** as possible.


## 4. How Does the Tree Choose the Best Feature?

To split data, the algorithm uses **split measures**.

### Common Measures:

### ✅ Entropy

* Measures **randomness**
* High entropy → Mixed data
* Low entropy → Pure data

Range:

* 0 → Fully pure
* 1 → Fully mixed


### ✅ Information Gain

Shows how much **uncertainty is reduced** after splitting.

Formula (concept):

> Information Gain = Entropy (Before) − Entropy (After)

👉 Higher gain = Better feature


### ✅ Gini Impurity

* Measures wrong classification
* Lower value = Better split

(Libraries calculate this automatically)


## 📈 Entropy and Information Gain Visualization

![Image](https://miro.medium.com/1%2AKKICWqYsVwac-SnP1Mt4Gg.png)

![Image](https://ekamperi.github.io/images/decision_trees/gini_vs_entropy.png)

![Image](https://miro.medium.com/1%2AOctuEVmm38Xeo-jfCHPRdw.png)

![Image](https://miro.medium.com/0%2AavdB7itYtq-oKIU7.png)

### Goal of Splitting:

✔️ Reduce entropy
✔️ Increase information gain
✔️ Make leaves more pure


## 5. When Does the Tree Stop Growing?

A tree stops when:

* Maximum depth is reached
* Minimum samples in a node is reached
* Minimum samples in a leaf is reached
* Maximum number of leaves is reached

This is called:

> ✅ Pre-pruning (Early stopping)


## 6. Pruning in Decision Trees

Sometimes trees become too large and complex.

This leads to:

> ❌ Overfitting (memorizing training data)

### What is Pruning?

Removing unnecessary branches.

### Why Prune?

* Reduces overfitting
* Removes noise
* Improves accuracy
* Makes model simpler

### Types:

1. Pre-pruning → Stop early
2. Post-pruning → Cut after training


## 7. Advantages of Decision Trees

### ✅ Easy to Understand

* Looks like a flowchart

### ✅ Highly Interpretable

* You can see each decision

### ✅ Feature Importance

* Shows which features matter most

### ✅ No Data Scaling Needed

* Works with raw data


## 8. Limitations

### ❌ Overfitting

* Large trees memorize data

### ❌ Sensitive to Noise

* Small changes affect structure

### ❌ Less Stable

* Compared to Random Forests

## 9. Quick Summary (For Revision)

| Topic          | Key Point                    |
| -------------- | ---------------------------- |
| Definition     | Flowchart-based ML algorithm |
| Structure      | Nodes, branches, leaves      |
| Training       | Recursive splitting          |
| Split Measures | Entropy, Gain, Gini          |
| Stopping       | Depth, samples, leaves       |
| Pruning        | Controls overfitting         |
| Advantage      | Simple & visual              |


## 10. Final Conclusion

Decision Trees classify data by asking a sequence of logical questions based on features. They use entropy, information gain, or Gini impurity to choose the best splits. Pruning helps prevent overfitting. Because of their simple and visual nature, Decision Trees are widely used and easy to understand in machine learning.


If you’d like, I can now prepare:

✅ One-page exam cheat sheet
✅ Numerical example of entropy & gain
✅ Comparison with Random Forest
✅ Practice MCQs
