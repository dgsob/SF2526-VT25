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

### Exercise 5

![alt text](image-1.png)

### Exercise 6c

![alt text](image-2.png)

