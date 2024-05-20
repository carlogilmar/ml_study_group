# Linear Regression

One type of supervised learning is linear regression, **which involves processing features to predict \( Y \) targets using a training set.**

1. Line formula
2. Cost function
3. Gradient Descent

---

## 1. Straight Line Formula 

```math
f_{w,b}(x) = w \cdot x + b
```

where:
- $´ w ´$ is the weight (or slope) parameter,
- $´ b ´$ is the bias (or intercept) parameter,
- $´ x ´$ is the input feature.

> [!NOTE]
> This formula represents a `straight line`, making linear regression suitable for data that has a linear relationship between the input features and the target variable.
---

## 2. Cost Function in Linear Regression

```math
[ J(w, b) = \frac{1}{m} \sum_{i=1}^{m} (f_{w,b}(x^{(i)}) - y^{(i)})^2 ]
```

where:
- $´ m ´$ is the number of training examples,
- $`( f_{w,b}(x^{(i)}) )`$ is the predicted value for the $´ i ´$-th training example,
- $` y^{(i)} `$ is the actual value for the $´ i ´$-th training example.

> [!NOTE]
> The cost function provides a single value that summarizes the error of the model across all training examples. Lower values indicate a better fit.
---

## 3. Gradient Descent for Minimizing the Error

> [!NOTE]
> Gradient descent is an optimization algorithm used to minimize the cost function by iteratively adjusting the parameters $´ w ´$ and $´ b ´$. The goal is to find the values of $´ w ´$ and $´ b ´$ that result in the smallest possible cost function value.

The gradient descent algorithm updates the parameters using the following rules:

```math
w := w - \alpha \frac{\partial J(w, b)}{\partial w}
```

```math
b := b - \alpha \frac{\partial J(w, b)}{\partial b}
```

where:
- $´ \alpha ´$ is the learning rate, a small positive number that controls the step size,
- $´ \frac{\partial J(w, b)}{\partial w} ´$ and $´ \frac{\partial J(w, b)}{\partial b} ´$ are the partial derivatives of the cost function with respect to $´ w ´$ and $´ b ´$, respectively.

### Summary
- **Model Formula**: $´ f_{w,b}(x) = w \cdot x + b ´$
- **Cost Function**: Measures the error in predictions, commonly using Mean Squared Error (MSE).
- **Gradient Descent**: An optimization technique to find the best \( w \) and \( b \) by iteratively reducing the cost function.

## 4. Example

`Dataset`
|Sizes|Prices|
|---|---|
|500|150000|
|800|200000|
|1000|250000|
|1200|300000|
|1500|350000|

`Steps to calculate linear regression`
1. Feature scaling to normalize data (Subtracting the mean and dividing by the standard deviation).
2. Initialize parameters `w, b, learning rate and iterations`
3. Train the model iterating 1000 times (this means get the gradient descent)
4. With this you'll calculate the params `w` and `b` for your linear regression model to predict `Y` based on `X`: `Y = w * X + b`

 
```python
import numpy as np
import matplotlib.pyplot as plt

# Sample data: sizes (in square feet) and prices (in dollars)
sizes = np.array([500, 800, 1000, 1200, 1500])
prices = np.array([150000, 200000, 250000, 300000, 350000])

# Normalize the data (feature scaling)
sizes = (sizes - np.mean(sizes)) / np.std(sizes)
prices = (prices - np.mean(prices)) / np.std(prices)

# Initialize parameters
w = 0
b = 0
alpha = 0.01  # Learning rate
num_iterations = 1000

# Cost function
def compute_cost(sizes, prices, w, b):
    m = len(prices)
    cost = (1 / (2 * m)) * np.sum((w * sizes + b - prices) ** 2)
    return cost

# Gradient descent
cost_history = []  # To store the cost at each iteration
for i in range(num_iterations):
    w_gradient = (1 / len(prices)) * np.sum((w * sizes + b - prices) * sizes)
    b_gradient = (1 / len(prices)) * np.sum(w * sizes + b - prices)
    w -= alpha * w_gradient
    b -= alpha * b_gradient

    # Compute and store the cost
    cost = compute_cost(sizes, prices, w, b)
    cost_history.append(cost)

    # Print the cost every 100 iterations
    if i % 100 == 0:
        print(f"Iteration {i}: Cost {cost}")

# Plot the results
plt.scatter(sizes, prices, color='blue', label='Data points')
plt.plot(sizes, w * sizes + b, color='red', label='Linear regression')
plt.xlabel('Size (normalized)')
plt.ylabel('Price (normalized)')
plt.legend()
plt.show()

# Plot cost history
plt.plot(range(num_iterations), cost_history, color='green')
plt.xlabel('Iteration')
plt.ylabel('Cost')
plt.title('Cost Reduction Over Time')
plt.show()

# Print the final parameters
print(f"w: {w}, b: {b}")
```

<img width="748" alt="image" src="https://github.com/carlogilmar/ml_study_group/assets/17634377/76734bb9-6f7e-439d-b0f2-b85e43566f6c">

<img width="737" alt="image" src="https://github.com/carlogilmar/ml_study_group/assets/17634377/641a5272-b307-4583-ae09-881489a78952">


