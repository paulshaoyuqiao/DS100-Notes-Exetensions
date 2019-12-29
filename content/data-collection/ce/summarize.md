Within our dataset, the most basic element is a single observation. In the simplest context, if an observation contains just one feature (one dimension), it is simply a number. 

Usually, we can readily have data come in a list of numbers (when the list is very long, we usually call it *a stream of numbers* instead). Throughout this section and the book, we will see that even for raw data with much more complex forms, such as images and audio files, we are still able to reduce and convert them to a set of numerical observations. In those cases though, each observation likely will have more than one feature.

For simplicity and generality of notation, we will work primarily with a list of $n$ numerical samples (one-dimensional samples, $x_i \in \mathbb{R}$, $i = 1, 2, \dots, n$): $$X = [x_1, x_2, \dots, x_n ]$$
In statistics, any numerical quantity $s = f(X)$ that can be calculated from the sampling dataset $X$ is called a **summary statistic**.

# Measures of Location: Mean and Median

A measure of location is a statistic that represents the center of the sample. One such measure is the **sample mean**, which is the **average of the sample**:
$$
\bar{x} = \frac{1}{n}\sum_{i=1}^n x_i = \frac{x_1 + x_2 + \dots + x_n}{n}.
$$
## Main Drawbacks of the Mean

The main drawback of the mean is that it is **sensitive to outliers**. We can interpret an outlier as an observation $x'$ that is *far away* from other observations within the sampling dataset. 

