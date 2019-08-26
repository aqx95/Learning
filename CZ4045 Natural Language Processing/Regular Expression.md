
#2. Regrex, Text Normalization, Edit Distance


##Regular Expression
_Algebraic notation for characterizing a set of strings._

Involves having a pattern to search for, and a corpus (a collection of computer-readable text) of text to search through.

### Regrex Patterns

![alt text](/img/Regrex1.png "Regrex 1")
![alt text](/img/Regrex1.png "Regrex 1")



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
![alt text](/img/Regrex1.png "Regrex 1")

_Regrex are greedy; always match largest string_

#### Error Rates
1. False Positive (increase Precision)
2. False Negative (increase Recall)


#### Substitution, Capture Groups
e.g _s/([0-9]+)/<\1>/_<br>
\1 operator is used to refer back to first pattern enclosed by ()

e.g _the (.*)er they were, the \1er they will be_ <br>
set constraint for same string

Capture Group: use of () to store pattern in memory (register)
Non-Capturing group: (?: pattern)

<br>

### Words
