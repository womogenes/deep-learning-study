# Chapter 2 notes

Supervised learning model is a function $y = f[x, \phi]$ relating inputs x to outputs y. We measure model performance using a loss function $L[\phi]$. $\{x_i , y_i\}$ is our training set and helps us select optimal $\phi$.

Preview of later chapters:

- Chapter 3: Shallow neural networks
- Chapter 4: Deep neural networks
- Chapter 5: Different kinds of loss functions, theoretical underpinnings of least-squares loss
- Chapters 6, 7: Training process
- Chapter 8: Measuring model performance
- Chapter 9: Regularization techniques

## Problems (p. 24)

**Problem 2.1** Calculate $\partial L/\partial \phi_0$ and $\partial L/\partial \phi_1$.

We know
$$L[\phi] = \sum_{i=1}^I (\phi_0 + \phi_1 x_i - y_i)^2.$$
Presumably this means
$$\partial L/\partial\phi_0 = \sum_{i=1}^I 2(\phi_0 + \phi_1 x_i - y_i)$$
because every term can be differentiated separately and added back, and then we just use chain rule.

Then also
$$\partial L/\partial\phi_1 = \sum_{i=1}^I x_i (\phi_0 + \phi_1 x_i - y_i).$$

**Problem 2.2** Find $\phi_0$ and $\phi_1$ such that both of the partials are zero.

$$
\begin{align*}
  \partial L/\partial\phi_0 &= 0 \\
  \sum_{i=1}^I (\phi_0 + \phi_1 x_i - y_i) &= 0 \\
  I\phi_0 + \phi_1 \sum x_i - \sum y_i &= 0 \\
  \phi_0 = \frac1I \left(\phi_1 \sum x_i - \sum y_i \right)
\end{align*}
$$

Maybe we should find $\phi_1$ too.
$$
\begin{align*}
  \partial L/\partial\phi_1 &= 0 \\
  \sum_{i=1}^I 2x_i(\phi_0 + \phi_1 x_i - y_i) &= 0 \\
  \phi_0 \sum x_i + \phi_1 \sum x_i^2 - \sum x_i y_i &= 0
\end{align*}
$$
At this point it's probably helpful to define ${S_x = \sum x_i}$, ${S_{x^2} = \sum x_i^2}$, ${S_y = \sum y_i}$, and ${S_{xy} = \sum x_i y_i}$. These are all known, computable quantities. So we have
$$
\begin{align*}
    \phi_0 &= \frac1I (S_x \phi_1 - S_y) \\
    \phi_1 &= \frac1{S_{x^2}} (S_x \phi_0 - S_{xy}).
\end{align*}
$$
I'm going to stop here, because now it's a simple linear system that we know how to solve.

**Problem 2.3** Consider reformulating linear regression as a generative model, so we have x = g[y, ϕ] = ϕ0 + ϕ1y. What is the new loss function? Find an expression for the inverse function y = g
−1 [x, ϕ] that we would use to perform inference. Will this model make the same predictions as the discriminative version for a given training dataset {xi, yi}? One way to establish this is to write code that fits a line to three data points using both methods and see if the result is the same.

We might want to switch up the loss function. Cause now we have
$$x = g[y, \phi] = \phi_0 + \phi_1 y.$$

I mean it depends what we want to name the loss function as.
