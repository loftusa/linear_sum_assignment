# linear_sum_assignment
Custom code to solve the linear sum assignment problem in the context of soldiers and countries.
I got interested in this problem on the car ride back from a skiing trip while I was reading about all the ukraine stuff

anyway, the problem (formally) is as follows:

You have two sets A and T of not necessarily equal size, together with a weight function $C: A \times T \rightarrow R$. 

Now, Find a bijection $f: A \rightarrow T$ 
such that the cost function $\sum_{a \in A} C(a, f(a))$ is minimized.

The way I'll be doing this will be to view this in terms of a bipartite graph. $A$ and $T$ make up the disjoint nodes of the two parts; the weight function $C$ defines the edges and weights between the nodes in $A$ and the nodes in $T$. Remember that in a bipartite graph, edges only exist between parts, not within parts.

Gonna try to implement the Hungarian algorithm to solve it
