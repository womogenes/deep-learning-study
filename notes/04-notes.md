# Chapter 4 notes

> A different way to think about composing networks is that the first network “folds” the input space x back onto itself so that multiple inputs generate the same output. Then the second network applies a function, which is replicated at all points that were folded on top of one another (figure 4.3).

![Figure 4.3](./images/fig-4.3.png)

> It’s important not to lose sight of the fact that this is still merely an equation relating input $x$ to output $y'$.
> (p. 46)

### 4.3.1 Hyperparameters

Vocabulary

- **Width:** number of hidden units at each layer
- **Depth:** number of hidden layers
- **Capacity:** total number of hidden units

### 4.4.1 General formulation

- Number of hidden units at layer $k$: $D_k$
- Vector of hidden units at layer $k$: $\textbf{h}_k$
- Vector of biases that contribute to hidden layer $k+1$: $\mathbf{\beta}_k$
- Weights from $k$th layer to $(k+1)$th layer: $\mathbf{\Omega}_k$

### 4.5.2 Number of linear regions per parameter

> Deep neural networks create much more complex functions for a fixed parameter budget. (p. 50)
