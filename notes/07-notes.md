# Chapter 7: Backpropagation and weight initialization

This is the most important part:

![Section 7.4.1](images/sec-7.4.1.png)

## 7.5 Parameter initialization

Important problems: exploding and vanishing gradients. If we don't initialize weights properly, the forward and/or backword pass will have numbers way too big to work with.

_He initialization_ states that we should initialize weights in layer $h$ with variance
$$\sigma_\Omega^2 = \frac{2}{D_h},$$
where $D_h$ is the dimension of the original layer to which the weights are applied.
