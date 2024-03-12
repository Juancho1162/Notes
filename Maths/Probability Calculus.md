####  1. The Probability Space
A probability space is a mathematical triplet ($\Omega$, $\mathcal{F}$, $\mathcal{P}$) that represent a **model** in which $\Omega$, $\mathcal{F}$, $\mathcal{P}$ need to be defined, fulfilling certain conditions. Formally, a **probability space** is a **measure space** such that the measure of the whole space is equal to one.

- **The *Sample Space $\Omega$*** is the set of all possible outcomes. An outcome is the result of a single execution of the model. **Is an arbitrary non-empty set.**
- The ***$\mathbf{\sigma}$-algebra ($\mathcal{F}$)*** **is a set of subsets ($\mathcal{A}$) of $\Omega$, called events** such that:
	- $\Omega \in \mathcal{F}$
	- If $A \in \mathcal{F}$, then $\{x \in \Omega / x \notin A\} = \mathcal{A}^{c}(\Omega)$ $\in \mathcal{F}$. *This assures coherence, without this condition we couldn't define things like "the probability of the Event A1 not happening"*.
	- If $\mathcal{A}_i \in \mathcal{F}$ $for$ $i=1,2,...,$ then also $(\bigcup_{i=1} ^\infty \mathcal{A}_i)$ $\in \mathcal{F}$. *This assures that every possible union of events exists.*
		- As a corollary from the previous two properties and *De Morgan's laws*$(A \cup B)^c = A^c \cap B^c$, and ($A \cap B)^c = A^c \cup B^c$. If $\mathcal{A}_i \in \mathcal{F}$ for $i=1,2,...,$ then also $(\bigcap_{i=1}^{\infty} \mathcal{A}_i) \in \mathcal{F}$. *This let us to consider the probability of simultaneous events, even infinite number of events, very useful in cases as convergences in stochastic processes. Consider a case of several lights that turn on and off following a "rule", let's say the event $\mathcal{A}_i$ is "in the minute i, every lights are off", the event $(\bigcap_{i=x} ^\infty \mathcal{A}_i)$ represents that the lights are turn off forever since the minute x.*
- The ***probability measure $\mathcal{P}$*** is a set function returning an event's probability. $\mathcal{P} : \mathcal{F} \rightarrow [0,1]$ such that:
	- The measure of the entire sample space is equal to one: $\mathcal{P}(\Omega)=1$.
	- $\mathcal{P}$ is countably additive (also called $\sigma$-*additive*). If $\{\mathcal{A}_{i=1}^{\infty}\} \subseteq \mathcal{F}$ is a countable collection of pairwise disjoint sets (if $i \neq j$ then $\mathcal{A}_i \cap \mathcal{A}_j = \emptyset$), then $\mathcal{P}(\bigcup_{i=1} ^\infty \mathcal{A}_i) = \sum_{i=1}^\infty \mathcal{P}(\mathcal{A_i})$.
	- We could add a third axiom (to mimic the Kolmogorov axioms) such that:  $0 \leq \mathcal{P}(A) \leq 1$  $\forall \mathcal{A} \in \mathcal{F}$, that is implied in the definition of $\mathcal{P}$ as $\mathcal{P} :\mathcal{F} \rightarrow [0,1]$.

#### 2. Definitions of Probability
The previous definition of probability is purely formal and does not give an actual meaning to the term probability. Let's do a brief explanation about the two most common definitions. 
###### 2.1 Frequentist Probability Definition (Richard Von Mises)
There is a close connection between the relative frequency and probability of an event. A random experiment is described by its possible outcomes. Suppose an experiment has $m$ possible outcomes $A_1, A_2, ..., A_m$  and the experiment is repeated n times. Now we can count how many times each of the possible outcomes has occurred, the **absolute frequency**, which is the number of times the event  $A_i$  has happened:
$$
n_i = n(A_i)
$$
The **relative frequency** of a random event  $A_i$  with $n$ repetitions of the experiment, is calculated as:
$$
f_i = f(A_i) = \frac{n_i}{n}
$$
If we assume that the experiment is repeated a large number of times and the experimental conditions remain the same over all repetitions, then the relative frequency $f(A)$ converges to a limiting value for $A$. **This limiting value is interpreted as the probability of $A$ and is denoted by $P(A)$, i.e.**
$$
P(A) = \lim_{n \to \infty} \frac{n(A)}{n}
$$

###### 2.2 Laplace Probability (Pierre-Simon Laplace (1749-1827))
We call an experiment a **Laplace experiment** if the number of possible simple events (*events that are formed by only one element of the sample space*) is finite and all the outcomes are equally probable. The probability based on that conditions is defined as follows:
$$
P(A)=\frac{C(A)}{C(\Omega)}\text{, being $C(X)$ the cardinality of X.}
$$

###### 2.3 Subjective Probability Definition
*(Related to Bayesian Philosophy of Science)*
The subjective definition of probability, as advocated by Bruno de Finetti, diverges from the classical interpretations of probability, venturing into the realm of personal belief and uncertainty. This view rejects the notion that probability is a physical or empirical property of the external world and argued instead that is a measure of an individual's  personal belief or degree of confidence in the occurrence of a particular event, based on the information available at the time.

Based on this, probability is not objective or universal; rather, it is personal and varies from one individual to another, depending on their knowledge, experience, and analysis of the available information. **The probability of an event is, therefore, an expression of a person's willingness to bet on the occurrence of that event.**

Still in order to assure coherence, the assigned probabilities must comply with the axioms of probability to ensure that there are no sets of bets that guarantee a loss (or gain) regardless of the outcomes of the events.

