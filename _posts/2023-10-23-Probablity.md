---
title: Probablity
author: Bhoomeendra
date: 2023-10-23
category: MATHS
layout: post
comments: true
---
# Introduction

## Sample Space: 
The set of all possible outcomes of an experiment is called the sample space of the experiment and is denoted by S.

## Event: 
Any subset of a sample space is called an event and denoted by E.

## Naive Definition of Probability: 
The probability of an event E is the ratio of the number of outcomes favorable to E to the total number of outcomes in the sample space S.

Assumptions of Naive Definition of Probability:
1. The sample space S is finite.(Very strong assumption)
2. All the outcomes in S are equally likely.

Probability of life on nepturne: 1/2 (Either it is there or it is not there)

# Counting

Selection: This is denoted by $ C_{k}^{n} = \binom{n}{k}$

|  | orderd | not orderd |
|---|---|---|
| Replacment | $n^k$ | ? |
| No Replacment | $n(n-1)...(n-k+1)$ |  $\binom{n}{k}$|


what the upper write corner cell mean is that lets say we are given a string of unique elements of length n how many unique can a sting of length k from it and we are allowed to use the same element again and again.

A very nice and important way to transform the problem is to think that we have n classes and each obj but belong to only one class. Now we have to select k objects such that the set of classes and counts of the k object belong to is unique. 2221 and 1222 are the same
but 2212 and 2211 are different.

Solution:
Let us imagine we have k objects and n-1 walls. These n-1 walls makes n boxes/classes that the objects may belong to before the assignment to a box the objects do no have any class. We have to place the k objects in the n-1 walls. This can be done in $\binom{n+k-1}{k}$ ways.

Extenstion of the above problem: How many ways can we place k objects in n boxes such that each box has atleast one object.

## Non navie Defination of Probability: 
Let S be a sample space and P be a function from S to [0,1] such that
1. P(S) = 1
2. P($\phi$) = 0
3. For any sequence of mutually exclusive events $E_1,E_2,...$ we have $P(\bigcup_{i=1}^{\infty}E_i) = \sum_{i=1}^{\infty}P(E_i)$

