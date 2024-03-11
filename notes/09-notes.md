# Chapter 9: Regularization

## Questions

What's a prior?

## 9.1.2 L2 regularization

Penalize sum of squares of weights. **Do not** include biases in this.

"Weight decay" is a term for this.

## 9.2 Implicit regularization

(Stochastic) gradient descent *inherently* favors regularization??

Discrete gradient descent trajectory is repelled from places where gradient norm is large (surface is steep).

Discrete stochastic gradient descent favors places where gradients all agree.

**Observation:** full batch gradient descent generalizes better with larger step sizes.

## 9.3 Heuristics to improve performance

1. Early stopping
2. Ensembling (there are many ways to do this, for regularization vs. classification tasks)
   1. "Bootstrap aggregating" or "bagging" &mdash; training on different subsets of the dataset.
3. Dropout
   1. If we kill nodes in the network randomly (usually 50%) during every training step, random kinks will be sorted out.
   
   **"weight scaling inference rule"** &mdash; if we use dropout, weights must later be multiplied by 1 - dropout probability for interence.

### 9.3.4 Adding noise

1. Add noise to training data (reduce variance)
2. Add noise to weights. Encourages model to settle in "flat" local minima
3. Add noise to labels. Two ways to do this: randomly change labels during training, or optimize for not-overly-confident probability vectors (i.e. $(0.8, 0.1, 0.1)$ instead of $(1, 0, 0)$).

### 9.3.6 Transfer learning!

Transfer part of a model for one task to another, related one.

There are a bunch of other techniques.
