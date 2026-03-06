# Practice Questions for Machine Learning Models

## Instructions

These practice questions are designed to test your understanding of the material covered in the Machine Learning Models lecture. Work through each question carefully and show your reasoning.

---

## Part 1: True/False Questions

**Question 1:** In a machine learning model, independent variables are the features used to predict the dependent variable (label).

**Question 2:** Non-parametric models have no parameters at all.

**Question 3:** In a linear regression model with two features, the equation $y = w_1x_1 + w_2x_2 + w_0$ geometrically represents a plane in three-dimensional space (where the dimensions are the two features and the response).

**Question 4:** For linear classification models, the equation $\textbf{x}^T\textbf{w} + w_0 = 0$ represents the separating hyperplane that divides the feature space into regions for different classes.

**Question 5:** A parametric model's number of parameters increases with the size of the training dataset.

---

## Part 2: Explanatory Questions

**Question 6:** Explain the relationship between model input, model parameters, and model output in the context of machine learning models. How do these three components differ from each other?

**Question 7:** Compare and contrast parametric and non-parametric machine learning models. What are the main differences in their assumptions and how they use training data?

**Question 8:** Describe the geometric interpretation of linear classification models in a two-dimensional feature space. What does the weight vector represent, and how does it relate to the decision boundary?

**Question 9:** Explain what happens during the training phase of a linear model. What is being optimized, and what are the criteria used to determine the best parameters?

**Question 10:** What are the main advantages and disadvantages of linear models? In what situations would linear models be particularly useful or problematic?

---

## Part 3: Coding Question

**Question 11: Implement Simple Linear Regression**

Implement a simple linear regression model from scratch that fits a line to data using the least squares method. Your implementation should find the optimal weights $w_1$ (slope) and $w_0$ (intercept) that minimize the sum of squared errors.

**Steps:**
1. Calculate the mean of the input features (x) and labels (y)
2. Compute the slope $w_1$ using the formula: $w_1 = \frac{\sum_{i=1}^{n}(x_i - \bar{x})(y_i - \bar{y})}{\sum_{i=1}^{n}(x_i - \bar{x})^2}$
3. Compute the intercept $w_0$ using the formula: $w_0 = \bar{y} - w_1\bar{x}$
4. Create a predict function that uses these parameters to make predictions
5. Test your implementation on sample data

**Function Signature:**
```python
def simple_linear_regression(x_train, y_train):
    """
    Train a simple linear regression model using the least squares method.
    
    Args:
        x_train: numpy array of shape (n,) containing training features
        y_train: numpy array of shape (n,) containing training labels
    
    Returns:
        w1: float, the slope parameter
        w0: float, the intercept parameter
    """
    pass

def predict(x, w1, w0):
    """
    Make predictions using the linear regression model.
    
    Args:
        x: numpy array of input features
        w1: float, slope parameter
        w0: float, intercept parameter
    
    Returns:
        numpy array of predicted values
    """
    pass
```

**Example:**
```python
import numpy as np

# Input
x_train = np.array([1, 2, 3, 4, 5])
y_train = np.array([2, 4, 5, 4, 5])

w1, w0 = simple_linear_regression(x_train, y_train)
x_test = np.array([6, 7])
predictions = predict(x_test, w1, w0)

# Output
# w1 ≈ 0.6, w0 ≈ 2.2
# predictions ≈ [5.8, 6.4]
```

**Hints:**
- Use numpy's `np.mean()` function to calculate means
- The numerator in the slope formula represents the covariance between x and y
- The denominator represents the variance of x
- Remember that in Python, you can perform element-wise operations on numpy arrays

---

## Part 4: Use Case Application

**Question 12: House Price Prediction Using Multiple Linear Regression**

**Scenario:**

You are working for a real estate company that wants to predict house prices based on various features. The company has collected data on house size (in square feet), number of bedrooms, and age of the house (in years). Your task is to build a multiple linear regression model to predict house prices and use it to help the company price new listings.

**Data:**

The dataset contains information about houses with three features and their corresponding prices.

```python
import numpy as np
import pandas as pd

# Generate sample house data
np.random.seed(42)
n_samples = 100

# Features: size (sqft), bedrooms, age (years)
size = np.random.uniform(800, 3000, n_samples)
bedrooms = np.random.randint(1, 6, n_samples)
age = np.random.uniform(0, 50, n_samples)

# Generate prices with some relationship to features (with noise)
# Price formula: base + size_effect - age_penalty + bedroom_bonus + noise
prices = (50000 + 
          150 * size + 
          20000 * bedrooms - 
          1000 * age + 
          np.random.normal(0, 30000, n_samples))

# Create DataFrame
df = pd.DataFrame({
    'size_sqft': size,
    'bedrooms': bedrooms,
    'age_years': age,
    'price': prices
})

print(df.head())
```

**Task:**

Build a multiple linear regression model to predict house prices and analyze the results.

**Requirements:**
- Split the data into training (80%) and testing (20%) sets
- Train a linear regression model using scikit-learn
- Evaluate the model's performance on both training and testing sets using appropriate metrics
- Interpret the learned weights: which features have the most impact on house prices?
- Make predictions for the following new houses:
  - House 1: 1500 sqft, 3 bedrooms, 10 years old
  - House 2: 2500 sqft, 4 bedrooms, 5 years old

**Hints:**
- Use `sklearn.model_selection.train_test_split` for splitting the data
- Use `sklearn.linear_model.LinearRegression` for the model
- The `coef_` attribute of the trained model contains the weights for each feature
- Consider using Mean Squared Error (MSE) or R² score for evaluation
- Remember that the sign of the weight indicates whether the feature has a positive or negative effect on the price
- The magnitude of the weight indicates the strength of the feature's contribution
