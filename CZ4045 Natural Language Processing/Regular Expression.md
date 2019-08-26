
# 2. Regrex, Text Normalization, Edit Distance


## Regular Expression
_Algebraic notation for characterizing a set of strings._

Involves having a pattern to search for, and a corpus (a collection of computer-readable text) of text to search through.

### Regrex Patterns

![Regrex](https://github.com/aqx95/Uni_Notes/blob/master/CZ4045%20Natural%20Language%20Processing/img/regrex1.png "pattern1")
![Regrex](https://github.com/aqx95/Uni_Notes/blob/master/CZ4045%20Natural%20Language%20Processing/img/regrex2.png "pattern2")
![Regrex](https://github.com/aqx95/Uni_Notes/blob/master/CZ4045%20Natural%20Language%20Processing/img/regrex3.png "pattern3")
![Regrex](https://github.com/aqx95/Uni_Notes/blob/master/CZ4045%20Natural%20Language%20Processing/img/regrex4.png "pattern4")
![Regrex](https://github.com/aqx95/Uni_Notes/blob/master/CZ4045%20Natural%20Language%20Processing/img/regrex5.png "pattern5")
![Regrex](https://github.com/aqx95/Uni_Notes/blob/master/CZ4045%20Natural%20Language%20Processing/img/regrex6.png "pattern6")
![Regrex](https://github.com/aqx95/Uni_Notes/blob/master/CZ4045%20Natural%20Language%20Processing/img/regrex7.png "pattern7")
![Regrex](https://github.com/aqx95/Uni_Notes/blob/master/CZ4045%20Natural%20Language%20Processing/img/regrex8.png "pattern8")



**?** : 0 or 1 instance of the preceding term

**\*** : 0 or more instance of the preceding term

**+** : 1 or more occurrence of the preceding term

**^** : 1. matches start of string
2. Negation (if it comes after the opening bracket)
3. Represent ^

**$** : match end of string

**\b..\b** : word boundary (*word* defined as sequence of digits, underscores or letters)

#### Disjunction, Grouping and Precedence

**|** : disjunction operator

**()** : parenthesis operator; enclosed pattern act like character

##### Operator Precedence Hierarchy
![Hierarchy](https://github.com/aqx95/Uni_Notes/blob/master/CZ4045%20Natural%20Language%20Processing/img/op_hierarchy.png "op")

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

### Words
