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

