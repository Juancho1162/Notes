#matemáticas #matemáticas/estadística
####  The Probability Space
A probability space is a mathematical triplet ($\Omega$, $\mathcal{F}$, $\mathcal{P}$) that represent a **model** in which $\Omega$, $\mathcal{F}$, $\mathcal{P}$ need to be defined, fulfilling certain conditions. Formally, a **probability space** is a **measure space** such that the measure of the whole space is equal to one.

- **The *Sample Space $\Omega$*** is the set of all possible outcomes. An outcome is the result of a single execution of the model. **Is an arbitrary non-empty set.**
- The ***$\mathbf{\sigma}$-algebra ($\mathcal{F}$)*** **is a set of subsets ($\mathcal{A}$) of $\Omega$, called events** such that:
	- $\Omega \in \mathcal{F}$
	- If $A \in \mathcal{F}$, then $\{x \in \Omega / x \notin A\} = \mathcal{A}^{c}(\Omega)$ $\in \mathcal{F}$. *This assures coherence, without this condition we couldn't define things like "the probability of the Event A1 not happening"*.
	- If $\mathcal{A}_i \in \mathcal{F}$ $for$ $i=1,2,...,$ then also $(\bigcup_{i=1} ^\infty \mathcal{A}_i)$ $\in \mathcal{F}$. *This assures that every possible union of events exists.*
		- As a corollary from the previous two properties and *De Morgan's laws*$(A \cup B)^c = A^c \cap B^c$, and ($A \cap B)^c = A^c \cup B^c$. If $\mathcal{A}_i \in \mathcal{F}$ for $i=1,2,...,$ then also $(\bigcap_{i=1}^{\infty} \mathcal{A}_i) \in \mathcal{F}$. *This let us to consider the probability of simultaneous events, even infinite number of events, very useful in cases as convergences in stochastic processes. Consider a case of several lights that turn on and off following a "rule", let's say the event $\mathcal{A}_i$ is "in the minute i, every lights are off", the event $(\bigcap_{i=x} ^\infty \mathcal{A}_i)$ represents that the lights are turn off since the minute x to the infinite.*
- The ***probability measure $\mathcal{P}$*** is a set function returning an event's probability. $\mathcal{P} : \mathcal{F} \rightarrow [0,1]$ such that:
	- The measure of the entire sample space is equal to one: $\mathcal{P}(\Omega)=1$.
	- $\mathcal{P}$ is countably additive (also called $\sigma$-*additive*). If $\{\mathcal{A}_{i=1}^{\infty}\} \subseteq \mathcal{F}$ is a countable collection of pairwise disjoint sets (if $i \neq j$ then $\mathcal{A}_i \cap \mathcal{A}_j = \emptyset$), then $\mathcal{P}(\bigcup_{i=1} ^\infty \mathcal{A}_i) = \sum_{i=1}^\infty \mathcal{P}(\mathcal{A_i})$.
	- We could add a third axiom (to mimic the Kolmogorov axioms) such that:  $0 \leq \mathcal{P}(A) \leq 1$  $\forall \mathcal{A} \in \mathcal{F}$, that is implied in the definition of $\mathcal{P}$ as $\mathcal{P} :\mathcal{F} \rightarrow [0,1]$.

#### Definitions of Probability
The previous definition of probability is purely formal and does not give an actual meaning to the term probability. Let's do a brief explanation about the two most common definitions. 
###### Frequentist Probability Definition (Richard Von Mises)
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

###### Laplace Probability (Pierre-Simon Laplace (1749-1827))
We call an experiment a **Laplace experiment** if the number of possible simple events is finite and all the outcomes are equally probable. The probability based on that conditions is defined as follows:
$$
P(A)=\frac{C(A)}{C(\Omega)}\text{, being $C(X)$ the cardinality of X.}
$$

###### Subjective Probability Definition
*(Related to Bayesian Philosophy of Science)*
The subjective definition of probability, as advocated by Bruno de Finetti, diverges from the classical interpretations of probability, venturing into the realm of personal belief and uncertainty. This view rejects the notion that probability is a physical or empirical property of the external world and argued instead that is a measure of an individual's  personal belief or degree of confidence in the occurrence of a particular event, based on the information available at the time.

Based on this, probability is not objective or universal; rather, it is personal and varies from one individual to another, depending on their knowledge, experience, and analysis of the available information. **The probability of an event is, therefore, an expression of a person's willingness to bet on the occurrence of that event.**

