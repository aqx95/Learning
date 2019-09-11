
# 2. Regrex, Text Normalization, Edit Distance


## Regular Expression
_Algebraic notation for characterizing a set of strings._

Involves having a pattern to search for, and a corpus (a collection of computer-readable text) of text to search through.

### Regrex Patterns

![Regrex](img/regrex1.png "pattern1")
![Regrex](img/regrex2.png "pattern2")
![Regrex](img/regrex3.png "pattern3")
![Regrex](img/regrex4.png "pattern4")
![Regrex](img/regrex5.png "pattern5")
![Regrex](img/regrex6.png "pattern6")
![Regrex](img/regrex7.png "pattern7")
![Regrex](img/regrex8.png "pattern8")


**^** : 1. matches start of string
2. Negation (if it comes after the opening bracket)
3. Represent ^

**$** : match end of string

**\b..\b** : word boundary (*word* defined as sequence of digits, underscores or letters)

#### Disjunction, Grouping and Precedence

**|** : disjunction operator

**()** : parenthesis operator; enclosed pattern act like character

##### Operator Precedence Hierarchy
![Hierarchy](img/op_hierarchy.png "op")

_Regrex are greedy; always match largest string_

#### Error Rates
1. False Positive (increase Precision)
2. False Negative (increase Recall)


#### Substitution, Capture Groups
e.g _([0-9]+)/<\1>_<br>
\1 operator is used to refer back to first pattern enclosed by ()

e.g _the (.*)er they were, the \1er they will be_ <br>
set constraint for same string

Capture Group: use of () to store pattern in memory (register)

Non-Capturing group: (?: pattern)

<br>
<br>
<br>

## Words

**Utterance** (2 kinds of disfluencies)

1. fragment : broken-off word
2. fillers : uhm, uh etc


**Lemma** <br>
a set of lexical forms having the same stem, the same major part-of-speech, and same word sense

**Types**<br>
number of distinct words

**Tokens**<br>
total number N of running words

<br>


#### Herdan's Law
states the relationship between types |V| & number of tokens N.

$$|V| = kN^{\beta}$$

where $k$ and $\beta$ are positive constant, 0 < $\beta$ < 1


### Text Normalization

1. Tokenization
2. Normalizing
3. Segmenting sentences

**Clitic** : a part of a word that can't stand on its own, can only occur when it is attached to another word.

#####Common tokenization standard
Penn Treebank tokenization

#### Word Segmentation
**Problems**: some languages (Chinese Japanese) does not use space to mark separate words

**Solution**: Maximum-Matching (requires dictionary)

![MaxMatch](img/maxmatch.png)

![MaxMatch](img/output_maxmatch.png)

**Metric** : Word error rate, compute using normalised minimum edit distance (output vs actual)

#### Lemmatization & Stemming

**Lemmatization** is the task of determining that two words have the same root, despite their surface differences

Sophisticated method of Lemmatization involves morphological parsing.
**Morphology** is the study of
morpheme the way words are built up from smaller meaning-bearing units called **morphemes**

**Morphemes**
1. Stems : central morpheme of word, supplying main meaning
2. Affixes : adding 'additional' meaning of various kinds

e.g A morphological parser takes a word like cats and parses it into the two morphemes _cat_ and _s_

**Stemming**
mainly consists of chopping off word-final affixes
<br>
e.g Porter Stemmer

#### Byte-Pair Encoding
tackle the problem of unknown words, words that a system has not seen before

Intuition of the algorithm is to iteratively merge frequent pairs of characters

#### Sentence Segmentation
In general, sentence tokenization methods work by building a binary classifier (based on a sequence of rules or on machine learning) that decides if a period is part of the word or is a sentence-boundary marker.


### Minimum Edit Distance
**Definition**: minimum number of editing operations (insertion, deletion, substitution) needed to transform one string into another.

Uses dynamic programming: large problems solve by combining solutions to sub problem.

Usefulness:
1. Spelling error correction
2. Provide minimum cost alignment between 2 strings

**Algorithm**

![Min_dist](img/min_dist.png)