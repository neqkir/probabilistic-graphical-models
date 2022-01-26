### probabilistic-graphical-models

Types of models

* Markov models (undirected graphs)

* Bayesian models (directed graphs) 

Examples

> Image segmentation: RV are labels for pixels, edges represent relationships between labels (this is a Bayesian network)

> Medical diagnosis through diagnostic questions

> Text information retrieval, retrieving for instance information about persons, locations and organization in a text, one variable for each word, which encodes the label for that word (person, location, organization)

> Biological network reconstruction, for instance discovering new relationships between proteins

Three aspects: Representation, Learning and Inference

A factor 
<img src="https://render.githubusercontent.com/render/math?math=\phi(X_{1},...,X_{n})">
is a real valued function, its scope 
<img src="https://render.githubusercontent.com/render/math?math={X_{1},...,X_{n}}"> 
is the set of used RVs, or the set of arguments which the factor takes. 

A joint distribution, e.g., 
<img src="https://render.githubusercontent.com/render/math?math=P(X_{1},...,X_{n})"> 
is a factor when for every combination of 
<img src="https://render.githubusercontent.com/render/math?math=X_{1},X_{2},X_{3}"> 
we get a value. An unnormalize measure is a factor also, e.g., 
P(X〗_1,X_2,x_3,0) which scope is 〖{X〗_1,X_2}. A conditional probability distribution is a factor, e.g., 〖P(X〗_1 |X_2,X_3) meaning that for every combination of values for X_2 and X_3 we have a probability distribution over X_1.  

Factor operations include

> Factor products, multiplying values for the different factors, the scope is the union of the multiplied scopes

> Factor marginalization, marginalizing out part of the scope by summing values over those marginalized dimensions, and reducing the scope accordingly
	
> Factor reduction, fixing the value taken by a subset of the RVs, and reducing the scope accordingly

A Bayesian Network is a Directed Acyclic Graph (DAG) whose nodes represent the RVs X_1,X_2,…,X_n. For each node X_i is defined a conditional probability distribution on its parents 〖P(X〗_i |〖Par〗_G (X_i )). The Bayesian Network represents a joint distribution via the chain rule for Bayesian Networks 〖P(X〗_1,〖…,X〗_n)= ∏▒〖〖P(X〗_i |〖Par〗_G (X_i ))〗. We say that the probability distribution factorizes over G. 

Different reasoning patterns: 

> Causal reasoning chaining probabilities down from the parents 

> Evidential reasoning chaining probabilities up to the parents
	
> Intercausal reasoning

Probabilistic distributions flow – an active trail is a trail X_1-…-X_n where for any v-structure X_(i-1)→X_i←X_(i+1) we have X_i part of the observed variables (the v-structure is said to be activated) and no other X_i is observed. 

Conditional independence 

P satisfies X⊥Y | Z if P(X,Y | Z)= P(Y | Z)*P(X | Z) or equivalently P(X ┤|Y,Z)= P(X | Z) or equivalently P(Y ┤|X,Z)= P(Y | Z).

D-separation – X and Y are d-separated in G given Z if there is no active trail in G between X and Y given Z, notation 〖d-sep〗_G (X,Y ┤|  Z). 

 
 
