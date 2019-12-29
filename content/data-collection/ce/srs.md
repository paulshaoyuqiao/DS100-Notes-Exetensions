In simple random sampling (SRS), every subset of $n$ units in the population has the same chance of being the sample. 

Mathematically, if we are to sample $n$ units **one at a time without replacement** from a total population of $N$ units, the chance of us obtaining a particular sample is equal to:
$$\frac{1}{(N \text{ choose } n)} = \frac{1}{\binom{N}{n}}$$
# Sample Mean $\bar{X}_n$ v.s. the Population Mean $\mu$

Supppose our population $P$ contains $m$ distinct values in total $p_1, p_2, \dots, p_m$. Suppose for each distinct value $p_i$, there is a total of $n_i$ occurrences for that value. Then, we can represent each sample element as a discrete random variable $X_i$ with the probability mass function:
$$P(X_i = p_j) = \frac{n_j}{N}, \:\: j=1,\dots,m$$
and we can derive its expectation and variance to be:
$$E[X_i] = \mu, \:\:\: Var[X_i] = \sigma^2$$
Since for simple random sampling, we know the sample mean $\bar{X}_n$ to be:
$$
\bar{X}_n = \frac{1}{n}\sum_{i=1}^n X_i
$$
We have:
$$
\begin{aligned}
    E[\bar{X}_n] &= E\left[\frac{1}{n}\sum_{i=1}^n X_i\right] \\
                 &= \frac{1}{n} \sum_{i=1}^n E[X_i] \\
                 &= \frac{1}{n} \sum_{i=1}^n \mu \\
                 &= \mu
\end{aligned}
$$
Hence, we can see that with SRS, $E[\bar{X}_n] = \mu$. From previous sections, we conclude that **$\bar{X}_n$ is an unbiased estimator of the true population mean $\mu$**.

# Covariances

Before jumping into the variance of the dataset obtained thorugh SRS, let's review the concept of covariance, which will be important in the following section.

Covariance ($Cov$) provides a measure of the **strength of the (linear) correlation between two or more sets of random variables**. Mathematically, it is defined as:
$$Cov(X, Y) = E[(X - \mu_X)(Y - \mu_Y)],$$
where $X$ and $Y$ are two random variables, and $\mu_X = E[X], \mu_Y = E[Y]$.

Similar to variance, we can further expand the inside of the expression and obtain an easier computational formula for covariance:
$$Cov(X, Y) = E[XY] - \mu_X \mu_Y$$

This also allows us to rewrite variance:
- $Cov(X, X) = Var[X]$.
- $Var[X+Y] = Var[X] + Var[Y] + 2Cov(X, Y)$.

# Independence

Now that we know covariance a way to measure how strongly two random variables correlate with each other, let’s look into an extreme case where two random variables do not correlate with each other at all - independence.

Two random variables are independent if they **convey no information about each other**
and, as a consequence, receiving information about one of the two does not change our
assessment of the probability distribution of the other. In other words, the value of gaining information about two independent random variables with respect to each other is equal to 0. In more concrete terms, **knowing about the outcomes and probability distribution of one random variable doesn’t help us find out about those of the other one if they are independent**.

Given two independent random variables $X$ and $Y$, we know that:
- $E[X]E[Y] = E[XY]$
- $Cov(X, Y) = 0$
- $Var[X+Y] = Var[X] + Var[Y]$

# Variance of the Sample Mean $\bar{X}_n$
Let's first rewrite the variance in terms of covariances:
$$
\begin{aligned}
    Var[\bar{X}_n] &= Var \left[ \frac{1}{n} \sum_{i=1}^n X_i \right] = \frac{1}{n^2} Var \left[\sum_{i=1}^n X_i \right] \\
    &= \frac{1}{n^2} \sum_{i=1}^n \sum_{j=1}^n Cov(X_i, X_j)
\end{aligned}
$$

To compute the variance, let's make use of another lemma:
if $i \neq j$, then the covariance between $X_i$ and $X_j$ is:
$$Cov(X_i, X_j) = -\frac{\sigma^2}{N - 1}$$

Now we are ready to derive the variance of the sample mean:
$$
\begin{aligned}
    Var[\bar{X}_n] &= \frac{1}{n^2} \sum_{i=1}^n \sum_{j=1}^n Cov(X_i, X_j) \\
    &= \frac{1}{n^2}\sum_{i=1}^n Var(X_i) + \frac{1}{n^2} \sum_{i=1}^n \sum_{j\neq i} Cov(X_i, X_j) \\
    &= \frac{\sigma^2}{n} - \frac{1}{n^2} n(n-1) \frac{\sigma^2}{N - 1} \\
    &= \frac{\sigma^2}{n}\left(\frac{N-n}{N -1}\right) \\
    &= \frac{\sigma^2}{n}\left(1 - \frac{n - 1}{N -1}\right)
\end{aligned}
$$

Hence, the variance of $\bar{X}_n$ is given by:
$$
Var[\bar{X}_n] = \frac{\sigma^2}{n}\left(1 - \frac{n - 1}{N -1}\right)
$$
Here're a few important observations:
1. The factor $(1 - \frac{n-1}{N-1})$ is called *finite population correction*. We can see that $1 - \frac{n-1}{N-1} \approx 1 - \frac{n}{N}$, where the ratio $\frac{n}{N}$ is the **sampling fraction**.
2. We can see that $(1 - \frac{n-1}{N-1})$ is always less than one. Therefore, we have: $$Var[\bar{X}_n] < \frac{\sigma^2}{n}$$. We will explore in later sections on what this inequality implies.
3. If the sampling fraction is small ($n << N$), then: $$Var[\bar{X}_n] \approx \frac{\sigma^2}{n}, \:\:\: \sigma_{\bar{X}_n} \approx \frac{\sigma}{\sqrt{n}}$$
4. To double the accuracy of the approximation $\bar{X}_n$, the sample size $n$ must be quadrupled.
5. If $\sigma$ is small (population values are not very dispersed), then a small sample will be fairly accurate. However, as $\sigma$ increases, we will need a larger sample to obtain the same accuracy.

# Sampling with Replacement

Let's look at a simpler case of simple random sampling, done with replacement. In this case,**each sample random variable $X_i$ can be treated as independent of each other**. This would give us the following expressions for the sample mean, sample variance, and sample standard deviation.

- **Sample Mean**: $$E[\bar{X}_n] = \mu$$
- **Sample Variance**: $$Var[\bar{X}_n] = \frac{1}{n^2} \sum_{i=1}^n Var[X_i] = \frac{1}{n^2} \sum_{i=1}^n \sigma^2 = \frac{\sigma^2}{n}$$
- **Sample Standard Deviation**: $$\sigma_{\bar{X}_n} = \sqrt{Var[\bar{X}_n]} = \frac{\sigma}{\sqrt{n}}$$

## SRS (Without Replacement) v.s. Sampling With Replacement

Now, back to the second and third observations we have made about SRS without replacement above:
1. Since we know that $Var[\bar{X}_n] < \frac{\sigma^2}{n}$, this means simple random sampling (without sampling) is **more efficient than sampling with replacement**.
2. When $n << N$, we can see that the sample mean and the variance of the sample mean is **approximately the same as if we sample with replacement**.

## One Last Thing to Note

In Simple Random Sampling, we sample **without replacement**.