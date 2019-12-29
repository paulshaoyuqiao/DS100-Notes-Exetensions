In the data collection stage of the lifecycle, we rely on a few sampling methods to select members from the population to be included in the study.

In this section, we will go over some good and bad ways to build our sampling dataset.

# Good Ways to sample

## Simple Random Sample (SRS)

**Every member and set of members has an equal chance of being included in the sample**. Usuallly we utilize a random number generator or some other chance process to retrieve a simple random sample from the population. 

![illustration](https://faculty.elgin.edu/dkernler/statistics/ch01/images/srs.gif)

Another intuitive example would be if a group of people wants to sample from all the members, putting people's names in a box and choosing without looking is resembling of the Simple Random Sample approach.

## Stratified Random Sample

In this sampling method, the population is first split into groups. The overall sample consists of some members from every group. The members from each group are chosen randomly.

![illustration](https://faculty.elgin.edu/dkernler/statistics/ch01/images/strata-sample.gif)

Here's another example: the ASUC surveys 100 undergraduate students by getting random samples of 25 freshmen, 25 sophomores, 25 juniors, and 25 seniors.

A stratified sample guarantees that members from each group will be represented in the sample, so this sampling method is **suited** for when we want an even representation of members from every group.

### Common Stratified Sampling Strategies

#### Proportionate Allocation

Proportionate allocation uses a **sampling fraction** in each of the strata that is proportional to that of the total population. 

For example, if the population consists of $N$ total individuals, $M$ of which are male and $F$ are female (where $M+F = N$), then maintaining the relative size of the two samples ($n_1 = \frac{M}{N}$ males, $n_2 = \frac{F}{N}$ females) should reflect this proportion.

Numerically, if let $N = 100$, $M = 40$, $F=60$, then if we use proportionate allocation for stratified sampling, and assume we sample a total of 10 individuals. We want to make sure we sample $\frac{40}{100} \times 10 = 4$ males for the male stratum, and $\frac{60}{100} \times 10 = 6$ females for the female stratum.

#### Optimum Allocation

The sampling fraction of each stratum is proportionate to both the proportion and **the standard deviation of the distribution of the variable**. Larger samples are taken in the strata with **the greatest variability** to **generate the least possible overall sampling variance**.

### Advantages of Stratified Sampling

We generally prefer stratified sampling to simple random sampling when:
1. measurements within strata have **lower standard deviation**; stratification gives smaller error in estimation.
2. measurements become more manageable/cheaper when the population is grouped into strata.
3. we want to have **estimates of population parameters** for groups within the population.

If the population density varies greatly within a region, stratified sampling will ensure that estimates can be made with equal accuracy in different parts of the region, and that comparisons of sub-regions can be made with equal statistical power.

### Disadvantages of Stratified Sampling

Stratified Sampling fails when the population cannot be partitioned into **disjoint subgroups**.

One thing to be cautious about is that combining sub-strata to ensure adequate and even numbers is not always desirable as it can lead to **Simpson's paradox**, where trends that **actually exist in different groups of data disappear or even reverse when the groups are combined**.

## Cluster Random Sample

Contrary to Stratified Sampling, in cluster sampling, the population is first divided into groups. The overall sample consists of every member from some of the groups. THe groups are then selected at random.

![illustration](https://faculty.elgin.edu/dkernler/statistics/ch01/images/cluster-sample.gif)

Here's another example: an airline company wants to survey its customers one day, so they randomly select 5 flights that day and survey every passenger on those flights.

A cluster sample guarantees that every member from the chosen groups is surveyed. It performs well when each group reflects the population as a whole.

### Advantages of Cluster Sampling

Since cluster sampling samples all the members within a few randomly chosen cluster, it is usually cheapter than other sampling methods.

Practically speaking though, we resort to cluster sampling only when **the sampling frame of all elements is not available**.

### Disadvantages of Cluster Sampling

1. Cluster sampling tends to produce higher sampling error. In particular, when we have greater differences (**hetreogeneity**) between clusters (**intercluster difference**) and greater similarity (**homogeneity**) between elements within a cluster (**intracluster similarity**), cluster sampling will become a lot less accurate. 
2. As convenient and economical as cluster sampling is, it is usually more sophisticated and requires more attention to analyze and interpret the collected data to approximate the actual true population.

### Two-Stage Cluster Sampling

The first disadvantage that we have seen in the previous section leads us to an augmented cluster sampling method: two-stage cluster sampling.

As a variant of multistatge sampling, two-stage cluster sampling works by:
1. selecting cluster samples
2. selecting a sample of elements from every sampled cluster (usually using SRS)

Note that in the second stage, the number of elements selected from different clusters are **not necessarily equal**.

The two-stage cluster sampling method aims at minimizing survey costs and at the same time **controlling the uncertainty related to estimates of interest**.

## Systematic Random Sample

In systematic sampling, members of the population are sorted in some order. A starting point is then selected at random, and every $i$th member is chosen to be in the sample.

![illustration](https://faculty.elgin.edu/dkernler/statistics/ch01/images/sys-sample2.gif)

Here's another example: a principal takes an alphabetized list of student names and picks a random starting point. Every 20th student is selected to take a survey.

# Bad Ways to sample

Here are a few common sampling methods that could easily result in **selection bias**.

## Convenience sample

We choose a sample that is readily available in some non-random way.

For example, we poll students as they walk into the entrance of a lecture hall on campus.

It easily introduces biases as the location and time of day and other factors can produce a biased sample of people. 

## Voluntary Response Sample

We put out a request for members of a population to join the sample, and people decide whether or not to be in the sample.

A very common example is sending out a Google Form and asking people to fill it out.

It easily introduces biases as the people might either not respond (**non-response bias**) or for the ones who do, they might tend to **have similarly strong opinions compared to the rest of the population**.