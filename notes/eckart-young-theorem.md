# Eckart-Young Theorem

## Theory

The Eckart-Young theorem characterizes the best low-rank approximation of a matrix using the Singular Value Decomposition (SVD).

Let $A \in \mathbb{R}^{n \times m}$ be a matrix with singular value decomposition:

$$A = U\Sigma V^T$$

where:
- $U \in \mathbb{R}^{n \times n}$ is an orthogonal matrix
- $\Sigma = \text{diag}(\sigma_1, \ldots, \sigma_p) \in \mathbb{R}^{n \times m}$ is a rectangular diagonal matrix
- $V \in \mathbb{R}^{m \times m}$ is an orthogonal matrix
- $p = \min(n, m)$
- $\sigma_1 \geq \sigma_2 \geq \ldots \geq \sigma_p \geq 0$ are the singular values in non-increasing order

## Best Low-Rank Approximation

The Eckart-Young theorem states that the best rank-$k$ approximation to matrix $A$ is given by:

$$X = \sum_{i=1}^{k} u_i v_i^T \sigma_i$$

with column-vectors $u_i$ and $v_i$ in $U = [u_1, \ldots, u_p]$ and $V = [v_1, \ldots, v_p]$, and singular 
values $\sigma_i$ in $\Sigma = diag(\sigma_1, \ldots, \sigma_p)$.

Equivalently, if we partition the SVD as:

$$U = [U_1, U_2], \quad \Sigma_1 = \text{diag}(\sigma_1, \ldots, \sigma_k), \quad V = [V_1, V_2]$$

where $U_1$ contains the first $k$ columns of $U$ and $V_1$ contains the first $k$ columns of $V$, then:

$$X = U_1 \Sigma_1 V_1^T$$

## Optimality

This approximation is optimal in the sense that the minimizer:

$$\min_{X \in \mathbb{R}^{n \times m}, \text{rank}(X)=k} \|A - X\|$$

is given by $X = \sum_{i=1}^{k} u_i v_i^T \sigma_i$

## Error Bound

Moreover, the approximation error is given by:

$$\|A - X\| = \sigma_{k+1}$$


## Applications

The Eckart-Young theorem provides the theoretical foundation for many dimensionality reduction techniques and data compression methods:

1. It justifies the use of SVD for low-rank approximations in areas like image compression and noise reduction
2. It forms the basis for PCA
3. It allows for optimal data representation in a lower-dimensional space
