# linear_sum_assignment
Custom code to solve the linear sum assignment problem in the context of soldiers and countries.
I got interested in this problem on the car ride back from a skiing trip while I was reading about all the ukraine stuff. The problem I thought of was:

Suppose you're a country, and you want to station your soldiers in other countries.  
You have a particular number of soldiers that you want to send to each country. Specifically, you want to send $n_1$ soldiers to country 1, n_2 soldiers to country 2, up to n_m soldiers to country m. Your total number of soldiers, of course, is $\sum_{i=1}^m n_i$. You don't really care which soldiers go to which country as long as the total number is correct.

However, the soldiers themselves have preferences. Specifically, each of them gives a ranking P(\[1, 2, ..., m\]) where $P: R^m \rightarrow R^m$ is a permutation function on the vector [1, ..., m]. You would like each soldier to go to their top country if possible, and if that country is filled, to send the to their second-top country, and so on. Specifically, you would like to minimize the sum of the rankings across all soldiers, which means that they're as happy as possible with the country they got sent to.

Now, I did a bit of research and asked a couple friends, and it turns out that this is (unsurprisingly) a somewhat solved problem. It's called the linear sum assignment problem, which has its own wikipedia article. 

The problem (formally) is as follows:

You have two sets A and T of not necessarily equal size, together with a weight function $C: A \times T \rightarrow R$. 

Now, Find a bijection $f: A \rightarrow T$
such that the cost function $\sum_{a \in A} C(a, f(a))$ is minimized.

The way I'll be doing this will be to view this in terms of a bipartite graph. A and T make up the disjoint nodes of the two parts; the weight function C defines the edges and weights between the nodes in A and the nodes in T. Remember that in a bipartite graph, edges only exist between parts, not within parts.

You can view this as a graph theory problem. You'd start with a complete weighted bipartite graph with n + m nodes. The soldiers make up the first n nodes, and the countries make up the second m nodes. Each node i in \{n\} has an edge to each node j in \{m\} with weight E(i, j) corresponding to the ranking that soldier i gave to country j.

Now, find a subgraph such that each soldier node in n gets mapped to exactly one country node in m (but not the reverse, meaning multiple nodes in n can get mapped to a single node in m). Specifically, you want to find the subgraph that minimizes the sum of the edge weights. 

Apparently you can solve this (somehow) with the Hungarian algorithm...
