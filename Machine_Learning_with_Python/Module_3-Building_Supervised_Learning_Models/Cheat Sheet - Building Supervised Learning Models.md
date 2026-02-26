# Cheat Sheet: Building Supervised Learning Models

## Common Supervised Learning Models

---

## One vs One Classifier (Using Logistic Regression)

**Process:**
This method trains one classifier for each pair of classes.

**Key Hyperparameters:**

* `estimator`: Base classifier (e.g., Logistic Regression)

**Pros:**

* Works well for small datasets.

**Cons:**

* Computationally expensive for large datasets.

**Common Applications:**

* Multiclass classification problems with relatively small number of classes.

```python
from sklearn.multiclass import OneVsOneClassifier
from sklearn.linear_model import LogisticRegression

model = OneVsOneClassifier(LogisticRegression())
```

---

## One vs All (One vs Rest) Classifier (Using Logistic Regression)

**Process:**
Trains one classifier per class, where each classifier distinguishes between one class and the rest.

**Key Hyperparameters:**

* `estimator`: Base classifier (e.g., Logistic Regression)
* `multi_class`: Strategy to handle multiclass classification (`ovr`)

**Pros:**

* Simpler and more scalable than One vs One.

**Cons:**

* Less accurate for highly imbalanced classes.

**Common Applications:**

* Multiclass classification problems such as image classification.

```python
from sklearn.multiclass import OneVsRestClassifier
from sklearn.linear_model import LogisticRegression

model = OneVsRestClassifier(LogisticRegression())
```

**Alternative:**

```python
from sklearn.linear_model import LogisticRegression

model_ova = LogisticRegression(multi_class='ovr')
```

---

## Decision Tree Classifier

**Process:**
A tree-based classifier that splits data into smaller subsets based on feature values.

**Key Hyperparameters:**

* `max_depth`: Maximum depth of the tree

**Pros:**

* Easy to interpret and visualize.

**Cons:**

* Prone to overfitting if not pruned properly.

**Common Applications:**

* Classification tasks such as credit risk assessment.

```python
from sklearn.tree import DecisionTreeClassifier

model = DecisionTreeClassifier(max_depth=5)
```

---

## Decision Tree Regressor

**Process:**
Similar to the decision tree classifier, but used for regression tasks to predict continuous values.

**Key Hyperparameters:**

* `max_depth`: Maximum depth of the tree

**Pros:**

* Easy to interpret.
* Handles nonlinear data.

**Cons:**

* Can overfit and perform poorly on noisy data.

**Common Applications:**

* Regression tasks such as predicting housing prices.

```python
from sklearn.tree import DecisionTreeRegressor

model = DecisionTreeRegressor(max_depth=5)
```

---

## Linear SVM Classifier

**Process:**
A linear classifier that finds the optimal hyperplane separating classes with maximum margin.

**Key Hyperparameters:**

* `C`: Regularization parameter
* `kernel`: Type of kernel function (`linear`, `poly`, `rbf`, etc.)
* `gamma`: Kernel coefficient (only for `rbf`, `poly`, etc.)

**Pros:**

* Effective for high-dimensional spaces.

**Cons:**

* Not ideal for nonlinear problems without kernel tricks.

**Common Applications:**

* Text classification
* Image recognition

```python
from sklearn.svm import SVC

model = SVC(kernel='linear', C=1.0)
```

---

## K-Nearest Neighbors (KNN) Classifier

**Process:**
Classifies data based on the majority class of its nearest neighbors.

**Key Hyperparameters:**

* `n_neighbors`: Number of neighbors to use
* `weights`: Weight function used in prediction (`uniform` or `distance`)
* `algorithm`: Algorithm used to compute nearest neighbors (`auto`, `ball_tree`, `kd_tree`, `brute`)

**Pros:**

* Simple and effective for small datasets.

**Cons:**

* Computationally expensive as dataset grows.

**Common Applications:**

* Recommendation systems
* Image recognition

```python
from sklearn.neighbors import KNeighborsClassifier

model = KNeighborsClassifier(n_neighbors=5, weights='uniform')
```

---

## Random Forest Regressor

**Process:**
An ensemble method using multiple decision trees to improve accuracy and reduce overfitting.

**Key Hyperparameters:**

* `n_estimators`: Number of trees in the forest
* `max_depth`: Maximum depth of each tree

**Pros:**

* Less prone to overfitting than individual decision trees.

**Cons:**

* Model complexity increases with the number of trees.

**Common Applications:**

* Regression tasks such as predicting sales or stock prices.

```python
from sklearn.ensemble import RandomForestRegressor

model = RandomForestRegressor(n_estimators=100, max_depth=5)
```

---

## XGBoost Regressor

**Process:**
A gradient boosting method that builds trees sequentially to correct errors from previous trees.

**Key Hyperparameters:**

* `n_estimators`: Number of boosting rounds
* `learning_rate`: Step size to improve accuracy
* `max_depth`: Maximum depth of each tree

**Pros:**

* High accuracy
* Works well with large datasets

**Cons:**

* Computationally intensive
* Complex to tune

**Common Applications:**

* Predictive modeling
* Kaggle competitions

```python
import xgboost as xgb

model = xgb.XGBRegressor(
    n_estimators=100,
    learning_rate=0.1,
    max_depth=5
)
```

---

# Associated Functions Used

---

## OneHotEncoder

**Description:**
Transforms categorical features into a one-hot encoded matrix.

```python
from sklearn.preprocessing import OneHotEncoder

encoder = OneHotEncoder(sparse=False)
encoded_data = encoder.fit_transform(categorical_data)
```

---

## accuracy_score

**Description:**
Computes the accuracy of a classifier by comparing predicted and true labels.

```python
from sklearn.metrics import accuracy_score

accuracy = accuracy_score(y_true, y_pred)
```

---

## LabelEncoder

**Description:**
Encodes labels (target variable) into numeric format.

```python
from sklearn.preprocessing import LabelEncoder

encoder = LabelEncoder()
encoded_labels = encoder.fit_transform(labels)
```

---

## plot_tree

**Description:**
Plots a decision tree model for visualization.

```python
from sklearn.tree import plot_tree

plot_tree(model, max_depth=3, filled=True)
```

---

## normalize

**Description:**
Scales each feature to have zero mean and unit variance (standardization).

```python
from sklearn.preprocessing import normalize

normalized_data = normalize(data, norm='l2')
```

---

## compute_sample_weight

**Description:**
Computes sample weights for imbalanced datasets.

```python
from sklearn.utils.class_weight import compute_sample_weight

weights = compute_sample_weight(class_weight='balanced', y=y)
```

---

## roc_auc_score

**Description:**
Computes the Area Under the Receiver Operating Characteristic Curve (AUC-ROC) for binary classification models.

```python
from sklearn.metrics import roc_auc_score

auc = roc_auc_score(y_true, y_score)
```

---

## Author

* Jeff Grossman
* Abhishek Gagneja
