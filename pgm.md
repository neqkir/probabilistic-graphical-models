### probabilistic graphical models 

[Concepts and definitions, more explanation, following the curriculum of the Coursera Standford online course
https://www.coursera.org/learn/probabilistic-graphical-models] 

Types of models

* Markov models (undirected graphs)

* Bayesian models (directed graphs) 

Examples

> Image segmentation: RV are labels for pixels, edges represent relationships between labels (this is a Bayesian network)

> Medical diagnosis through diagnostic questions

> Text information retrieval, retrieving for instance information about persons, locations and organization in a text, one variable for each word, which encodes the label for that word (person, location, organization), this is called named entity recognition

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
we get a value. 

An unnormalize measure is a factor also, e.g., 
<img src="https://render.githubusercontent.com/render/math?math=P(X_{1},X_{2},X_{3})"> 
which scope is 
<img src="https://render.githubusercontent.com/render/math?math={X_{1},X_{2}}">.

A conditional probability distribution is a factor, e.g., <img src="https://render.githubusercontent.com/render/math?math=P(X_{1}|X_{2},X_{3})"> 
meaning that for every combination of values for 
<img src="https://render.githubusercontent.com/render/math?math=X_{2}">.
and
<img src="https://render.githubusercontent.com/render/math?math=X_{3}">
we have a probability distribution over 
<img src="https://render.githubusercontent.com/render/math?math=X_{1}">.  

Factor operations include

> Factor products, multiplying values for the different factors, the scope is the union of the multiplied scopes

> Factor marginalization, marginalizing out part of the scope by summing values over those marginalized dimensions, and reducing the scope accordingly
	
> Factor reduction, fixing the value taken by a subset of the RVs, and reducing the scope accordingly

A Bayesian Network is a Directed Acyclic Graph (DAG) whose nodes represent the RVs 
<img src="https://render.githubusercontent.com/render/math?math=X_{1},X_{2},...,X_{n}">. 

For each node <img src="https://render.githubusercontent.com/render/math?math=X_{i}"> 
is defined a conditional probability distribution on its parents <img src="https://render.githubusercontent.com/render/math?math=P(X_{i}|Par_{G}(X_{i}))">. 

The Bayesian Network represents a joint distribution via the chain rule for Bayesian Networks 
<img src="https://render.githubusercontent.com/render/math?math=P(X_{1},...,X_{n})= \prod P(X_{i}|Par_{G}(X_{i}))">. 

We say that the probability distribution factorizes over G. 

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
<img src="https://render.githubusercontent.com/render/math?math=v \notin C">, and neither are any of its descendants.

When a trail is not blocked, it is an active trail, as per the definition above.

### d-separation 

X and Y are d-separated in G given Z if there is no active trail in G between X and Y given Z, notation 
<img src="https://render.githubusercontent.com/render/math?math=d-sep_{G}(X,Y|Z)">. 

An example

<img src="https://user-images.githubusercontent.com/89974426/151166687-19e3e7ec-a986-40e0-a460-40b43e2cf249.PNG" width=13% height=13%>

B is observed. A and D are d-separated because A-D is a head-tail with observed B. A and E are not because there is a trail between them, through C, which is head-head with C unobserved.

### Independence of Bayesian Networks

Theorem 

If P factorizes over G, and <img src="https://render.githubusercontent.com/render/math?math=d-sep_{G}(X,Y|Z)"> then P satisfies <img src="https://render.githubusercontent.com/render/math?math=X \perp Y|Z">

Property 

Any node is d-separated from its non-descendant given its parents.

So that, if P factorizes over G, then in P, any variable is independent of its non-descendants given its parents.

**I-maps**

In the previous paragraph, we saw that d-separation in G implies the corresponding independence statement. <img src="https://render.githubusercontent.com/render/math?math=I(G)"> is the set of independencies which derives from the d-separation statement, which writes, <img src="https://render.githubusercontent.com/render/math?math=I(G)=\{X \perp Y | Z : d-sep_{G}(X,Y|Z)\}">

Definition

If P satisfies <img src="https://render.githubusercontent.com/render/math?math=I(G)">, we say that G is an I-map (indenpendency map) of P.

**back to our first theorem**

We deduce from the above that, if P factorizes over G, then G is an I-map for P. In fact we also have reciprocally, if G is an I-map for P, then P factorizes over G.

Let's visualize the reciprocal and hint at its demonstration.

<img src="https://user-images.githubusercontent.com/89974426/151169598-ac94fcbe-3bc2-4640-af35-977247989b35.PNG" width=13% height=13%>

Using the chain rule of probabilities (not the Bayes rule since we don't know yet whether this is a Bayesian Network) we can write

<img src="https://render.githubusercontent.com/render/math?math=P(D,I,G,S,L)=P(D)*P(I|D)*P(G|D,I)*P(S|D,I,G)*P(L|D,I,G,S)">.

As a reminder, this is because <img src="https://render.githubusercontent.com/render/math?math=P(D)*P(I|D)=P(D,I)"> etc.

Here we have <img src="https://render.githubusercontent.com/render/math?math=P(I|D)=P(I)"> since <img src="https://render.githubusercontent.com/render/math?math=D \perp I">. Then <img src="https://render.githubusercontent.com/render/math?math=P(S|D,I,G)"> is the probability of S conditioned by its parent I and two non-descendants and <img src="https://render.githubusercontent.com/render/math?math=P(S|D,I,G)=P(S|I)">. Same for the last factor and we obtain
 
<img src="https://render.githubusercontent.com/render/math?math=P(D,I,G,S,L)=P(D)*P(I)*P(G|D,I)*P(S|I)*P(L|G)">

which shows the factorization over G. 

### Naive Bayes

A unobserved class and observed features <img src="https://render.githubusercontent.com/render/math?math=X_{i}"> : the naive bayesian independence assumption says that every pair of features is conditionally independent given the class, or <img src="https://render.githubusercontent.com/render/math?math=X_{i} \perp X_{j} | C"> <img src="https://render.githubusercontent.com/render/math?math=\forall X_{i}, X_{j}">, so that the Naive Bayes model comes down to the pairwise interaction between the class variable and the individual features. In other terms we have

<img src="https://render.githubusercontent.com/render/math?math=P(C,X_{1},...,X_{n})=P(C) \prod P(X_{i}|C))">

where <img src="https://render.githubusercontent.com/render/math?math=P(C)"> is called the prior probability of C.

#### Naive Bayes classifier

If we look at the ratio of the probabilities of two different classes given the same features observations 

<img src="https://render.githubusercontent.com/render/math?math=\frac{P(C=c_{1}|x_{1},...,x_{n})}{P(C=c_{2}|x_{1},...,x_{n})}=\frac{P(C=c_{1})}{P(C=c_{2})} \prod \frac{P(x_{i}|C=c_{1})}{P(x_{i}|C=c_{2})}">

where the first term is the ratio of the prior probabilities and the second is the product of the "odds ratios", i.e., the ratios of the probabilities of a given observation in the context of two classes.   

#### Application to medical diagnosis

The CPCS network is one of the largest available to the research community.

<img src="https://user-images.githubusercontent.com/89974426/151556934-c55a8030-5477-47eb-a147-1d5b1dab4df4.PNG" width=60% height=60%>

#### Template models

> An example, image segmentation: classsifying each superpixel. 

We don't want a separate model for each superpixel. All pixels share the same model relating the class of a pixel to its image features and all pairs of superpixels share the same edge model, relating adjacent superpixel. 

The structure and the parameters of models pertaining to different parts / variables of a bayesian network can be shared to take similarities into account. Those variables will share the same dependencies structure and the same conditional probability distribution. 

We introduce the notion of template variables, which are instanciated (duplicated) multiple times. In the above example, the superpixel labels are template variables. 

#### Temporal models 

Temporal models represent a distribution over time. Time is discretized given a certain time granularity. We consider a set of template random variables indexed by time, <img src="https://render.githubusercontent.com/render/math?math=X^{t}"> and we denote <img src="https://render.githubusercontent.com/render/math?math=X^{t:t'}=\{X^{t},...,X^{t'}\}"> a trajectory. We want to represent the probability distribution of a trajectory, <img src="https://render.githubusercontent.com/render/math?math=P(X^{t:t'})">, or in fact, an infinite family of probability distributions, since we can look at trajectories of duration 1, 2, ..., 1 million etc.

We start with the Markov Assumption

<img src="https://render.githubusercontent.com/render/math?math=P(X^{0:T})=P(X^{0}) \prod_{t=0}^{T-1} P(X^{t+1}|X^{0:t})">.





