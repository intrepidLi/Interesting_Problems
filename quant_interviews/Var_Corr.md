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

