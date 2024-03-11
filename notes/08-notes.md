# Chapter 8: Measuring performance

## 8.4 Double descent

As model capacity increases, bias decreases and variance increases. But only up to a certain point! After the number of parameters equals the number of training examples, variance goes back down.

Also, **note:** the curse of dimensionality means the number of training examples is almost always inadequate to fill in the total number of dimensions. With 40 dimensions and 40,000 examples, this is $x^{40}$ regions if $x$ is the number of quantizations of each dimension.
