$N$ random variables, the correlation coefficient between every two variables is the same, What is the whole range of correlation efficient?

**Solution:**

There are $N$ random variables $X_1, X_2, \ldots , X_{N}$. Assume the correlation coefficient between every two variables equals $\rho$. The correlation matrix looks like:

$$
\Sigma = \begin{bmatrix} 
    1 & \rho & \rho & \cdots & \rho \\
    \rho & 1 & \rho & \cdots & \rho \\
    \vdots & \vdots & \ddots & \vdots & \vdots \\
    \rho & \rho & \rho & \cdots & 1 \\
\end{bmatrix} 
$$

$\Sigma$ as a correlation matrix needs to be semi-positive:

$$
\det(\Sigma) \ge 0
$$


**The First way:(硬推)**

$$
\begin{aligned}
 \det (\Sigma) &= \det \begin{bmatrix} 
    1 & \rho & \rho & \cdots & \rho \\
    \rho & 1 & \rho & \cdots & \rho \\
    \vdots & \vdots & \ddots & \vdots & \vdots \\
    \rho & \rho & \rho & \cdots & 1 \\
\end{bmatrix}_{N}  = \begin{bmatrix} 
    1- \rho & 0 & 0 & \cdots & \rho - 1 \\
    0 & 1- \rho & 0 & \cdots & \rho - 1 \\
    \vdots & \vdots & \ddots & \vdots & \vdots \\
    \rho & \rho & \rho & \cdots & 1 \\ 
\end{bmatrix}_{N} \quad \text{(add -last col to 1} \rightarrow \text{N-1 col)} \\
&= \begin{bmatrix} 
    1- \rho & 0 & 0 & \cdots & \rho -1 \\
    0 & 1- \rho & 0 & \cdots & \rho - 1 \\
    \vdots & \vdots & \ddots & \vdots & \vdots \\
    0 & \rho & \rho & \cdots & \rho + 1 \\
\end{bmatrix}_{N} \quad \text{(add} -\frac{\rho}{1-\rho} \text{first col to the last col)} \\
&= (1- \rho) \cdot (-1)^{1+1} \cdot \begin{bmatrix} 
    1- \rho & 0 & 0 & \cdots & \rho -1 \\
    0 & 1- \rho & 0 & \cdots & \rho - 1 \\
    \vdots & \vdots & \ddots & \vdots & \vdots \\
    \rho & \rho & \rho & \cdots & \rho + 1 \\
\end{bmatrix}_{N-1} \quad \text{(flatten by the first col)}\\
&= (1 -\rho) \cdot \begin{bmatrix} 
    1- \rho & 0 & 0 & \cdots & \rho - 1 \\
    0 & 1- \rho & 0 & \cdots & \rho - 1 \\
    \vdots & \vdots & \ddots & \vdots & \vdots \\
    0 & \rho & \rho & \cdots & 2\rho + 1 \\
\end{bmatrix}_{N-1} \quad \text{(add} -\frac{\rho}{1-\rho} \text{first col to the last col)}\\
&= (1 - \rho) \cdot (1-\rho) \cdot (-1)^{1+1} \begin{bmatrix} 
    1- \rho & 0 & 0 & \cdots & \rho - 1 \\
    0 & 1- \rho & 0 & \cdots & \rho - 1 \\
    \vdots & \vdots & \ddots & \vdots & \vdots \\
    \rho & \rho & \rho & \cdots & 2 \rho + 1 \\
\end{bmatrix}_{N-2}  \quad \text{(flatten by the first col)}\\
&= \cdots \\
&= (1 - \rho)^{N-1} \cdot ((N-1) \rho + 1) \ge 0\\
\end{aligned}
$$

Because $\rho \le 1$

So, $(N-1)\rho + 1 \ge 0 \rightarrow \rho \ge -\frac{1}{N-1}$.

The final answer:

$$
-\frac{1}{N-1} \le \rho \le 1
$$


**The Second way:(特征值法)**
The matrix can be written as:

$$
\Sigma = (1 - \rho) I_{N} + \rho J_{N}
$$

where $I$ is the identity matrix and $J$ is the matrix of all ones.

For $J_{N}$:

$$
J_{N} = \boldsymbol{u}\boldsymbol{u}^{T}, \boldsymbol{u} = (1, 1, \ldots , 1)^{T}, \operatorname{rank}(J_{N}) = 1 \rightarrow \text{one non-zero eigenvalue}
$$

$$
\because \text{tr}(J_{N}) = N \implies \text{the only non-zero eigenvalue is } N
$$


And the multiplicity of eigenvalue $N$ is 1, the multiplicity of eigenvalue $0$ is $N-1$.

So, the whole eigenvalues for $\Sigma$ are:

$$
\lambda_1 = (1 - \rho) + N \rho, \text{multiplicity } 1
$$

$$
\lambda_2 = (1 - \rho) + 0 \cdot \rho = 1 - \rho, \text{multiplicity } N-1
$$

Because of semi-positive:

$$
\lambda_1 \ge 0 \implies (1 - \rho) + N \rho \ge 0 \rightarrow \rho \ge -\frac{1}{N-1}
$$

$$
\lambda_2 \ge 0 \implies 1 - \rho \ge 0 \rightarrow \rho \le 1
$$

The result is:

$$
-\frac{1}{N-1} \le \rho \le 1
$$
