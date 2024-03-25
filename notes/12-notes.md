# Chapter 12: Transformers

## 12.2 Dot-product self-attention

For an **attention block**, we have the following:

1. Input: $N$ $D$-dimensional vectors, $x_1, x_2, \dots, x_N$
2. Output: Same format

We compute the output by transforming all input vectors with the _same weight matrix and bias vector_. Then, output $i$ is a weighted sum of these transformed inputs, where weights are determined by a function $a$ of $x_i$ and the vector that's being weighted.

Weights are acutually just the softmaxed-dot produts of **key** and **query** vectors, which are computed per-input vector (same weights/biases for every key, and every query).

### 12.3.1 Positional encoding

Add "position signals" to the input.

### 12.3.2 Scaled dot product self-attention

Scale the weights by the square root of the dimension before doing softmax.

### 12.3.3 Multiple heads

If there are $H$ heads, make the value dimension be $D/H$, and recombine outputs at the end.

### 12.5.1 Tokenization

"Byte pair encoding" is used to tokenize datasets.

### 12.5.2. Embedding

Embedding matrix is learned! Input is one-hot vectors.
