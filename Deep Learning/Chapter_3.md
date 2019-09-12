# Probability and Information Theory

**Probability theory** a mathematical framework for representing uncertain statements.

#### Why Probability in ML ?
1. Deal with uncertain quantities
2. Deal with stochastic quantities

#### Types of Probability
1. Frequentist probability
2. Bayesian probability

<br>

### Probability Distribution
How likely a random variable takes on each of the possible states.

#### Discrete Variables
Described using **Probability mass function (PMF)**, _P_. It maps from a state of a random variable to the probability of that random variable taking on that state.


#### Continuous Variable
Described using **Probability density function (PDF)**
- Integrate density function to find actual probability mass of a set of points

<br>

### Marginal Probability
Probability distribution over a subset of variables

**Sum Rule (discrete)**
$$ \forall x \in \text x, P(\text x = x) = \sum_y P(\text x = x, \text y = y)
$$

**Continuous**
$$ p(x) = \int p(x,y)dy $$

<br>

### Conditional Probability

$$ P(y=\text y | x=\text x) = \frac{P(\text y = y, \text x = x)}{P(\text x = x)} $$

<br>

### Chain Rule of Conditional Probability
$$
P(x^1,...,x^n) = P(x^1)\prod_{i=2}^nP(x^i|x^1,..,x^{(n-1)})
$$
Decompose joint probability distribution over many random variable into conditional distribution over one variable.

<br>

### Independence & Conditional Independence

**Independent**
$$ \forall x \in \text x, y \in \text y,  p(\text x = x, \text y = y) = p(\text x = x)p(\text y = y)
$$

**Conditionally Independent**
$$ \forall x \in \text x, y \in \text y, z \in \text z, p(\text x = x, \text y = y | \text z = z) = p(\text x = x | \text z = z)p(\text y = y | \text z = z)
$$


### Expectation, Variance, Covariance

#### Expectation

Discrete Variables
$$ \mathbb E_{xP} |f(x)| = \sum_x P(x)f(x) $$

Continuous Variables
$$ \mathbb E_{xP} |f(x)| = \int p(x)f(x)dx $$

#### Variance
$$
Var(f(x)) = \mathbb E[f(x) - \mathbb E[f(x)]^2]
$$

#### Covariance
Indicate how much two values are linearly related to each other, as well as scale of these variables
$$
Cov(f(x),g(y)) = \mathbb E[(f(x)-\mathbb E[f(x)])(g(y)-\mathbb E[g(y)])]
$$

### Common Probability Distribution

#### Bernoulli Distribution
- Distribution over a single **binary** random variable


#### Multinoulli Distribution
- Distribution over a **single discrete** variable with *k* different state


#### Gaussian Distribution
**Why Gaussian is good choice for real number distribution without prior knowledge?**
1. Central Limit Theorem
- sum of many independent random variables is approximately normally distributed.
2. Encodes maximum amount of uncertainty over real number

### Exponential & Laplace Distribution
In deep learning, want to have probability distribution with a sharp point at *x* = 0

#### Exponential

#### Laplace


#### Dirac & Empirical Distribution
