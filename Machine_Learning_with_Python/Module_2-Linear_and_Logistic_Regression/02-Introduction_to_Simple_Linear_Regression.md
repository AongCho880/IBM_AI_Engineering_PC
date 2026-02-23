# Introduction to Simple Linear Regression

These notes are prepared based on the attached lecture script on *Introduction to Simple Linear Regression* . The content follows the same topic sequence and explains concepts in clear and simple language.

## 1. What is Simple Linear Regression?

Simple Linear Regression is a statistical method used to model the relationship between:

* **One independent variable (X)**
* **One dependent (target) variable (Y)**

It is mainly used to **predict continuous values**, such as:

* House prices
* Temperature
* Sales
* CO₂ emissions (in this lecture)

### Example Dataset (From Lecture)

The dataset contains information about cars, including:

| Feature          | Description                    |
| ---------------- | ------------------------------ |
| Engine Size      | Size of the car engine         |
| Cylinders        | Number of cylinders            |
| Fuel Consumption | Fuel usage                     |
| CO₂ Emission     | Carbon dioxide output (Target) |

In **simple linear regression**, only **one feature** is used.

> Here, **Engine Size (X)** → predicts → **CO₂ Emission (Y)**


## 2. Visualizing the Relationship: Scatter Plot

Before building a model, we visualize the data.

A **scatter plot** shows how two variables are related.

### Purpose of Scatter Plot

* Each point = one data sample
* Shows trends and patterns
* Helps detect correlation

If points roughly follow a straight line → Linear relationship exists.

### Example: Engine Size vs CO₂ Emission

<img width="1904" height="1048" alt="image" src="https://github.com/user-attachments/assets/e5d36ca1-e3e7-444a-a08f-ff1141b20e14" />
<img width="1907" height="1053" alt="image" src="https://github.com/user-attachments/assets/3bb3bec1-847b-4688-b6c9-9b892ed401f5" />

### Observation

* As engine size increases → CO₂ emission increases
* Relationship is approximately **linear**

So, linear regression is suitable.


## 3. The Simple Linear Regression Model

Simple linear regression fits a **straight line** through the data.

<img width="1912" height="1056" alt="image" src="https://github.com/user-attachments/assets/205edc58-fff8-4075-b923-fe78a6e87bf0" />


### Mathematical Model

$$
\hat{y} = \theta_0 + \theta_1 x
$$

Where:

| Symbol | Meaning                     |
| ------ | --------------------------- |
| ŷ      | Predicted value             |
| x      | Input feature (Engine Size) |
| θ₀     | Intercept (Bias)            |
| θ₁     | Slope (Coefficient)         |

### Meaning of Parameters

#### 1. Intercept (θ₀)

* Value of Y when X = 0
* Where the line crosses Y-axis

#### 2. Slope (θ₁)

* Change in Y for 1 unit change in X
* Controls steepness of line

### Example From Lecture

Given:

* θ₀ = 108.05
* θ₁ = 39
* x = 2.4

$$
\hat{y} = 108.05 + 39 \times 2.4
$$

$$
\hat{y} = 201.65
$$

👉 Predicted CO₂ emission = **201.65**


## 4. Prediction Using Regression Line

Once the model is trained, prediction is easy.

### Steps

1. Take input value (x)
2. Substitute in equation
3. Compute ŷ

### Graphical Interpretation

<img width="1909" height="1052" alt="image" src="https://github.com/user-attachments/assets/ee3416b5-f4a0-4fe2-8329-a31117701fb8" />
<img width="760" height="491" alt="image" src="https://github.com/user-attachments/assets/e41a0cdc-f928-4999-ad3c-6fe6c91c7317" />


### Key Idea

* Every input maps to one point on the line
* That point gives predicted value


## 5. Residual Error and Model Performance

Not all points lie exactly on the line.

The **difference** between actual and predicted value is called **Residual Error**.

