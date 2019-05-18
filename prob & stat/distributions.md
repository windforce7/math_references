#   1 **The Bernoulli distribution** [discrete]
<details>
<summary>
The Bernoulli distribution is a statistic model for the Bernoulli experiment.
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
p(x) = 0 \text{, otherwise}
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

#   2 **The Binomial distribution** [discrete]
Binomial distribution is based on n independent Bernoulli experiments.

##  2.1 Definition of Binomial R.V.
Do Bernoulli experiment $n \geq 1$ time(s) and let X denote the **total number of type A results**. This can be also written as $X \sim b(n, p)$.

##  2.2 pmf of Binomail R.V.
$$
p(x) = \begin{cases}
P\{X=x\} = 
{n \choose x} p ^ x (1 - p) ^ {n - x} = {n \choose x} p ^ x q ^ {n - x}, x = 0, 1, ... ,n\\
0 \text{, otherwise}
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

#   3 **The Negative binomial distribution** [discrete]
Negative binomial distribution is also derived from a series of independent Bernoulli experiments.

##  3.1 Definition of negative binomial R.V.
For an arbitary positive integer $r$, do a series of Bernoulli experiments for $n \geq 1$ time(s) independently and let Y denote the **total number of failures (B) right before observing the $r$th successful (A) result**.
Naturally it makes no sense when $n \lt r$.

##  3.2 pmf of negative binomial R.V.
The event described in 3.1 can be taken as a 2-step composite event:
1.  There are $r - 1$ successful (A) results in first $Y + r - 1$ experiments
2.  In the $Y + r - 1$th experiment, a successful (A) result is observed

Therefore the pmf:
$$
p_y(y) = \begin{cases}
{y + r - 1 \choose r - 1} p ^ {r - 1} (1 - p) ^ y \times p 
= {y + r - 1 \choose r - 1} p ^ r q ^ y, y = 0, 1, ...\\
0 \text{, otherwise}
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

