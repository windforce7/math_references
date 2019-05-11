#   1 Bernoulli experiment & distribution [discrete]
<details>
<summary>
What is a Bernoulli experiment and how does it generate a distribution?
</summary>
A Bernoulli experiment is a random experiment satisfying:

1.  Outcome of the experiment can be divided into two exclusive and exhaustive types, say A and B (or success and failure if you wish). We have:
    1.  $A \cap B = \phi$
    2.  $A \cup B = S, S$ for the sample space
2.  Let $p$ be the probability that a type A outcome is get in a Bernoulli experiment and then the probability of getting type B is $1 - p$. We normally denote $1 - p$ as $q$.
3.  The experiment could be conducted for any number of times independently without changing $p$.
</details>

##  1.1 Definition of Bernoulli R.V.
In a single Bernoulli experiment, let X be **the number of type A result**. X can be 1 or 0.
$$
\begin{cases}
X(A) = 1\\
X(B) = 0
\end{cases}
$$
##  1.2 pmf of Bernoulli R.V.
$$
\begin{cases}
p(1) = p\\
p(0) = 1 - p\\
p(x) = 0, otherwise
\end{cases}
$$
Or in other way: $p(x)=p^x(1-p)^{1-x}$.
##  1.3 Support set of Bernoulli R.V.
$$
D = \{0, 1\}
$$
##  1.4 Moment of Bernoulli distribution
$$
M(t) = [(1 - p) + pe ^ t] = [q + pe ^ t]\\
\mu = p\\
\sigma^2 = p(1-p) = pq
$$

#   2 Binomial distribution [discrete]
Binomial distribution is based on n independent Bernoulli experiments.

##  2.1 Difinition of Binomial R.V.
Do Bernoulli experiment $n \geq 1$ time(s) and let X denote the **total number of type A results**. This can be also written as $X \sim b(n, p)$.

##  2.2 pmf of Binomail R.V.
$$
p(x) = \begin{cases}
P\{X=x\} = 
{n \choose x} p ^ x (1 - p) ^ {n - x} = {n \choose x} p ^ x q ^ {n - x}, x = 0, 1, ... ,n\\
0, otherwise
\end{cases}
$$

##  2.3 Support set of Binomial R.V.
$$
D = \{0, 1, 2, ... , n\}
$$

##  2.4 Moment of Binomial distribution
$$
M(t) = \sum _ {x = 0} ^ {n} e ^ {tx} {n \choose x} p ^ x q ^ {n - x} = 
\sum _ {x = 0} ^ {n} (pe ^ t) q ^ {n - x} = [q + pe ^ t] ^ n\\
\mu = M'(t) = np\\
\sigma ^ 2 = M''(0) - \mu ^ 2 = np(1 - p) = npq
$$