## Trick
Keep this in mind when solving problems P(A) = 1 - P(A')

## Properties of Probability

1. $P(\bar{A}) = 1 - P(A)$
2. If $A\subseteq B$ then $P(B) = P(A) + P(B \cap \bar{A})$
3. Independence of Events: Two events A and B are said to be independent if $P(A \cap B) = P(A)P(B)$

## Conditional Probability
The conditional probability of an event A given that an event B has occured is defined as $P(A|B) = \frac{P(A \cap B)}{P(B)}$. The formula can be understood as follows as the event B has already happened we are only interested in the outcomes of A that are in B. So we only consider the outcomes of A that are in B and divide it by the total number of outcomes in B as this is our new sample space given the prior that B has occured.

$$P\left(\frac{A}{B}\right)P(B) = P(A\cap B)$$

$$P\left(\frac{B}{A}\right)P(A) = P(A\cap B)$$

$$P(A_1 \cap A_2 ... A_n) = P(A_1)P\left(\frac{A_2}{A_1}\right)P\left(\frac{A_3}{A_1 \cap A_2}\right)...P\left(\frac{A_n}{A_1 \cap A_2 \cap ... \cap A_{n-1}}\right)$$

## Bayes Theorem

$$P\left(\frac{A}{B}\right) = \frac{P(A)P\left(\frac{B}{A}\right)}{P(B)}$$

## Law of Total Probability

$$P(B) = P(A_1)P\left(\frac{B}{A_1}\right) + P(A_2)P\left(\frac{B}{A_2}\right) + ... + P(A_n)P\left(\frac{B}{A_n}\right)$$

$A_1,A_2,...,A_n$ are mutually exclusive and exhaustive events.

## Problem
Paitent get tested for a desease. The test is 99% accurate. The probability of a person having the desease is 1%. What is the probability that a person has the desease given that the test is positive.? Hint: $P(A) = P(A\cap B) + P(A \cap \bar B)$

## Conditional Independence

Two events A and B are said to be conditionally independent given an event C if $P(A \cap B\| C) = P(A\|C)P(B\|C)$

## Problem
You have one fair coin and one baised coin that has a probability of 0.75 of landing on heads. You pick one of the coins at random and flip it thrice. Given that you see heads all the times, what is the probability that you picked the fair coin?

## Montey Hall Problem
We have 3 doors, 1 have car and 2 have goats. We choose one door and the host opens one of the other doors that has a goat. Now we have to choose between the door we choose and the other door. What is the probability that we win if we switch the door?

This is a very intersing problem and the solution is intutive but not obvious. The solution is that the probability of winning if we switch is 2/3 and if we do not switch is 1/3. When we are making the first selection we have 1/3 probability of choosing the door with the car and 2/3 probability of choosing a door with a goat. So most probably we will choose a door with a goat now that we now that the host will open a door with a goat its better to switch. The calculation of probability is as follows. Let us say that we choose door 1 and the host opens door 2. Now we have to choose between door 1 and door 3. The probability of winning if we switch is the probability that the car is behind door 3 given that the host opened door 2. P(Winning/Switing) = P(Goat)*P(Car/Goat) = 2/3. P(Car/Goat) =1 because if the door which we have selected has goat behind it then the other door has to have the car behind it. 

# Random Variables
It is a function from sample space to a real line.

# Probablity Distribution
In probability theory and statistics, a probability distribution is the mathematical function that gives the probabilities of occurrence of different possible outcomes for an experiment. It is a mathematical description of a random phenomenon in terms of its sample space and the probabilities of events (subsets of the sample space). The event are mapped to real numbers by the random variable. 

## Probability Mass Function
The probability mass function of a discrete random variable X is a function that gives the probability of X taking a random value.

## Probability Density Function
The probability density function of a continuous random variable X is a function that gives the probability of over a range of X when integrated over it.

## Cumulative Distribution Function
The cumulative distribution function of a random variable X is a function that gives the probability that X will take a value less than or equal to x.


## Bernoulli Probablity Distribution

A random variable X is said to have Bernoulli Distribution if it takes two values ( 0  and 1)and is denoted by $X \sim Bern(p)$ where p is the probability of the random variable taking the value 1. The probability mass function of the random variable is given by $P(X = x) = p^x(1-p)^{1-x}$

## Binomial Probablity Distribution

A random variable X is said to have Binomial distribution if we perform n independent Bernoulli trials with probability of success p. The distribution is over the number of success. The probability mass function of the random variable is given by $P(X = k) = \binom{n}{k}p^k(1-p)^{n-k}$

## Properties of Cumulative Distribution Function

1. It is non decreasing
2. It is right continuous ( RHL exits and is equal to the function values $\lim_{x \to a^+}F(x) = F(a)$)
3. $\lim_{x \to -\infty}F(x) = 0$ and $\lim_{x \to \infty}F(x) = 1$

# Expectation

The expectation of a random variable X is the weighted average of the values that the random variable can take. The weights are given by the probability mass function of the random variable. The expectation of a random variable X is denoted by $E[X]$ or $\mu$.

$$ E[X] = \sum_{x \in X} xP(X = x)$$

$$ E[X] = \int_{-\infty}^{\infty} xf(x)dx$$

## Properties of Expectation

1. $E[aX + b] = aE[X] + b$
2. $E[X + Y] = E[X] + E[Y]$
3. $E[XY] = E[X]E[Y]$ if X and Y are independent
4. $E[g(X)] = \sum_{x \in X} g(x)P(X = x)$
5. $E[g(X)] = \int_{-\infty}^{\infty} g(x)f(x)dx$

# Variance

$$Var(X) = E[(X - E[X])^2]$$

$$Var(X) = E[X^2] - E[X]^2$$

$$ SD(X) = \sqrt{Var(X)}$$

## Properties of Variance
1. $Var(X+a) = Var(X)$
2. $Var(aX) = a^2Var(X)$


## Uniform Distribution

## Universality of Uniform

## Normal Distribution

$$ \boldsymbol{N}(\mu,\sigma) = \frac{1}{\sqrt{2\pi}}\exp\left(-\left(\frac{x-\mu}{\sigma}\right)^2\right)$$

# Joint and Marginal Distribution

## Covariance

$$Cov(X,Y) = E[(X - E[X])(Y - E[Y])]$$

Properties of Covariance:
1. $Cov(X,X) = Var(X)$
2. $Cov(X,Y) = Cov(Y,X)$
3. $Cov(aX + bY, Z) = aCov(X,Z) + bCov(Y,Z)$
4. $Var(X + Y) = Var(X) + Var(Y) + 2Cov(X,Y)$
5. $Var(X_1 + X_2 ...X_n) = Var(X_1) + Var(X_2) ... + Var(X_n) + 2\sum_{i < j}Cov(X_i,X_j)$

## Correlation
If X and Y are two random variables then the correlation between them lies in between -1 to 1 is given by

$$\rho(X,Y) = \frac{Cov(X,Y)}{\sqrt{Var(X)Var(Y)}}$$

## Spearman's Rank Correlation

If X and Y are two random variables then the Spearman's Rank Correlation between them is given by

$$\rho(X,Y) = \frac{Cov(Rank(X),Rank(Y))}{\sqrt{Var(Rank(X))Var(Rank(Y))}}$$

# Central Limit Theorem

If $X_1,X_2...X_n$ are independent and identically distributed random variables with mean $\mu$ and variance $\sigma^2$ then the distribution of $\frac{\sum_{i=1}^n X_i - n\mu}{\sigma\sqrt{n}}$ converges to $N(0,1)$ as n tends to infinity.

# Confidence Interval

# Hypothesis Testing

# Resampling and Permutation Testing