There could be various causes of an outlier. The **intrinsic variability of the data** (for example, in a dataset detailing an American's amount of wealth, Bill Gates will be an outlier toward the far right of the distribution) and **measurement error** are two common factors that lead to outliers. 

A particularly large or small outlier can move the mean considerably in the positive or negative direction correspondingly as well. As we can see from how the mean is calculated above, **each sample is contributing EQUALLY to the mean** (which might introduce bias as well to how the true population is actually represented).

## A More Robust Measurement: Median

Another measure of location that is more robust to outliers is the **median**. The median is the data point that **divides the sampling dataset in equal halves**. 

To calculate the median, we also need to sort the data first as well. Suppose the sampling dataset $X$ is sorted in **increasing order** such that:
$$x_1 \leq x_2 \leq \dots \leq x_n$$
We can define the median as follows:
$$
\tilde{x} = 
\left\{
    \begin{matrix}
        x_{\frac{n+1}{2}} & \text{if } n \text{ is odd},\\ 
        \frac{1}{2}(x_{\frac{n}{2}} + x_{\frac{n}{2} + 1}) & \text{if } n \text{ is even}.
    \end{matrix}
\right.
$$
Due to the nature of median requiring the data to be sorted first, we also call median an **order statistic**. 

## Main Drawbacks of the Median

The main drawback of the median is exactly the opposite of that of the mean: **it is too insensitive to the change in the sample values.**

For example, consider a sample dataset of $n$ values, where $n = 2k-1$ (there is an odd number of values in total). In this case, the median is $\tilde{x} = x_k$. Now, if we arbitrarily multiply the right half of the sorted sample dataset by $10^9$ (this means $x_{k+1}, x_{k+2}, \dots, x_n$ now become $10^9 x_{k+1}, 10^9 x_{k+2}, \dots, 10^9 x_n$), does that change the overall median of the dataset?

**Unfortunately no**, since the data still remains sorted, our median is still equal to $\tilde{x} = x_k$. This implies making the values of the right half of the sampling dataset **arbitrarily large does not affect the median**. The same applies to **making the left half arbitrarily small** as well. 

# Measures of Spread: Variance and Standard Deviation

A measure of spread usually gives an idea of **how far an individual value $x_i$ vary from the center of the data**. The simplest measure of spread is the **range**, which is simply the difference between the smallest and largest samples in the dataset,
$$r = x_{\max} - x_{\min}$$
As indicated by the formula above, the range $r$ is very sensitive by outliers.

A more common measure of spread is the **sample standard deviation** $\sigma_X$:
$$
\sigma_X = \sqrt{
    \frac{1}{n} \sum_{i=1}^n (x_i - \bar{x})^2
},
$$
where $\bar{x}$ is the mean of the dataset. 

The variance, which is much easier to work with mathematically, is simply the standard deviation squared:
$$V_X = (\sigma_X)^2$$
## Biased v.s. Unbiased Sample Variance

As you might have seen in some other classes, there are 2 ways of defining sample standard deviation for a dataset of $n$ samples. We will be discussing the difference and usages of the two.

The **biased sample varaince** has the more commonly-known formula as follows:
$$
\sigma^2_{X, biased} = \frac{1}{n} \sum_{i=1}^n (x_i - \bar{x})^2
$$
It is used to compute an estimate of the population's standard deviation $\sigma_{X, biased}$.

The **unbiased sample variance** is an **unbiased estimator of the population variance** and has the following form:
$$
\sigma^2_{X, unbiased} = \frac{1}{n-1} \sum_{i=1}^n (x_i - \bar{x})^2
$$
This estimator is unbiased if the variance exists and the sample values are **drawn independently with replacement**. When we take the square root of the unbiased sample variance, it gives us the **corrected sample standard deviation**.

Now, why does the second formula above produce an **unbiased estimator of the population variance**? What does **an unbiased estimator** even mean in the first place? We will see that shortly in the section that follows.

# A Probabilistic Perspective: Random Variables

To introduce the notion of *an unbiased estimator*, we have to first talk about random variables.

## Let's build some intuitions first

For this section, we will be discussing primarily **discrete random variables**. Note that there are also **continuous random variables** as well, which we will discuss in later chapters (they work similarly to discrete random variables though, except on a continuous scale).

### Random Variables

A **random variable is a numerical function defined on an outcome space**. You can think of the outcome space as **a collection of possible outcomes we can achieve for a certain event**. For example, if I toss a coin, I can define my outcome space as the set $X$, where $X = \{ H, T \}$ ($H$ is for head up, $T$ is for tail up). A more concrete way of putting this is that it is a variable that can **take on a collection of possible values as numerical outcomes for a random event**.

### Probability Distribution

The probability distribution of a random variable includes **all possible values the random variable can take on along with their probabilities** (the chance that the random variable takes on that value). There are many ways we can represent the probability distribution of a random variable, some common ways include:

* A probability distribution table, where we enumerate all possibilities (usually the
value the random variable + the probability that happens) **row by row**.
* A **histogram** visualizing the distribution, where the $x$ axis stands for the values the random variable takes on, and the $y$ axis maps to the corresponding probability.
  
For example, a probability distribution table summarizing the random variable $X$ for the random event of tossing a fair coin and checking which side it lands on is as follows:

| $x$ | $P(X = x)$    |
|-----|:-------------:|
| $H$ | $\frac{1}{2}$ |
| $T$ | $\frac{1}{2}$ |

## Expectation (Expected Value)

### Definition and Example

The expected value of a random variable $X$, denoted by $E[X]$, represents the average of the possible values $X$ can take on weighted by their probabilities. Again, it gives us a notion of where the ”center” of the probability distribution lies if we plot that out for $X$.

For all possible values of $x$ that the random variable $X$ can take on:
$$E[X] = \sum_{\text{all } x's} x \cdot P(X = x)$$
For example, if I have the value of a regular die after rolling as a random variable $X$, the expected value of $X$ can be calculated as the sum of all the possible values the die can have multiplied (or weighted) by the chance of us getting that particular value.

More detailedly, we can treat **the event of rolling a regular die and checking the number that is facing up** as a random variable $X$. $X$ takes on the following probability distribution

| $x$ | $P(X = x)$    |
|-----|:-------------:|
| $1$ | $\frac{1}{6}$ |
| $2$ | $\frac{1}{6}$ |
| $3$ | $\frac{1}{6}$ |
| $4$ | $\frac{1}{6}$ |
| $5$ | $\frac{1}{6}$ |
| $6$ | $\frac{1}{6}$ |

The expected value of $X$ is equal to:
$$E[X] = \sum_{x=1}^6 x \cdot P(X = x)$$
Note that $P(X=x)$ is the same for all $x$'s, we can factor that probability outside the sumamtion:
$$E[X] = P(X=x) \sum_{x=1}^6 x = \frac{1}{6}(1+2+3+4+5+6) = \frac{21}{6} = 3.5.$$
### Properties of Expected Values

Here are a few common arithmetic properties of expectations that are helpful when dealing with a transformed/augmented dataset. For random variables $X, Y$, and a real-valued scalar $a$:

- **Non-negativity**: if $X \geq 0$, then $E[X] \geq 0$.
- **Linearity of Expectation**: 
  - $E[X+Y] = E[X] + E[Y].$
  - $E[aX] = aE[X].$
- **Independence**:
  - If $X$ and $Y$ are **mutually independent of each other**:
    - $E[XY] = E[X]E[Y].$
- **Non-degeneracy**:
  - If $E[X] = 0$, then it must be true that $X = 0$.
- **Expected Value of a Constant**:
  - $E[a] = a.$
- **Expected Value of Functions of a Random Variable**
  - Suppose the random variable $Y = f(X)$, where $f$ is a function applied on every value $X$ can take on. More precisely, $Y$ has the probability distribution: $$p_Y = \{ (f(x_1), P(Y = x_1)), \dots, (f(x_n), P(Y = x_n))\},$$ $$ E[Y] = E[f(X)] = \sum_{i=1}^n f(x_i) P(X = x_i).$$

An illustration of the last property (expected value of functions of a random variable) is as follows. Consider $X$ again as the random variable representing tossing a regular die and checking the number facing up, and let $Y$ be another random variable such that $Y = f(X)$, where $f(\omega) = \omega^2$ for all $\omega$ in the outcome space of $X$. We have:
$$E[Y] =  E[f(X)] = \sum_{i=1}^n f(x_i)^2 P(X=x_i) = \sum_{i=1}^6 (x_i)^2 P(X=x_i)$$
Simplifying further, this gives us:
$$E[Y] = \frac{1^2 + 2^2 + 3^2 +4^2 +5^2 +6^2}{6} = \frac{91}{6}$$

## Variance

## Definition and Example

Variance is the expectation of the squared deviation of a random variable from its mean. Informally, it measures how far a set of (random) numbers are spread out from their average value.

The variance is defined as follows:
$$Var[X] = E[(X - \mu)^2], \:\: \mu = E[X]$$
There is also a more straightforward computational formula for the variance (we can derive upon expanding the inside of the expectation and using some of the previous properties of expectations we have mentioned above):
$$Var[X] = E[X^2] - (E[X])^2$$

Here's the derivation for the computational formula above:
$$
\begin{aligned}
    Var[X] &= E[(X-\mu)^2] = E[X^2 - 2\mu X + \mu^2] = E[X^2] - E[2\mu X] + E[\mu^2] \\
           &= E[X^2] - 2\mu E[X] + \mu^2 = E[X^2] - 2\mu^2 + \mu^2 \\
           &= E[X^2] - \mu^2 \\
           &= E[X^2] - (E[X])^2
\end{aligned}
$$
Let's revisit the example of rolling the die. Let $X$ be the random variable of rolling a regular die and checking the number facing up, we have:
$$
Var[X] = E[X^2] - (E[X])^2 = \frac{91}{6} - (\frac{21}{6})^2 = \frac{35}{12}
$$
We can also use the **biased variance estimate** formula from the statistical perspective:
$$
Var[X] = \frac{1}{6}\sum_{i=1}^6 (x_i - \mu)^2 = \frac{\sum_{i=1}^6 (x_i - 3.5)^2}{6} = \frac{35}{12}
$$
### Properties of Variance
Let $X$ be a random variable, and $c$ a real-valued scalar, we have:
- $Var[cX] = c^2 Var[X].$
- $Var[X + c] = Var[X].$

In general, for two random variables $X$ and $Y$, $Var[X+Y] \neq Var[X] + Var[Y]$.

# Unbiased Estimator

Now that we have talked about both the statistical and probabilistic perspectives of summarizing data, let's return to the question we posed in the earlier section about the unbiased estimator of the population variance.

## What's the bias of an estimator?

Recall in the data science lifecycle, the 4th stage requires us to build a model that makes predictions/estimations which address the hypothesis/experiment we formulate. Let's call this model an estimator. The bias of the estimator measures **the difference between this estimator's expected value and the true value of the parameter being estimated**. 

## What's an unbiased estimator?

Based on our definition above, an unbiased estimator is an estimator that has 0 bias. In other words, if **the estimator's expected value is equal to the true value of the parameter being estimated**, the estimator is **unbiased**.

## Biased v.s. Unbiased Estimators of Population Variance

Let's revisit the example we mentioned earlier. Recall that **the uncorrected sample variance** for a sample dataset of $n$ samples is defined as:
$$\sigma^2_{X, biased} = \frac{1}{n}\sum_{i=1}^n (x_i - \bar{x})^2$$.
Assuming our data sampling process is random and even, we can treat all $n$ samples $x_1, x_2, \dots, x_n$ as independent and identically distributed (i.i.d) random variables $X_1, X_2, \dots, X_n$ with expected value $\mu$ and variance $\sigma^2$.

We can see that the **true variance of the sample dataset** is $\frac{1}{n}\cdot n\sigma^2 = \sigma^2$.

To check that **the uncorrected sample variance** is a biased estimator of $\sigma^2$, we evaluate:
$$
\begin{aligned}
    E[\sigma^2_{X, biased}] &= E\left[\frac{1}{n}\sum_{i=1}^n (X_i - \bar{X})^2\right] \\
     &=  E\left[\frac{1}{n}\sum_{i=1}^n \left( (X_i - \mu)^2 + 2(\bar{X} - \mu)(X_i - \mu) + (\bar{X} - \mu)^2 \right)\right] \\
    &= E\left[\frac{1}{n}\sum_{i=1}^n (X_i - \mu)^2 + \frac{2}{n}(\bar{X} - \mu)\sum_{i=1}^n (X_i - \mu) + (\bar{X} - \mu)^2 \right] \\
    &= E\left[\frac{1}{n}\sum_{i=1}^n (X_i - \mu)^2 + \frac{2}{n}(\bar{X} - \mu)\cdot n \cdot (X_i - \mu) + (\bar{X} - \mu)^2 \right] \\
    &= E\left[\frac{1}{n}\sum_{i=1}^n (X_i - \mu)^2 + 2(\bar{X} - \mu)^2 + (\bar{X} - \mu)^2 \right] \\
    &= E\left[\frac{1}{n}\sum_{i=1}^n (X_i - \mu)^2 \right] + E\left[(\bar{X} - \mu)^2 \right] \\
    &= \sigma^2 - E\left[(\bar{X} - \mu)^2\right] \\
    &= \left( 1 - \frac{1}{n} \right) \sigma^2 < \sigma^2.
\end{aligned}
$$
Hence, we can see that $E[\sigma^2_{X, biased}] \neq sigma^2$.

On the other hand, we also have the **the corrected sample variance**:
$$\sigma^2_{X, unbiased} = \frac{1}{n - 1}\sum_{i=1}^n (x_i - \bar{x})^2$$.
Again, Let's evaluate the expected value of the corrected sample variance:
$$
\begin{aligned}
    E[\sigma^2_{X, unbiased}] &= \frac{n}{n-1}E\left[\frac{1}{n}\sum_{i=1}^n (X_i - \bar{X})^2\right] \\
    &= \frac{n}{n-1}\left(1-\frac{1}{n}\right)\sigma^2 \\
    &= \sigma^2.
\end{aligned}
$$

Hence, we can see that the **corrected sample variance is an unbiased estimator of the population variance**, $\sigma^2$.