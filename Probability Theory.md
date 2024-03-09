#matemáticas #matemáticas/estadística
#### The Probability Space
A probability space is a mathematical triplet ($\Omega$, $\mathcal{F}$, $\mathcal{P}$) that represent a **model** in which $\Omega$, $\mathcal{F}$, $\mathcal{P}$ need to be defined, fulfilling certain conditions.

- **The *Sample Space $\Omega$*** is the set of all possible outcomes. An outcome is the result of a single execution of the model. **Is an arbitrary non-empty set.**
- The ***$\mathbf{\sigma}$-algebra ($\mathcal{F}$)*** **is a set of subsets of $\Omega$, called events** such that:
	- $\Omega \in \mathcal{F}$
	- If $A \in \mathcal{F}$, then $\{x \in \Omega / x \notin A\} = \mathcal{A}^{c}(\Omega)$ $\in \mathcal{F}$. *This assures coherence, without this condition we couldn't define things like "the probability of the Event A1 not happening"*.
	- If $\mathcal{A}_i \in \mathcal{F}$ $for$ $i=1,2,...,$ then also $(\bigcup_{i=1} ^\infty \mathcal{A}_i)$ $\in \mathcal{F}$. *This assures that every possible union of events exists.*
		- As a corollary from the previous two properties and *De Morgan's laws*$(A \cup B)^c = A^c \cap B^c$, and ($A \cap B)^c = A^c \cup B^c$. If $\mathcal{A}_i \in \mathcal{F}$ for $i=1,2,...,$ then also $(\bigcap_{i=1}^{\infty} \mathcal{A}_i) \in \mathcal{F}$. *This let us to consider the probability of simultaneous events, even infinite number of events, very useful in cases as convergences in stochastic processes. Consider a case of several lights that turn on and off following a "rule", let's say the event $\mathcal{A}_i$ is "in the minute i, every lights are off", the event $(\bigcap_{i=x} ^\infty \mathcal{A}_i)$ represents that the lights are turn off since the minute x to the infinite.*
- The **probability measure $\mathcal{P}$** is a set function 



