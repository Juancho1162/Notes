#matemáticas #matemáticas/estadística
#### The Probability Space
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
	- We could add a third axiom (to mimic the Kolmogorov axioms) such that:  $0 \leq \mathcal{P}(A) \leq 1$    $\forall \mathcal{A} \in \mathcal{F}$, that is implied in the definition of $\mathcal{P}$ as $\mathcal{P} :\mathcal{F} \rightarrow [0,1]$.

#### Definitions of Probability
The previous definition is purely formal and does not give an actual meaning to the term probability. Let's do a brief explanation about the two most common definitions. 
###### Frequentist Probability Definition (Richard Von Mises)
