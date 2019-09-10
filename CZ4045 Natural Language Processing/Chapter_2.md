# N-gram Language Models

Assigning **probabilities** to next possible word/sequence (important in identifying words in noisy input)

1. Spelling correction
2. Machine translation

**n-gram**: sequence of n-words

####Problem:
Language is creative, there isn't enough data to accurately estimate probabilities from counts

#####Relative Frequency count
$$P(w|h) = P(the|its water is so transparent that ) \\ = \frac{C(its water is so transparent that the)}{C(its water its so transparent that)}$$

#####Joint Probability
$$P(X_{1}..X_{n}) = P(X_{1})P(X_{2}|X_{1})P(X_{3}|X^{2}_{1})...P(X_{n}|X^{n-1}_{1}) \\
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

####Perplexity (evaluation metric for language model)
Probability of the test set, normalised by number of words

$$ PP(W) = \sqrt[N]{\prod_{i=1}^N \frac{1}{P(w_i|w_{i-1})}} $$


*Minimizing perplexity = Maximizing probability*
Perplexity of any 2 language model is comporable only if they use identical vocabulary

<br>

###Generalization and Zeros
n-grams dependent on training corpus

1. n-grams do better job of modeling training corpus with increasing N.
2. Probabilities often encode specific facts about a given training corpus

#####Things to note
- Use training corpus that has similar genre to the task we are trying to accomplish
- Get training data with appropriate dialect

##### Problems of Zero probability n-gram
1. Underestimate probability of all sorts of words that might occur; hurt performance
2. Can't compute perplexity; zero probability


#### Out of Vocab (OOV)
- Unknown words
We model unknown words by adding pseudo-word,<UNK>

1. Turn problem back into closed vocabulary
2. Replace word in training set by <UNK> based on frequency
