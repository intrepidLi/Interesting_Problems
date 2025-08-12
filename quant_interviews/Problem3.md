You flip a coin 11 times.

Given that you get 4 heads and 7 tails, what is the probability that you see the pattern "THTH" at least once?

**Solution:**

The whole space is $C_{11}^{4} = 330$.

对 $i = 1, \ldots 8$, 令 $A_i$ = "模式THTH出现在位置 $i$"(序列第 $i$ 到第 $i+3$ 位是 THTH)

最后一个可以开始的位置：$i+3=11 \rightarrow i=8$

计算 

$$
P(\cup_{i=1}^{8} A_i) = \left\vert \cup_{i=1}^{8} A_i \right\vert / 330 \tag{1}
$$

使用容斥原理：

$$
\begin{aligned}
\left\vert \cup_{i=1}^{8} A_i \right\vert &= \sum_{i=1}^{8} \left\vert A_i \right\vert - \sum_{1 \leq i < j \leq 8} \left\vert A_i \cap A_j \right\vert + \sum_{1 \leq i < j < k \leq 8} \left\vert A_i \cap A_j \cap A_k \right\vert - \cdots \\
\end{aligned}
$$

1. 单事件数目：

固定 $i$, 第 $i$ 到 $i+3$位为 THTH，剩余7位放剩下的2H, 5T:

$$
\left\vert A_i \right\vert = C_{7}^{2} = 21
$$

$$
\sum_{i=1}^{8} \left\vert A_i \right\vert = 8 \times 21 = 168
$$

2. 两事件交的数目：

对 $i < j$分两类：

a) 不重叠：$j - i \ge 4$: 两段共占8位，正好用掉 4H, 4T: 剩余3位全放T：设两个THTH序列分别为B，问题转化为2个B，3个T的序列中B的放法有多少，这种情况下：

$$
\sum_{i + 4 \le j} \left\vert A_i \cap A_j \right\vert = C_{5}^{2} = 10
$$

这种情况也可以枚举：$j-i=4,5,6,7$, 分别对应 $4,3,2,1$ 个放法，总共也是10种情况。

b) 重叠：$j - i < 4$: 实际只有 $j-i=2$的时候，重叠会得到THTHTH，用掉3H,3T，剩5个地方放1H和4T：将THTHTH看成B，问题变成1个B，1个H，4个T序列的放法：

$$
\sum_{i + 4 > j} \left\vert A_i \cap A_j \right\vert = C_{6}^{1}C_{5}^{1} = 30
$$

所以总共的数目是 $10 + 30=40$

3. 三事件交的数目：

实际只有 THTHTHTH序列，在 $i, j=i+2, k=i+4$ 的情况下会出现这种情况，剩余三个T，总共情况如上方法：

$$
\sum_{1 \leq i < j < k \leq 8} \left\vert A_i \cap A_j \cap A_k \right\vert = C_4^{1} = 4
$$

4. 更高阶事件交的数量均需要 $\ge 8$H，冲突，所以都是0

最终代入 $(1)$得

$$
P(\cup_{i=1}^{8} A_i) = \frac{168 - 40 + 4}{330} = \frac{132}{330} = \frac{12}{30} = \frac{2}{5}
$$
