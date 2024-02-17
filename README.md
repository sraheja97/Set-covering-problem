# Set-covering-problem
Set covering integer linear program using pyomo
Let the set of nodes be N, indexed as Ni = i in : i = 1,2, ...,n. The objective of monitoring all road links implies covering one end point of every edge of the graph thus yielding a vertex cover problem.
Introducing a decision variable xn for selecting each node, such that xn = 1 if selected, xn = 0 otherwise. 
The ILP program formulating this minimum node cover is written as:
            min Σcn*xn, n∈N
subject to xn + xv ≥ 1 ∀e = (n,v) ∈ E, xn ∈ {0,1} ∀N
The edges can be defined with the help of a matrix A with elements anv, also called the adjacency matrix:
        anv =   1 if node n is connected to node v (n ̸= v)
            =   0 otherwise
Using these matrix elements, the constraint can be written as:
            xn + xv ≥ anv (n,v) ∈ E

Minimum Uncovered Links:
The objective here is to obtain an ILP to minimize the number of uncovered road links while using at most 2 stations. This is equivalent to maximising the number of road links that can be covered. Let the decision variable representing the selection of edge (n,v) be Ynv. Then, the objective can be written as:
                        Max ∑_(n,v)▒Ynv/2
            Constraints:
                        Ynv ≤ Xn + Xv
                        Ynv ≥ Xn
                        Ynv ≥ Xv
            Subject to:
                        ∑_(n∈N)▒xn ≤ 2
                        xn ∈ {0,1} ⩝ n ∊ N