#   4 **The Geometric distribution** [discrete]
Geometric distribution is a special case of [negative binomial distribution](#3-negative-binomial-distribution-discrete) when $r = 1$.

##  4.1 Definition of geometric R.V.
Let X denote the **total number of failures (B) right before observing the first successful (A) result** in a series of identically independent Bernoulli experiment.

##  4.2 pmf of geometric R.V.
$$
p_y(y) = \begin{cases}
(1 - p) ^ y p = pq ^ y, y = 0, 1, ...\\
0 \text{, otherwise}
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

#   5 **The Multinomial distribution** [discrete]
Multinomial distribution is an extension of binomial distribution. In each experiment there are $k$ exclusive and exhaustive outcomes instead of 2, say $C_1, C_2, ..., C_k$. Getting an outcome of $C_i$ has probability $p_i$ and clearly $\sum _ {i = 1} ^ k p_i = 1$. 

$n \geq 1$  independent repeat experiments are conducted in a row.

##  5.1 Definition of multinomial R.V.
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

#   6 **The Hypergeometric distribution** [discrete]
Hypergeometric distribution is commonly used in survey sampling. There are $D$ defect ones among a batch of $N \geq D$ products and a group of sample sized $n \leq D$ is picked from these products. Every time a product is picked from the batch, each product in the batch is equally likely to be picked, and the picked one is not returned to the batch(without replacement).

Each time a product is picked, the outcome whether it's defect is Bernoulli. If a product is returned when it's picked, the repeat experiment picking many times become Binomial.

##  6.1 Definition of hypergeometric R.V.
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

#   7 **Poisson Distribution** [discrete]
<details>
<summary>
The Poisson Distribution is widely used in stochastic process. It describes the number of times that a random event happens within a period of time (a subarea) on a continuous timeline (space). The Poisson Assumption strictly defines the case.
</summary>

The event happens on any spot within a continuous interval of space (1 dimeension) or time randomly. Let $g(x, w)$ denote the probability that $x$ events happen within an interval with length $w$. 3 assumptions are given:
1.  $g(1, h) = \lambda h + o(h), h \gt 0, \lambda \gt 0$
2.  $\sum_{x = 2} ^ \infty = o(h)$
3.  On non-overlapping intervals, $x_i$ are independent
</details>

##  7.1 Definition of Poisson R.V.
Let $X$ denote the **total number of happening events within the interval of length $w$**.

##  7.2 pmf of Poisson R.V.
$$
g(x, w) = \frac{(\lambda w) ^ x e ^ {-\lambda w}}{x!}, x = 0, 1, ...
$$

Let $m = \lambda w$ and the pmf can be rewritten as:
$$
p(x) = \begin{cases}
\frac{m ^ x e ^ {-m}}{x!}, x = 0, 1, 2,...\\
0 \text{, otherwise}
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

#   8 **The $\Gamma$ Distribution** [continuous]
<details>
<summary>
The Gamma distribution is used in many cases such as the time until decease. It's necessary to understand the Gamma function before going deeper.
</summary>

For a **positive** real number $\alpha \gt 0$, define:
$$
\int_0^\infty y ^ {\alpha - 1} e ^ {-y} \text{d}y = \Gamma(\alpha)
$$

It has the following properties:
$$
\Gamma(\alpha) = (\alpha - 1)\Gamma(\alpha - 1)\\
\Gamma(1) = 1\\
\Gamma(\frac{1}{2}) = \sqrt{\pi}
\Gamma(\alpha) \gt 0 \text{, for any }\alpha \gt 0
$$
</details>

##  8.1 Definition of $\Gamma$ R.V.
A $\Gamma$ R.V. is a continuous random variable which follows the $\Gamma$ distribution. A $\Gamma$ R.V. is not defined the same way as a binomial R.V. by its meaning.

##  8.2 pdf of $\Gamma$ R.V.
$$
f(x) = \begin{cases}
\frac{1}{\Gamma(\alpha) \beta ^ \alpha} x ^ {\alpha - 1} e ^ {- \frac{x}{\beta}} \text{, } 0 \lt x \lt +\infty\\
0 \text{, otherwise}
\end{cases}\\
\alpha \gt 0, \beta \gt 0.
$$

It can also be written as: $X \sim \Gamma(\alpha, \beta)$. Notice that the form of pdf is slightly different from the original $\Gamma$ function for another parameter $\beta$ is introduced. To understand this, consider substitution $y = \frac{x}{\beta}, \beta \gt 0$.
$$
\Gamma(\alpha) = \int_0^\infty{(\frac{x}{\beta}) ^ {\alpha - 1} e ^ {-\frac{x}{\beta}} (\frac{1}{\beta})\text{d}x}
$$

##  8.3 Support set of $\Gamma$ R.V.
$$
x \in (0, +\infty)
$$

##  8.4 Moment of $\Gamma$ distribution
$$
M(t) = \frac{1}{(1 - \beta t) ^ \alpha} \text{, } t \lt \frac{1}{\beta}\\
\mu = \alpha\beta\\
\sigma ^ 2 = \alpha\beta ^ 2
$$

##  8.5 R reference
See [The Gamma Distribution](https://stat.ethz.ch/R-manual/R-devel/library/stats/html/GammaDist.html).

#   9 **The Exponential Distribution** [continuous]
The exponential distribution is a special case of $\Gamma$ distribution.

##  9.1 Definition of exponential R.V.
Same as [The $\Gamma$ R.V.](#81-definition-of-gamma-rv) with $\alpha = 1$ and $\beta = \frac{1}{\lambda} \gt 0$.

##  9.2 pdf of exponential R.V.
$$
g(x) = \begin{cases}
\lambda e ^ {-\lambda x} \text{, } 0 \lt x \lt +\infty\\
0 \text{, otherwise}
\end{cases}\\
\lambda \gt 0
$$

##  9.3 Support set of exponential R.V.
Same as [The $\Gamma$ R.V.](#83-support-set-of-gamma-rv).

##  9.4 Moment of exponential distribution
$$
M(t) = \frac{1}{1 - \frac{1}{\lambda}t} = \frac{\lambda}{\lambda - t} \text{, } t \lt \lambda\\
\mu = \frac{1}{\lambda}\\
\sigma ^ 2 = \frac{1}{\lambda ^ 2}
$$

##  9.5 R reference
See [The Exponential Distribution](https://stat.ethz.ch/R-manual/R-devel/library/stats/html/Exponential.html).

#   10 **The $\chi ^ 2$ Distribution** [continuous]
The $\chi ^ 2$ distribution is also a special case of $\Gamma$ distribution. It is also closely related to Normal distribution.

##  10.1 Definition of $\chi ^ 2$ R.V.
Same as [The $\Gamma$ R.V.](#81-definition-of-gamma-rv) with $\alpha = \frac{r}{2}$ and $\beta = 2$ where $r$ is a positive integer.

##  10.2 pdf of $\chi ^ 2$ R.V.
$$
f(x) = \begin{cases}
\frac{1}{\Gamma(r/2)2 ^ {r/2}} x ^ {\frac{r}{2} - 1} e ^ {- \frac{x}{2}} \text{, } 0 \lt x \lt +\infty\\
0 \text{, otherwise}
\end{cases}\\
r \in N ^ + = \{1, 2, 3, ...\}
$$

##  10.3 Support set of $\chi ^ 2$ R.V.
Same as [The $\Gamma$ R.V.](#83-support-set-of-gamma-rv).

##  10.4 Moment of $\chi ^ 2$ distribution
$$
M(t) = \frac{1}{(1 - 2t) ^ \frac{r}{2}} \text{, } t \lt \frac{1}{2}\\
\mu = r\\
\sigma ^ 2 = 2r
$$

##  10.5 R reference
See [The Chi-Squared Distribution](https://stat.ethz.ch/R-manual/R-devel/library/stats/html/Chisquare.html).

#   11 **The Beta Distribution** [continuous]
<details>
<summary>
Beta distribution can be derived from two independent Gamma random variables.
</summary>

Suppose two independent random variables $X_1 \sim \Gamma(\alpha), X_2 \sim \Gamma(\beta)$. Joint pdf is:
$$
f_{1,2}(x_1, x_2) = \frac{1}{\Gamma(\alpha)\Gamma(\beta)} x_1 ^ {\alpha - 1} x_2 ^ {\beta - 1} e ^ {- x_1 - x_2} \text{, } 0 \lt x_1 \lt +\infty, 0 \lt x_2 \lt +\infty\\
\alpha \gt 0, \beta \gt 0
$$

Consider the substituion, which is a bijection from $(0, \infty) \times (0, \infty) \to (0, \infty) \times (0, 1)$:
$$
\begin{cases}
Y_1 = X_1 + X_2\\
Y_2 = \frac{X_1}{X_1 + X_2}
\end{cases}
$$

They have joint pdf and marginal pdf:
$$
g_{1,2} =\\
\begin{cases}
\frac{y_2 ^ {\alpha - 1}(1 - y_2) ^ {\beta - 1} y_1 ^ {\alpha + \beta - 1} e ^ {- y_1}}{\Gamma(\alpha)\Gamma(\beta)} \text{, } 0 \lt y_1 \lt +\infty, 0 \lt y_2 \lt 1\\
0 \text{, otherwise}
\end{cases}\\
g_1(y_1) =\\
\begin{cases}
\frac{y_1 ^ {\alpha + \beta - 1} e ^ {- y_1}}{\Gamma(\alpha + \beta)} \text{, } 0 \lt y_1 \lt +\infty\\
0 \text{, otherwise}
\end{cases}\\
g_2(y_2) =\\
\begin{cases}
\frac{\Gamma(\alpha + \beta)}{\Gamma(\alpha)\Gamma(\beta)} y_2 ^ {\alpha - 1} (1 - y_2) ^ {\beta - 1} \text{, } 0 \lt y_2 \lt 1\\
0 \text{, otherwise}
\end{cases}
$$

The following conclusions are drawn:
1.  $Y_1$ and $Y_2$ are independent
2.  $Y_1 \sim \Gamma(\alpha + \beta, 1)$

$Y_2$ follows a beta distribution with param $\alpha$ and $\beta$, which can be denote as $Y_2 \sim beta(\alpha, \beta)$.
</details>

##  11.1 Definition of beta R.V.
Aside from the connection with Gamma distribution, it's easier to take $\beta$ random variables as continuous R.V. which follows the $\beta$ distribution.

##  11.2 pdf of beta R.V.
$$
f(x) = \begin{cases}
\frac{\Gamma(\alpha + \beta)}{\Gamma(\alpha)\Gamma(\beta)} x ^ {\alpha - 1} (1 - x) ^ {\beta - 1} \text{, } 0 \lt x \lt 1\\
0 \text{, otherwise}
\end{cases}\\
\alpha \gt 0, \beta \gt 0
$$

##  11.3 Support set of beta R.V.
$$
x \in (0, 1)
$$

##  11.4 Moment of beta distribution
$$
M(t) = 1 = \sum_{i = 1}^\infty(\prod_{j = 0}^{i - 1}\frac{\alpha + j}{\alpha + \beta + j})\frac{t ^ i}{i!} \text{, } -\infty \lt t \lt +\infty\\
\mu = \frac{\alpha}{\alpha + \beta}\\
\sigma ^ 2 = \frac{\alpha\beta}{(\alpha + \beta + 1)(\alpha + \beta) ^ 2}
$$

##  11.5 R reference
See [The Beta Distribution](https://stat.ethz.ch/R-manual/R-devel/library/stats/html/Beta.html).

#   12 **The Normal Distribution** [continuous]
<details>
<summary>
The Normal distribution is the rockstar in Statistics. 

It is closely connected to the Central Limit Theorem and can be used as approximation of Binomial Distribution when param $n$ of $b(k, n, p)$ is huge. 
</summary>

Consider the integration:
$$
I = \int_{-\infty}^{+\infty} \frac{1}{\sqrt{2\pi}} \text{exp}(-\frac{x ^ 2}{2}) \text{d}x = \int_{-\infty}^{+\infty} \frac{1}{\sqrt{2\pi}} e ^ {-\frac{x ^ 2}{2}} \text{d}x
$$
It is non-negative and therefore:
$$
I = \sqrt{I ^ 2}\\
I ^ 2 = \frac{1}{2\pi} \int_{-\infty}^{+\infty} \int_{-\infty}^{+\infty} \text{exp}(-\frac{x ^ 2 + t ^ 2}{2}) \text{d}x\text{d}y\\
= \frac{1}{2\pi} \int_{0}^{2\pi} \int_{0}^{+\infty} \text{exp}(-\frac{r ^ 2}{2}) r dr\text{d}\theta\\
= \frac{1}{2\pi} \int_0^{2\pi} \text{d}\theta = 1
$$
This indicates that:
$$
f(x) = \frac{1}{2\pi} \text{exp}(-\frac{x ^ 2}{2}) \text{, } -\infty \lt x \lt +\infty
$$
can be pdf of a continuous over $R$, which can be extended to general form of the Normal pdf. For $X \sim N(\mu, \sigma ^ 2)$, consider the substitution:
$$
Z = \frac{X - \mu}{\sigma}
$$
It's easy to prove that $Z \sim N(0, 1)$.
</details>

##  12.1 Definition of Normal R.V.
A Normal R.V. is a continuous R.V. which follows the normal distribution.
##  12.2 pdf of Normal R.V.
$$
f(x) = \frac{1}{\sqrt{2\pi} \sigma} e ^ {-(\frac{x - \mu}{\sigma}) ^ 2} \text{, } -\infty \lt x \lt +\infty\\
\mu \in (-\infty, +\infty), \sigma \in (-\infty, +\infty), \text{a negative } \sigma \text{ is meaningless though.}
$$
It can be written as : $X \sim N(\mu, \sigma ^ 2)$.
##  12.3 Support set of beta R.V.
$$
x \in R = (- \infty, +\infty)
$$

##  12.4 Moment of Normal R.V.
$$
M(t) = \text{exp}\{\mu t + \frac{1}{2}\sigma ^ 2 t ^ 2\} = e ^ {\mu t + \frac{1}{2}\sigma ^ 2 t ^ 2}\\
$$
$\mu$ and $\sigma ^ 2$ are mean and variance of normal distribution respectively. We normally have:
$$
M^{(n)}(0) = E(X ^ n)
$$
In a more clever way:
$$
E(X ^ n) = E[(\sigma Z + \mu) ^ n] = \sum_{i = 0}^n {n \choose i} \sigma ^ i \mu ^ {n - i} E(Z ^ i)
$$
#   12.5 R reference
See [The Normal Distribution](https://stat.ethz.ch/R-manual/R-devel/library/stats/html/Normal.html).

#   13 **The Multivariate Normal Distribution** [continuous]
<details>
<summary>
There are many ways to introduce multivariate normal distribution. Here we start from standard multivariate normal distribution with n variables.
</summary>

Let random vector ${\boldsymbol Z}_{n \times 1} = (Z_1, Z_2, ... ,Z_n)$ where $Z_1, Z_2, ... ,Z_n$ are i.i.d with $Z_i \sim N(0, 1) \text{, } i = 1, 2, ... n$. Its pdf is:
$$
f_{{\boldsymbol Z}}{}({\boldsymbol z}) = (\frac{1}{\sqrt{2 \pi}}) ^ n \text{exp} \{ - \frac{1}{2} {\boldsymbol z}'{\boldsymbol z}\}
$$
Naturally ${\boldsymbol Z}$ has mean vector $0_{n \times 1}$ and covariance matrice $E_n$ (or ${\boldsymbol I}_n$). We say ${\boldsymbol Z} \sim N_n({\boldsymbol 0}, \boldsymbol{I}_n)$.

Now it's time to extend the standard form to general one. Covariance matrix of any n-dimensional random vectors:
1.  are symmetric and therefore and be diagnalized
2.  have non-negative eigen values and therefore psd

Let $\Sigma$ be a $n \times n$ matrice satisfying these two properties. $\Sigma$ has a spectral decomposition:
$$
\Sigma = \Gamma'\Lambda\Gamma
$$
where:
1.  $\Gamma$ is orthognal
2.  $\Lambda$ is diagnal,  $\Lambda = \text{diag}\{\lambda_1, \lambda_2 , ...\}$
3.  each $\lambda_i$ is non negative

Define:
$$
\Lambda ^ {\frac{1}{2}} = \text{diag}\{\lambda_1^\frac{1}{2}, \lambda_2^\frac{1}{2} , ...\}\\
\Sigma ^ \frac{1}{2} = \Gamma'\Lambda ^ \frac{1}{2}\Gamma\\
$$
Since
$$
(\Lambda ^ {\frac{1}{2}}) ^ 2 = \Lambda, (\Sigma ^ \frac{1}{2}) ^ 2 = \Sigma
$$

With these conclusions, consider the substitution:
$$
X = \Sigma ^ \frac{1}{2}Z + {\boldsymbol \mu}_{n \times 1}
$$
It's easy to show that $X$ has mean ${\boldsymbol \mu}$ and covariance matrice $\Sigma$. It is the final n-dimensional normal random vector.
</details>

##  13.1 Definition of Multivariate Normal R.V.
Similar to [The Normal R.V.](#121-definition-of-normal-rv).

##  13.2 pdf of multivariate normal R.V.
$$
f_{\boldsymbol X}({\boldsymbol x}) = \frac{1}{(2\pi) ^ \frac{n}{2} \text{det}(\Sigma) ^ \frac{1}{2}} \text{exp} \{-\frac{1}{2}(\boldsymbol{x - \mu})'\Sigma ^ {-1} (\boldsymbol{x - \mu})\}\\
\boldsymbol{\mu} \in R ^ n \text{, } \Sigma \text{ is symmetric and psd.}
$$
##  13.3 Support set of multivariate normal R.V.
$$
{\boldsymbol x} \in R ^ n
$$
##  13.4 Moment of multivariate normal R.V.
$$
M_{\boldsymbol X}({\boldsymbol t}) = \text{exp}\{{\boldsymbol t'\mu} + \frac{1}{2} {\boldsymbol t}' \Sigma {\boldsymbol t}\} = e ^ {t' \mu + \frac{1}{2} t' \Sigma t}
$$

##  13.5 Useful properties of multivariate normal R.V.
In the following conclusions, assume that:
$$
{\boldsymbol X} \sim N_n(\mu, \Sigma)\\
{\boldsymbol \mu} = (\mu_1, \mu_2, ..., \mu_n)'\\
\Sigma = (\sigma_{ij})_{n \times n}
$$

**Linear substitution of variables**

$Y_{m \times 1} = A_{m \times n}X + b$. Y is also multivariate normally distributed with $Y \sim N_m(A\mu + b, A \Sigma A')$.

**Marginal pdf of a subset of variables**

For any subset $\{k_1, k_2, ..., k_r\} \subset \{1, 2, ..., n\}$, $X_K = (x_{k_1}, x_{k_2}, ..., x_{k_r})$.
$$
{\boldsymbol X}_K \sim N_r(\mu_K, \Sigma_K)\\
{\boldsymbol \mu}_K = (\mu_{k_1}, \mu_{k_2}, ..., \mu_{k_r})\\
\Sigma_K = (\sigma_{i, j\in \{k_1, k_2, ... ,k_r\}})_{r \times r}
$$

**Conditional pdf of a subset of variables**

In this case we suppose $\Sigma$ is pd(positive definite). $\{1, 2, ..., n\}$ is divided into two mutually exclusive and exhaustive subsets: $P = \{p_1, p_2, ... , p_r\}, Q = \{q_1, p_2, ... , p_{n - r}\}$. WLOG $P = \{1, 2, 3, ... ,r\}, Q = \{r+ 1, r+2, ..., n\}$. Let $X_1 = (x_1, ... ,x_r), X_2 = (x_{r + 1}, ... ,x_{n})$ . Define partitioned matrice of $\Sigma$ and $\mu$:
$$
\Sigma = \begin{bmatrix}
\Sigma_{11} & \Sigma_{12}\\
\Sigma_{21} & \Sigma_{22}
\end{bmatrix}\\
\Sigma_{11} = (\sigma_{i,j \in P})_{r \times r}\\
\Sigma_{12} = (\sigma_{i \in P, j \in Q})_{r \times (n-r)}\\
\Sigma_{21} = (\sigma_{i \in Q, j \in P})_{(n - r) \times r}\\
\Sigma_{22} = (\sigma_{i, j \in Q})_{(n - r) \times (n - r)}\\
\boldsymbol{\mu}_1 = (\mu_1, \mu_2, ... ,\mu_r)\\
\boldsymbol{\mu}_2 = (\mu_{r + 1}, ... ,\mu_n)
$$
Then, ${\boldsymbol X_1} | {\boldsymbol X_2}$ is multivariate normally distributed:
$$
{\boldsymbol X_1} | {\boldsymbol X_2} \sim N_r({\boldsymbol \mu}_1 + \Sigma_{12}\Sigma_{22}^{-1}({\boldsymbol X}_2 - {\boldsymbol \mu}_2), \Sigma_{11} - \Sigma_{12}\Sigma_{22}^{-1}\Sigma_{21})
$$

##  13.6 R reference
See [MVNORM](https://www.rdocumentation.org/packages/mvtnorm/versions/1.0-10/topics/Mvnorm).

#   14 **The Student's t-distribution** [continuous]
<details>
<summary>
The Student's t-distribution is a powerful model describing sample means and variances.
</summary>

Assume there are two independent random variables $W \sim N(0,1)$ and $V \sim \chi ^ 2(r)$. They have joint pdf:
$$
h(w, v) = \begin{cases}
\frac{1}{\sqrt{2\pi}} e ^ {-\frac{w ^ 2}{2}} \frac{1}{\Gamma(\frac{r}{2})2 ^ {\frac{r}{2}}} v ^ {\frac{r}{2} - 1} e ^ {-\frac{v}{2}} \text{, } w \in (-\infty, +\infty), v \in (0, +\infty)\\
0 \text{, otherwise}
\end{cases}
$$
Consider the substitution, which is a bijection:
$$
T = \frac{W}{\sqrt{V/r}}\\
U = V
$$
T and U have joint distribution:
$$
g(t, u) = h(\frac{t\sqrt{u}}{\sqrt{r}}, u)|\text{det}(\frac{\partial(w, v)}{\partial(t, u)})|\\
= \begin{cases}
\frac{1}{\sqrt{2\pi}\Gamma(\frac{r}{2})2 ^ {\frac{r}{2}}}u^{\frac{r}{2} - 1}e ^ {- \frac{u(r + t ^ 2)}{2r}}, t\in R, u \gt 0\\
0 \text{, otherwise}
\end{cases}
$$
The marginal of T yields Student's t.
</details>

##  14.1 Definition of Student's t-R.V.
A Student's t-R.V. is a continous R.V. which follows Student's t distribution.
##  14.2 pdf of t R.V.
$$
f(x) = \frac{\Gamma(\frac{r + 1}{2})}{\sqrt{\pi r}\Gamma(\frac{r}{2})} \frac{1}{(1 + \frac{x ^ 2}{r}) ^ {\frac{r + 1}{2}}}\\
r \in N ^ + = \{1, 2, ...\}
$$
##  14.3 Support set of t R.V.
$$
x \in R = (- \infty, +\infty)
$$
##  14.4 Moment of t R.V.
We keep the concept of $W \sim N(0,1)$ and $V \sim \chi ^ 2(r)$ here.
$$
E(T ^ k) = E[W ^ k (\frac{V}{r}) ^ {- \frac{k}{2}}] = E[W ^ k]E[(\frac{V}{r}) ^ {- \frac{k}{2}}] \\
= E(W ^ k)\frac{2 ^ {- \frac{k}{2}} \Gamma(\frac{r - k}{2})}{\Gamma(\frac{r}{2})r ^ {- \frac{k}{2}}}, k \lt r\\
\mu = 0\\
\sigma ^ 2 = \frac{r}{r - 2} (r \gt 2)
$$

##  14.5 R reference
See [The Student t distribution](https://stat.ethz.ch/R-manual/R-devel/library/stats/html/TDist.html).

#   15 **The F Distribution**
<details>
<summary>
The ratio of two independent Chi-squared random variables generates an F variable.
</summary>

Suppose there are two independent random variables $U \sim \chi ^ 2(r_1)$ and $V \sim \chi ^2(r_2)$. They have joint pdf:
$$
h(u, v) = \begin{cases}
\frac{1}{\Gamma(\frac{r_1}{2})\Gamma(\frac{r_2}{2}) 2 ^ {\frac{r_1 + r_2}{2}}} u ^ {\frac{r_1}{2} - 1} v ^ {\frac{r_2}{2} - 1}e ^ {-\frac{u + v}{2}}, u, v\in R ^ +\\
0 \text{, otherwise}
\end{cases}
$$
Let $W = \frac{\frac{U}{r_1}}{\frac{V}{r_2}}, Z = V$. This substitution is also a bijection. These two variables have joint pdf:
$$
g(w, z) = \frac{1}{\Gamma(\frac{r_1}{2})\Gamma(\frac{r_2}{2})2 ^ \frac{r_1 + r_2}{2}} (\frac{r_1zw}{r_2}) ^ {\frac{r_1 - 2}{2}} z ^ {\frac{r_2 - 2}{2}} e ^ {-\frac{z(r_1w + r_2)}{2r_2}} \frac{r_1z}{r_2},
w \gt 0, z \gt 0
$$
Marginal pdf of W generates an F distribution with parameter $r_1$ and  $r_2$. 
In [the Beta distribution](#11-the-beta-distribution-continuous), order of parameter $\alpha$ and $\beta$ doesn't matter. 
In F distribution, the order matters.
We say W has F distribution with parameter $r_1$ and $r_2$.
</details>

##  15.1 Definition of F R.V.
An F R.V. is a continous R.V. which follows the F distribution.

##  15.2 pdf of F R.V.
$$
f(x) = \begin{cases}
\frac{\Gamma(\frac{r_1 + r_2}{2})(\frac{r_1}{r_2}) ^ {\frac{r_1}{2}}}{\Gamma(\frac{r_1}{2})\Gamma(\frac{r_2}{2})}\frac{x ^ {\frac{r_1}{2} - 1}}{(1 + \frac{r_1x}{r_2}) ^ \frac{r_1 + r_2}{2}}, x \gt 0\\
0 \text{, otherwise}
\end{cases}
$$
##  15.3 Support set of F R.V.
$$
x \in R ^ +
$$
##  15.4 Moment of F R.V.
$$
M(t) \text{ does not exist.}\\
E(F ^ k) = (\frac{r_2}{r_2}) ^ k E(U ^ k)E(V ^ {-k})
$$
When $2k < r_2$:
$$
\mu = \frac{r_2}{r_2 - 2}, r_2 \gt2\\
\sigma ^ 2 = 2(\frac{r_2}{r_2 - 2}) ^ 2\frac{r_1 + r_2 - 2}{r_1(r_2 - 4)}, r_2 \gt4
$$

##  15.5 R reference
See [The F distribution](https://stat.ethz.ch/R-manual/R-devel/library/stats/html/Fdist.html).