### Residual

$$
\text{Residual} = y - \hat{y}
$$

Where:

* y = Actual value
* ŷ = Predicted value

### Example From Lecture

* Actual CO₂ = 250
* Predicted CO₂ = 340

$$
\text{Error} = 250 - 340 = -90
$$

Magnitude = **90 units**

---

## 6. Mean Squared Error (MSE)

To evaluate the model, we calculate the **average error**.

This is done using **Mean Squared Error**.

### Formula

$$
MSE = \frac{1}{n} \sum (y_i - \hat{y}_i)^2
$$

### Why Squared?

* Makes all errors positive
* Penalizes large errors more
* Helps optimization

### Visual Explanation

<img width="727" height="418" alt="image" src="https://github.com/user-attachments/assets/1dc4ac16-36a6-4ed0-83f5-860a4bd9106e" />

<img width="380" height="202" alt="image" src="https://github.com/user-attachments/assets/d995d6e1-f260-4092-b6e9-fd4ff2f4903b" />

<img width="960" height="720" alt="image" src="https://github.com/user-attachments/assets/8be5b33f-6481-4f90-a510-3b878f624055" />

### Interpretation

* Small MSE → Good fit
* Large MSE → Poor fit


## 7. Ordinary Least Squares (OLS) Regression

<img width="1916" height="1050" alt="image" src="https://github.com/user-attachments/assets/0c4260d0-3c92-42a0-b937-098c0f6576eb" />

Linear regression uses **Ordinary Least Squares (OLS)** to find best parameters.

### Objective of OLS

> Minimize the Mean Squared Error

OLS chooses θ₀ and θ₁ such that:

$$
\sum (y - \hat{y})^2
$$

is minimum.


## 8. Calculating Coefficients (θ₀ and θ₁)

OLS provides closed-form formulas.

### Step 1: Compute Means

$$
\bar{x}, \bar{y}
$$

Example (Lecture):

* x̄ = 3.0
* ȳ = 226.2


### Step 2: Compute Slope (θ₁)

$$
\theta_1 = \frac{\sum (x_i-\bar{x})(y_i-\bar{y})}{\sum (x_i-\bar{x})^2}
$$

From lecture:

$$
\theta_1 = 39
$$


### Step 3: Compute Intercept (θ₀)

$$
\theta_0 = \bar{y} - \theta_1 \bar{x}
$$

From lecture:

$$
\theta_0 = 108.05
$$


### Final Model

$$
\hat{y} = 108.05 + 39x
$$


## 9. Advantages of Simple Linear Regression

### ✅ Easy to Understand

* Simple equation
* Clear interpretation

### ✅ Fast Computation

* No iterative training
* Direct calculation

### ✅ No Hyperparameters

* No tuning required

### ✅ Good for Small Datasets

* Works well with limited data


## 10. Limitations of Simple Linear Regression

### ❌ Assumes Linearity

* Cannot model curves
* Fails for nonlinear patterns

### ❌ Sensitive to Outliers

* Extreme values distort line
* Increase MSE

### ❌ Limited Expressiveness

* Only one feature
* Cannot handle complex data


## 11. Summary of Key Concepts

| Concept                  | Description                          |
| ------------------------ | ------------------------------------ |
| Simple Linear Regression | Uses one variable to predict another |
| Model                    | ŷ = θ₀ + θ₁x                         |
| θ₀                       | Intercept (Bias)                     |
| θ₁                       | Slope (Weight)                       |
| Residual                 | y − ŷ                                |
| MSE                      | Average squared error                |
| OLS                      | Method to minimize MSE               |


## 12. Final Takeaways

From this lecture, we learned:

✔ Simple linear regression predicts continuous values
✔ It models data using a straight line
✔ Parameters are found using OLS
✔ Performance is measured by MSE
✔ It is simple, fast, and interpretable
✔ But sensitive to outliers and limited in complexity
