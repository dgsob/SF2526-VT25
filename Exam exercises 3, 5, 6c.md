## Exercises 3, 5, 6c from the exam 250310

### Exercise 3

![After computing...](image.png)

#### Step 1: Determining the number of clusters
The multiplicity of $\lambda = 0$ tells us how many connected components the graph has.    
Here $\lambda_1 = 0.000$ and the $\lambda_2$ and $\lambda_3$ are relatively close to $0$. This means we have $3$ weakly connected groups of nodes that could be separated into $3$ clusters (nodes are more likely to be connected if they are close to each other). 

We can also confirm that, seeing the subsequent growing eigenvalues - attempting to split the graph into more clusters would force partitioning among more and more strongly interconnected nodes. 

#### Step 2: Clustering
The first eigenvector $x_1$ is constant indicating the graph is connected. The vectors $x_2$ and $x_3$ however, these capture structural information that can be used to embed nodes into a 2D space. Representing each point as $(x_2(i), x_3(i))$ where $i$ is the node index, one could then apply k-means with $k=3$ to assign each node to a corresponding cluster.

Since the proximity of the respective coordinates can be easily assessed visually in our case, we can conclude that the appropiate clusters are:
- Cluster 1: $i = \{1, 4, 9, 10\}$
- Cluster 2: $i = \{2,3,6,8\}$
- Cluster 3: $i = \{5,7,11,12\}$

### Exercise 5a

![alt text](image-1.png)

#### Step 1: Define the matrix $A$
$A$ should be a $n \times n$ circulant matrix, specifically:
$$
A = \begin{bmatrix}  
S(x_0)\Delta x & S(x_{1})\Delta x & \cdots & S(x_{n-1})\Delta x \\  
S(x_{n-1})\Delta x & S(x_0)\Delta x & \cdots & S(x_{n-2})\Delta x \\  
\vdots & \vdots & \ddots & \vdots \\  
S(x_{1})\Delta x & S(x_{2})\Delta x & \cdots & S(x_0)\Delta x  
\end{bmatrix},
$$

where:     
$A_{j,m} = S\left(x_{(m - j) \mod n}\right) \Delta x$ for $j, m = \{0, 1, \dots, n-1\}$ and $m = (j+k)$.

The $x_{(m - j) \mod n}$ ensures periodicity by wrapping the index $k = (m−j)$ around the grid boundaries. Here, it always returns $k$ if $k \geq 0$ and $k+n$ otherwise.

#### Step 2: Explain what is in the vectors $\boldsymbol{u}$ and $\boldsymbol{v}$
- $\boldsymbol{u}$: contains discrete samples of the original 1-periodic function $u(x)$ taken at the grid points:
$$
\boldsymbol{u} = [u_0, u_1, \dots, u_{n-1}]^T, \quad u_j \approx u(x_j),  
$$
- $\boldsymbol{v}$: stores local averages of $u$ around each point $x_j$ (each computed with the expression for $v_j$ given in the task):
$$
\boldsymbol{v} = [v_0, v_1, \dots, v_{n-1}]^T, \quad v_j \approx v(x_j).  
$$

#### Step 3: Show that $v$-sequence can be computed with $\boldsymbol{v} = A\boldsymbol{u}$
$$
\begin{bmatrix}  
S(x_0)\Delta x & S(x_{1})\Delta x & \cdots & S(x_{n-1})\Delta x \\  
S(x_{n-1})\Delta x & S(x_0)\Delta x & \cdots & S(x_{n-2})\Delta x \\  
\vdots & \vdots & \ddots & \vdots \\  
S(x_{1})\Delta x & S(x_{2})\Delta x & \cdots & S(x_0)\Delta x  
\end{bmatrix}  
\begin{bmatrix} u_0 \\ u_1 \\ \vdots \\ u_{n-1} \end{bmatrix}
=
\begin{bmatrix}  
\sum_{m=0}^{n-1} S(x_{(m - 0) \mod n})\Delta x \cdot u_m \\  
\sum_{m=0}^{n-1} S(x_{(m - 1) \mod n})\Delta x \cdot u_m \\  
\vdots \\  
\sum_{m=0}^{n-1} S(x_{(m - (n-1)) \mod n})\Delta x \cdot u_m  
\end{bmatrix} 
$$

Thus, 
$$
v_j = \sum_{m=0}^{n-1} S(x_{(m - j) \mod n})\Delta x \cdot u_m
$$
This can be re-written as:
$$
v_j = \sum_{k=-j}^{n-1-j} S(x_{k \mod n})\Delta x \cdot u_{j+k}
$$
Since by the problem definition $S$ is non-negative and satisfies $S(-\frac{1}{2}) = S(\frac{1}{2}) = 0$ we can restrict the summation to:
$$
v_j = \sum_{k=-n/2}^{n/2-1} S(x_{k \mod n})\Delta x \cdot u_{j+k}
$$
The $x_k$ can be made implicitely n-periodic at this point just like $u_{j+k}$ has been the whole time:
$$
v_j = \sum_{k=-n/2}^{n/2-1} S(x_k)\Delta x \cdot u_{j+k}
$$
Which gives exactly the expression from the problem formulation.
### Exercise 6c

![alt text](image-2.png)

