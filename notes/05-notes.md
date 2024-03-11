# Chapter 5 notes: Loss Functions

> This chapter ... **justifies the choice of the least squares criterion for real-valued outputs** and allows us to build loss functions for other prediction types.

> We consider binary classification, where the prediction y ∈ {0, 1} is one of two categories, multiclass classification, where the prediction y ∈ {1, 2, . . . , K} is one of K categories, and more complex cases. In the following two chapters, we address model training, where the goal is to find the parameter values that minimize these loss functions.

## 5.1 Maximum likelihood

New idea: consider the model as computing a **conditional probability distribution** $Pr(\bf{y}\mid\bf{x})$ over possible outputs $\bf{y}$ given input $\bf{x}$.

The goal is to maximize the probability of us seeing the training data given our suggested model.

Assumption: data are _independent and identically distributed_ (i.i.d) (p. 58)

Definition of log function:

$$
L[\phi] = -\sum_{i=1}^I \log[\Pr(\bf{y}_i \mid \bf f[\bf{x}_i, \phi])]
$$

## 5.2 Recipe for constructing loss functions

The recipe for constructing loss functions for training data $\{x_i, y_i\}$ using the maximum
likelihood approach is hence:

1. Choose a suitable probability distribution P r(y|θ) defined over the domain of the
   predictions y with distribution parameters θ.
2. Set the machine learning model f[x, ϕ] to predict one or more of these parameters,
   so θ = f[x, ϕ] and P r(y|θ) = P r(y|f[x, ϕ]).
3. To train the model, find the network parameters ϕˆ that minimize the negative
   log-likelihood loss function over the training dataset pairs
   $$\hat{\phi} = \argmin_{\phi}\Big[L[\phi]\Big] = \argmin{\phi}\Bigg[-\sum_{i=1}^I \log\Big[\Pr(\bf{y}_i \mid \bf{f}[\bf{x}_i, \phi])\Big]\Bigg].$$

. (5.6) 4. To perform inference for a new test example x, return either the full distribution P r(y|f[x, ϕˆ]) or the maximum of this distribution.

### 5.3.4 Heteroscedatic regression (64)

For a regression problem, instead of just predicting the mean, we can also predict the _variance_ at every input. This gives us two outputs, which together determine the modeled distribution of the ouptut. The loss function can be computed at every training input.

Seems like this is very useful.

Figure 5.11 is a table, has some interesting

- "what is your data type?"
- "what is your output domain?"
- "what is your distribution?"
- "then use this thing"

## Notes

"Learning to rank" &mdash; there are models that can rank inputs. Wow.

- "Mixture of Gaussians" density ? ![Figure 5.14](images/fig-5.14)
