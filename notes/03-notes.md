# Chapter 3: Shallow neural networks

## 3.4 Shallow neural networks: general case

Basically, there's one hidden layer. Here's how it's defined:
$$
\begin{equation}
  h_d = a\left[\theta_{d0} + \sum_{i=1}^{D_i} \theta_{di} x_i \right] \tag{3.11}
\end{equation}
$$
There are $D_i$ inputs, the $i$th of which is $x_i$. There are $D$ hidden units, the $d$th of which is $h_d$.

![Figure 3.9](images/fig-3.9.png)

There are $D_o$ outputs, the $j$th of which is $y_j$. We have
$$
\begin{equation}
  y_j = \phi_{j0} + \sum_{d=1}^D \phi_{jd} h_d. \tag{3.12}
\end{equation}
$$

## 3.5 Terminology (p. 35)

- Input layer
- Hidden layer
- Ouput layer
- Neurons: hidden units
- Pre-activations: values of the inputs to the hidden layer (i.e. before ReLU is applied)
- Activations: values at the hidden layer after ReLU is applied
- Multi-layer perceptron: any neural network with &ge;1 hidden layer
- Deep neural network: networks with multiple hidden layers
- Feed-forward newtworks: networks with no loops
- Fully connected: if every element in one layer connects to every element in the next
- Weights: slope parameters in underlying equations
- Biases: offset parameters

## Problems (p. 39)

**Problem 3.1** What kind of mapping from input to output would be created if the activation function in equation 3.1 was linear so that a[z] = ψ0 + ψ1z? What kind of mapping would be created if the activation function was removed, so a[z] = z?

Utterly useless. Everything would be linear.

**Problem 3.2** For each of the four linear regions in figure 3.3j, indicate which hidden units are inactive and which are active (i.e., which do and do not clip their inputs).

From left to right:
- Region 1: $h_3$
- Region 2: $h_1$, $h_3$
- Region 3: all
- Region 4: $h_1$, $h_2$

**Problem 3.3*** Derive expressions for the positions of the “joints” in function in figure 3.3j in terms of the ten parameters ϕ and the input x. Derive expressions for the slopes of the four linear regions.

This doesn't seem terribly instructive.

**Problem 3.4** No

**Problem 3.5** Prove that ReLU(az) = a * ReLU(az) for a > 0. This is known as the *non-negative homogeneity* property of the ReLU function.

This is actually pretty cool. Very easy to prove; we're basically scaling up everything from the origin.

**Problem 3.6** Following on from problem 3.5, what happens to the shallow network defined in
equations 3.3 and 3.4 when we multiply the parameters θ10 and θ11 by a positive constant α
and divide the slope ϕ1 by the same parameter α? What happens if α is negative?

Nothing happens if $\alpha > 0$. If $\alpha$ is negative, we have
$$\mathrm{ReLU}[\alpha \cdot z] = 0$$
if $z > 0$ and
$$\mathrm{ReLU}[\alpha\cdot z] = \mathrm{ReLU}[-\alpha z]$$
if $z < 0$. So basically,
$$\mathrm{ReLU}[\alpha z] = -\alpha\cdot\mathrm{ReLU}[z]$$
for $\alpha<0$.

**Problem 3.17** Equations 3.11 and 3.12 define a general neural network with Di inputs, one
hidden layer containing D hidden units, and Do outputs. Find an expression for the number of
parameters in the model in terms of Di, D, and Do.

- Input to hidden layer: $D_i D$ weights, $D_i$ biases
- Hidden to output layer: $D D_o$ weights, $D$ biases

In total, this makes for
$$D_iD + D_i + DD_o + D$$
parameters.
