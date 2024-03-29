# N-gram Language Models

Assigning **probabilities** to next possible word/sequence (important in identifying words in noisy input)

1. Spelling correction
2. Machine translation

**n-gram**: sequence of n-words

#### Problem:
1. Language is creative, there isn't enough data to accurately estimate probabilities from counts (a lot of zero counts)
2.  A lot of estimation to get joint probability of a word sequence
<br>

##### Relative Frequency count
$$P(w|h) = P(the|its water is so transparent that ) \\ = \frac{C(its water is so transparent that the)}{C(its water its so transparent that)}$$

##### Joint Probability
$$
P(X_{1}..X_{n}) = P(X_{1})P(X_{2}|X_{1})P(X_{3}|X^{2}_{1})...P(X_{n}|X^{n-1}_{1}) \\
= \prod_{k=1}^n P(X_{k}|X_{1}^{k-1})
$$

<br>

**Intuition of n-gram**: approximate history *h* of words by just the last few words

#### Markov assumption
Probability of a word depends only on the previous word

**Bi-gram**

- Next word in the sequence:
$$ P(w_{n}|w_{1}^{n-1}) \approx P(w_{n}|w_{n-N+1}^{n-1})
$$
- Complete word sequence
$$ P(w_{1}^n) \approx \prod_{k=1}^n P(w_{k}|w_{k-1}) $$

<br>

##### Estimating bi-gram probabilities (MLE)
$$ P(w_n|w_{n-1}) = \frac{C(w_{n-1}w_{n})}{C(w_{n-1})}
$$

*sum of all bigrams count starting with word $w_{n-1}$ equal to unigram count for word $w_{n-1}$*

##### More generally
$$ P(w_n|w_{n-N+1}^{n-1}) = \frac{C(w_{n-N+1}^{n-1}w_{n})}{C(w_{n-N+1}^{n-1})}
$$

<br>

##### Computing probabilities in log format
- Multiplying probabilities may lead to numerical underflow
$$
p1 \times p2 \times p3 \times p4 = exp(\log{p1} + \log{p2} + \log{p3} + \log{p4})  
$$

<br>

#### Perplexity (evaluation metric for language model)
Probability of the test set, normalised by number of words

$$ PP(W) = \sqrt[N]{\prod_{i=1}^N \frac{1}{P(w_i|w_{i-1})}} $$


*Minimizing perplexity = Maximizing probability*

Perplexity of any 2 language model is comporable only if they use identical vocabulary

<br>

### Generalization and Zeros
n-grams dependent on training corpus

1. n-grams do better job of modeling training corpus with increasing N.
2. Probabilities often encode specific facts about a given training corpus

##### Things to note
- Use training corpus that has similar genre to the task we are trying to accomplish
- Get training data with appropriate dialect

##### Problems of Zero probability n-gram
1. Underestimate probability of all sorts of words that might occur; hurt performance
2. Can't compute perplexity; zero probability


#### Out of Vocab (OOV)
Unknown words.
We model unknown words by adding pseudo-word,<UNK>

1. Turn problem back into closed vocabulary
    * Choose a vocabulary that is fixed in advance
    * Convert training set of any word not in this set to <'UNK'>
    * Estimate probabilities for <'UNK'> from its count
    
2. Replace word in training set by <'UNK'> based on frequency
    * Replace by <UNK> all words that occur fewer than n times in the training set, where n is some small number


**Perplexity should be compared across language model with similar vocabulary**(choice of <'UNK'> will have effect on perplexity)


<br>

### Smoothing

Distributing probability mass from frequent events and give it to events never seen before (avoiding langage model from assigning zero probability)

#### Laplace Smoothing

**Discount**
$$ d_c = \frac{c*}{c} $$
where $c*$ is the discounted count

**For bi-grams**
$$ P_{Laplace}(w_n|w_{n-1}) = \frac{C(w_n,w_{n-1})+1}{C(w_n-1)+V} $$

1. There will be sharp changes in counts and probabilities
2. Practical for text classification


#### Add-k Smoothing
Add a fractional count instead (0.5?, 0,05?, 0.1?)
**For bi-grams**
$$ P_{Add-k}(w_n|w_{n-1}) = \frac{C(w_n,w_{n-1})+k}{C(w_n-1)+kV} $$

1. Optimizing on devset to  choose k value


#### Backoff & Interpolation
Intuition: Using less context is a good thing, helping to generalize more for contexts that the model hasn’t learned much about

**Backoff**
Using lower order n-gram if we have zero evidence for higher order n-gram
1. Need to discount higher order n-grams to save probability mass for lower order n-gram

![backoff](img/backoff.png)


**Interpolation**
Mix probability estimates from all the n-gram estimators

$$
P(w_n|w_{n-2}w_{n-1}) = \lambda_1P(w_n|w_{n-2}w_{n-1}) + \lambda_2P(w_n|w_{n-1}) + \lambda_3P(w_n)
$$
Where $\sum_{i}\lambda_i = 1$

1. $\lambda$ learned from held-out set (find values that maximise likelihood of held out set)

#### Kneser-Ney Smoothing
Uses **Absolute discounting**: subtracting a fixed discount *d* from each count
1. Look at count for all the bigrams count {0...}

![kneser](img/kneser.png)

2. Subtract fixed discount *d* from each count
