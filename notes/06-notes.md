# Chapter 6: Fitting models

## My own takeaways

Notebook 6.3 suggests that larger batch sizes should be paired with larger learning rates. Is this true?
<https://stackoverflow.com/questions/53033556/how-should-the-learning-rate-change-as-the-batch-size-change>

### 6.1.2 Gabor model example

Fitting a model with a non-convex loss function can be tricky. Using gradient descent can lead to getting trapped in a local minimum (valley).

## 6.2 Stochastic gradient descent

1. Stochastic gradient descent (SGD) works by taking **batches** (or mini-batches), which are smaller subsets of the entire training data, and updating the parameters via derivative of loss with respect to that subset. The idea is that randomness helps make bad decisions locally that overall get us out of valleys.

### 6.2.2 Properties of SGD

1. Though it adds noise, still improves fit at every iteration
2. All training examples contribute equally
3. Less computationally expensive
4. Can (in theory) escape local minima
5. Reduces the chances of getting stuck near saddle points
6. In practice, finds parameters that generalze well to new data

## 6.3 Momentum

Momentum term (equation 6.11):

$$
\begin{align*}
  \bf{m}_{t+1} &\leftarrow \beta \cdot \bf{m}_t + (1-\beta) \sum_{i\in\mathcal{B}_t} \frac{\partial \ell_i[\bf{\phi}_t]}{\partial \bf{\phi}} \\
  \bf{\phi}_{t+1} &\leftarrow \bf{\phi}_t - \alpha \cdot \bf{m}_{t+1}
\end{align*}
$$

The momentum is an "exponentially weighted average" of the gradients. Smoother trajectory.

This helps increase speed of convergence.

## 6.4 Adam

Stands for "adaptive moment estimation."
How does this work?

1. At every step, we calculate the gradient vector (again, that's derivative of loss with respect to every parameter), as well as the element-wise square of that vector.
2. To update, we don't subtract the gradient directly but rather element-wise divide first by $\sqrt{v} + \varepsilon$, where $\varepsilon$ is some small amount to account for division by zero.
3. This means we move a fixed distance along each coordinate (parameter). That's really weird.

Adam takes this and adds momentum to both the gradient and the square of the gradient. That's cool.

![Figure 6.9](images/figure-6.9.png)

## 6.5 Training algorithm hyperparameters

**it's common to train many models with different hyperparameters and choose the best one.** This is known as _hyperparameter search._ (More in section 8)