*Suppose you assign a probability of 0.6 to "Heads" and a probability of 0.5 to "Tails." This assignment violates the second axiom because the total probability exceeds 1 (0.6 + 0.5 = 1.1).* 

###### 2.4 Corollaries Following from Kolmogorov's Axioms
We actually defined this axioms in the first section, but let's define them again:
$$
\begin{gather}
\text{\textbf{Axiom 1} Every random event $A$ has a probability in the closed interval $[0,1]$, i.e.}\\
0 \leq P(A) \leq 1 \\
\text{\textbf{Axiom 2} The sure event has probability 1, i.e.} \\
P(\Omega) = 1 \\
\text{\textbf{Axiom 3} If $i \neq j$ then $\mathcal{A}_i \cap \mathcal{A}_j = \emptyset$, then $\mathcal{P}(\bigcup_{i=1} ^\infty \mathcal{A}_i) = \sum_{i=1}^\infty \mathcal{P}(\mathcal{A_i})$.} \\
\\
\end{gather}
$$
**Corollary 1**: *The probability of the complementary event of A, (i.e. $\bar{A}$ ) is:*
$$
P(\bar{A}) = 1 - P(A)   
$$
**Corollary 2**: *The probability of occurrence of an imposible event $\emptyset$ is zero:*
$$
P(\emptyset)=P(\bar{\Omega}) = 1-P(\Omega) = 0
$$
**Corollary 3**: *Let $A_1$ and $A_2$ be not necessarily disjoint events. The probability of occurrence of $A_1$ and $A_2$ is:*
$$
P(A_1 \cup A_2) = P(A_1) + P(A_2) - P(A_1 \cap A_2)
$$
**Corollary 4**: *If $A \subseteq B \text{ then } P(A) \leq P(B)$*

We just describe a good amount of theory, now we will create an example to illustrate some of the concepts.

###### 2.5 Example, Poker Card Deck
The experiment consists of the following: **We will randomly draw a card** from a poker deck that contains 52 cards:

- $\Omega$ = {*Each individual card*},  $C(\Omega) = 52$.
- $\sigma-algebra (\mathcal{F})$:   This is the collection of all events we can form from the sample space, including all subsets of $\Omega$. For example, an event might be drawing a heart, which includes all hearts in the deck. $\mathcal{F}$  includes both simple events (like drawing a specific card) and compound events (like drawing a card of a particular suit or value). It also includes the sample space itself $\Omega$ and the empty set $\emptyset$, representing an impossible event. 
$$
\mathcal{F} = \{\emptyset,\Omega, A_1, ..., A_n \}
$$
- Probability Measure  $\mathcal{P}$: This assigns a probability in each event in $\mathcal{F}$, following the Kolmogorov's axioms.

As we have a finite number of  simple possible events, and all the outcomes are equally probable we are going to use the **Laplace Probability**:
$$
P(A) = \frac{C(A)}{C(\Omega)}
$$
**Example 1: (Corollary 1)**:
If $A_1$ is the event of drawing a heart from the deck, $P(A_1)= \frac{13}{52}$. Then, the complementary event, $\bar{A_1}$ would be not drawing a heart, which includes drawing any of the other 39 cards. Using Corollary 1:
$$
P(\bar{A_1}) = 1 - P(A_1) = 1-\frac{13}{52} = \frac{3}{4}
$$
**Example 2: (Corollary 3)**:
Let's consider two events:
- $A_1$: drawing a heart $\rightarrow$ $P(A_1) = \frac{13}{52}$
- $A_2$: drawing a king $\rightarrow$ $P(A_2) = \frac{4}{52}$

These events are not mutually exclusive, as one of the kings is a heart. The probability of drawing the king of hearts is:
$$
P(A_1 \cap A_2) = \frac{1}{52}
$$
So, the probability of drawing a heart or a king is:
$$
P(A_2 \cup A_2) = P(A_1) + P(A_2) - P(A_1 \cap A_2) = \frac{13}{52} + \frac{4}{52} - \frac{1}{52} = \frac{4}{13}
$$
**Example 3: (Corollary 4)**:
Let $A_3$ be the event of drawing the king of hearts ($P(A_1 \cap A_2) = \frac{1}{52}$ ).
It is trivial that $A_3 \subseteq A_1$, and $P(A_3) \leq P(A_1)$ as expected.

#### 3. Conditional Probability
Let $P(A) > 0$. Then the conditional probability of event $B$ occurring, given that event $A$ has already occurred, is:
$$
P(B|A)= \frac{P(A\cap B)}{P(A)}
$$
We can also define:
$$
P(A|B)= \frac{P(A\cap B)}{P(B)}
$$
Let's say we are doing a COVID test with this relatives frequencies:

|          | Present | Absent | Total(row) |
| -------- | ------- | ------ | ---------- |
| Positive | 0.30    | 0.10   | 0.40       |
| Negative | 0.15    | 0.45   | 0.60       |
| Total    | 0.45    | 0.55   | 1          |

The event $A$ represents having a positive test ($P(A) = 0.4$), $B$ represents being infected with COVID ($P(A \cap B) = 0.3$), then the probability of, given a positive test, being infected will be:
$$
P(B|A)= \frac{P(A\cap B)}{P(A)}=\frac{0.3}{0.4} = 0.75
$$
**Multiplication Theorem of Probability**: (*This theorem follows directly from the two first definitions without requiring P(A) >0 and P(B) >0*)
$$
P(A\cap B)=P(B|A)P(A)=P(A|B)P(B)
$$
**Law of Total Probability**
