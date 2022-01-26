### probabilistic graphical models 

[Concepts and definitions, more explanation, following the curriculum of the Coursera Standford online course
https://www.coursera.org/learn/probabilistic-graphical-models] 

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

### Conditional independence

P satisfies 
<img src="https://render.githubusercontent.com/render/math?math=X \perp Y | Z"> 
if 
<img src="https://render.githubusercontent.com/render/math?math=P(X,Y|Z)=P(Y|Z)*P(X|Z)"> 
or equivalently 
<img src="https://render.githubusercontent.com/render/math?math=P(X|Y,Z)=P(X|Z)">
or equivalently
<img src="https://render.githubusercontent.com/render/math?math=P(Y|X,Z)=P(Y|Z)">

### Probabilistic distributions flow 

An active trail is a trail 
<img src="https://render.githubusercontent.com/render/math?math=X_{1}-...-X_{n}">. 
where for any v-structure 
<img src="https://render.githubusercontent.com/render/math?math=X_{i-1} \leftarrow X_{i} \rightarrow X_{i+1}">. 
we have 
<img src="https://render.githubusercontent.com/render/math?math=X_{i}">. 
part of the observed variables (the v-structure is said to be activated) and no other 
<img src="https://render.githubusercontent.com/render/math?math=X_{j}">. 
is observed. 

**More illustrated maths and more on this ; three cases**

(1) tail-tail

<img src="https://user-images.githubusercontent.com/89974426/151158642-1e0eb728-aab3-43b9-adf2-0026e781c222.PNG" width=13% height=13%>

Conditioning on Z in the tail-tail case makes X and Y independent, that is 
<img src="https://render.githubusercontent.com/render/math?math=X \perp Y | Z">.

Indeed, the joint distribution can be factored as 

<img src="https://render.githubusercontent.com/render/math?math=P(X,Y,Z)=P(X|Z)*P(Y|Z)*P(Z)">

and conditioning on Z we get 

<img src="https://render.githubusercontent.com/render/math?math=P(X,Y|Z)= \frac{P(X,Y,Z)}{P(Z)} = \frac{P(X|Z)*P(Y|Z)*P(Z)}{P(Z)} = P(X|Z)*P(Y|Z)">

(2) head-tail

<img src="https://user-images.githubusercontent.com/89974426/151159552-2c92f398-284c-4df4-b1e4-00f79598baf0.PNG" width=6% height=6%>

Likewise conditioning on Z in the head-tail case makes X and Y independent, that is 
<img src="https://render.githubusercontent.com/render/math?math=X \perp Y | Z">.

Indeed, the joint distribution can be factored as 

<img src="https://render.githubusercontent.com/render/math?math=P(X,Y,Z)=P(X)*P(Z|X)*P(Y|Z)">

(if you wonder why refer to the definition of Bayesian Networks above and its chain rule, 

<img src="https://render.githubusercontent.com/render/math?math=P(X_{1},...,X_{n})= \prod{P(X_{i}|Par_{G}(X_{i}))}"> with the above notations, and where 
<img src="https://render.githubusercontent.com/render/math?math=Par_{G}(X_{i})"> refers to the parents nodes for <img src="https://render.githubusercontent.com/render/math?math=X_{i}">)

and conditioning on the value of Z we get (using the Bayes’ theorem)

<img src="https://render.githubusercontent.com/render/math?math=P(X,Y|Z)= \frac{P(X,Y,Z)}{P(Z)} = \frac{P(X)*P(Z|X)*P(Y|Z)}{P(Z)} = \frac{P(X|Z)*P(Y|Z)*P(Z)}{P(Z)} = P(X|Z)*P(Y|Z)">

(3) head-head

<img src="https://user-images.githubusercontent.com/89974426/151161801-6b449afd-9efd-4e8d-9a1c-3901a2d8691d.PNG" width=13% height=13%>

This is trickier. 

We can write as before our joint-distribution 

<img src="https://render.githubusercontent.com/render/math?math=P(X,Y,Z)=P(X)*P(Y)*P(Z|X,Y)">

but here conditioning on Z does not make X and Y necessarily independent. 

We can however write the <img src="https://render.githubusercontent.com/render/math?math=P(X,Y)"> as a marginalization over Z, that is

<img src="https://render.githubusercontent.com/render/math?math=P(X,Y)= \sum_{Z} P(X,Y,Z) = \sum_{Z} P(X)*P(Y)*P(Z|X,Y) = P(X)*P(Y)">

since 
<img src="https://render.githubusercontent.com/render/math?math=\sum_{Z} P(Z|X,Y) = 1">

As a result, in the head-head case we have marginal independence between X and Y, that is <img src="https://render.githubusercontent.com/render/math?math=X \perp Y">

**back to probabilistic flows**

A path between two vertices is blocked with respect to a subset of vertices C if it passes through a vertex v, such that either:

* the edges are head-tail or tail-tail, and 
<img src="https://render.githubusercontent.com/render/math?math=v \in C">, or

* the edges are head-head, and 
<img src="https://render.githubusercontent.com/render/math?math=v \not \in C">, and neither are any of its descendants.

When a trail is not blocked, it is an active trail, as per the definition above.

### d-separation 

X and Y are d-separated in G given Z if there is no active trail in G between X and Y given Z, notation 
<img src="https://render.githubusercontent.com/render/math?math=d-sep_{G}(X,Y|Z)">. 



 