##  2.5 R reference
See [The Binomial Distribution](https://stat.ethz.ch/R-manual/R-devel/library/stats/html/Binomial.html).

#   3 Negative binomial distribution [discrete]
Negative binomial distribution is also derived from a series of independent Bernoulli experiments.

##  3.1 Difinition of negative binomial R.V.
For an arbitary positive integer $r$, do a series of Bernoulli experiments for $n \geq 1$ time(s) independently and let Y denote the **total number of failures (B) right before observing the $r$th successful (A) result**.
Naturally it makes no sense when $n < r$.

##  3.2 pmf of negative binomial R.V.
The event described in 3.1 can be taken as a 2-step composite event:
1.  There are $r - 1$ successful (A) results in first $Y + r - 1$ experiments
2.  In the $Y + r - 1$th experiment, a successful (A) result is observed

Therefore the pmf:
$$
p_y(y) = \begin{cases}
{y + r - 1 \choose r - 1} p ^ {r - 1} (1 - p) ^ y \times p 
= {y + r - 1 \choose r - 1} p ^ r q ^ y, y = 0, 1, ...\\
0, otherwise
\end{cases}
$$

##  3.3 Support set of negative binomial R.V.
$$
y \in D = N = \{0, 1, 2, ...\}
$$

##  3.4 Moment of negative binomial distribution
$$
M(t) = p ^ r[1 - (1 - p)e ^ t] ^ {-r} = p ^ r[1 - qe ^ t] ^ {-r}\\
\mu = \frac{rp}{1 - p} = \frac{rp}{q}\\
\sigma ^ 2 = \frac{r(1 - p)}{p ^ 2} = \frac{rq}{p ^ 2}
$$

##  3.5 R reference
See [The Negative Binomial Distribution](https://stat.ethz.ch/R-manual/R-devel/library/stats/html/NegBinomial.html).

#   4 Geometric distribution [discrete]
Geometric distribution is a special case of [negative binomial distribution](#3-negative-binomial-distribution-discrete) when $r = 1$.

##  4.1 Difinition of geometric R.V.
Let X denote the **total number of failures (B) right before observing the first successful (A) result** in a series of identically independent Bernoulli experiment.

##  4.2 pmf of geometric R.V.
$$
p_y(y) = \begin{cases}
(1 - p) ^ y p = pq ^ y, y = 0, 1, ...\\
0, otherwise
\end{cases}
$$

##  4.3 Support set of geometric R.V.
Identical to [negative binomial distribution](#33-support-set-of-negative-binomial-distribution).

##  4.4 Moment of geometric distribution
$$
M(t) = p[1 - (1 - p)e ^ t] ^ {-1} = p[1 - qe ^ t] ^ {-1}\\
\mu = \frac{p}{1 - p} = \frac{p}{q}\\
\sigma ^ 2 = \frac{1 - p}{p ^ 2} = \frac{q}{p ^ 2}
$$

##  4.5 R reference
See [The Geometric Distribution](https://stat.ethz.ch/R-manual/R-devel/library/stats/html/Geometric.html).

#   5 Multinomial distribution [discrete]
Multinomial distribution is an extension of binomial distribution. In each experiment there are $k$ exclusive and exhaustive outcomes instead of 2, say $C_1, C_2, ..., C_k$. Getting an outcome of $C_i$ has probability $p_i$ and clearly $\sum _ {i = 1} ^ k p_i = 1$. 

$n \geq 1$  independent repeat experiments are conducted in a row.

##  5.1 Difinition of multinomial R.V.
Let vector ${\bold X} = \{x_1, x_2, ... , x_k\}$ denote the outcome that in $n$ independent repeat experiments, outcome $C_i$ is observed $x_i$ times. Therefore:
1.  $\sum _ {i = 0} ^ k x_i = n$
2.  $x_i \geq 0 for i = 1, 2, ... ,k$

Multinomial R.V. is multivariate with $k$ dimensions. With fixed $n$, it can also be of $k - 1$ dimensions since $x_i = n - \sum _ {j \ne i} ^ k x_j$.

##  5.2 pmf of multinomial R.V.
$$
p(x_1, x_2, ..., x_k) = {n \choose x_1}{n - x_1 \choose x_2}...{n - x_1 - ... - x_{k - 2} \choose x_{k - 1}}p_1 ^ {x_1}p_2 ^ {x_2}...p_k ^ {x_k}\\
=\frac{n!}{x_1!x_2!...x_k!}p_1 ^ {x_1}p_2 ^ {x_2}...p_k ^ {x_k}
$$

##  5.3 Support set of multinomial R.V.
$$
x_i \in \{0, 1, 2, ..., n\}, i = 1, 2,...,k
$$

##  5.4 Moment of multinomial distribution
$$
M({\bold t}) = (\sum _ {i = 1} ^ k p_i e ^ {t_i}) ^ n\\
\mu_i = np_i\\
\sigma_i ^ 2 = np_i(1 - p_i) = np_i q_i\\
Cov(x_i, x_j) = -np_i p_j
$$

##  5.5 R reference
See [The Multinomial Distribution](https://stat.ethz.ch/R-manual/R-devel/library/stats/html/Multinom.html).

#   6 Hypergeometric distribution [discrete]
Hypergeometric distribution is commonly used in survey sampling. There are $D$ defect ones among a batch of $N \geq D$ products and a group of sample sized $n \leq D$ is picked from these products. Every time a product is picked from the batch, each product in the batch is equally likely to be picked, and the picked one is not returned to the batch(without replacement).

Each time a product is picked, the outcome whether it's defect is Bernoulli. If a product is returned when it's picked, the repeat experiment picking many times become Binomial.

##  6.1 Difinition of hypergeometric R.V.
Let $X$ denote the number of defect products when the sample size is $n$.

##  6.2 pmf of hypergeometric R.V.
$$
p(x) = \frac{{N - D \choose n - x}{D \choose x}}{N \choose n}, x = 0, 1, ... ,n
$$

##  6.3 Support set of hypergeometric R.V.
$$
x \in \{0, 1, ..., n\}\\
n \leq min\{N, D\}
$$

##  6.4 Moment of hypergeometric distribution
$$
\mu = n\frac{D}{N}\\
\sigma ^ 2 = n \frac{D}{N}\frac{N - D}{N}\frac{N - n}{N - 1}
$$

##  6.5 R reference
See [Hypergeometric distribution](https://stat.ethz.ch/R-manual/R-devel/library/stats/html/Hypergeometric.html).

#   7 Poisson Distribution [discrete]
<details>
<summary>
The Poisson Distribution is widely used in stochastic process. It describes the number of times that a random event happens within a period of time (a subarea) on a continuous timeline (space). The Poisson Assumption strictly defines the case.
</summary>

The event happens on any spot within a continuous interval of space (1 dimeension) or time randomly. Let $g(x, w)$ denote the probability that $x$ events happen within an interval with length $w$. 3 assumptions are given:
1.  $g(1, h) = \lambda h + o(h), h \gt 0, \lambda \gt 0$
2.  $\sum_{x = 2} ^ \infty = o(h)$
3.  On non-overlapping intervals, $x_i$ are independent
</details>

##  7.1 Difinition of Poisson R.V.
Let $X$ denote the **total number of happening events within the interval of length $w$**.

##  7.2 pmf of Poisson R.V.
$$
g(x, w) = \frac{(\lambda w) ^ x e ^ {-\lambda w}}{x!}, x = 0, 1, ...
$$

Let $m = \lambda w$ and the pmf can be rewritten as:
$$
p(x) = \begin{cases}
\frac{m ^ x e ^ {-m}}{x!}, x = 0, 1, 2,...\\
0, otherwise
\end{cases}
$$

##  7.3 Support set of Poisson R.V.
$$
x \in \{0, 1, 2, ...\} = N
$$

##  7.4 Moment of Poisson distribution
$$
M(t) = \sum_x e^{tx}\frac{m ^ x e ^ {-m}}{x!} = e ^ {m(e ^ t - 1)}\\
\mu = m\\
\sigma ^2 = m
$$

##  7.5 R reference
See [The Poisson Distribution](https://stat.ethz.ch/R-manual/R-devel/library/stats/html/Poisson.html).

#   8 $\Gamma$ Distribution

#   9 $\chi ^ 2$ Distribution

#   10 $\beta$ Distribution