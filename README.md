# Rat-Lab-Bayesian-Analysis
Using Bayesian Analysis (Monte Carlo simulation) to understand the difference between tumor genesis in types of mice.

#### Context
A cancer lab is estimating the rate of tumorigenesis in two types of mice. Type A mice have been well studied, and information from other labs indicates that type A mice have tumor counts that are approximately Poisson distributed with a mean of 12, and theta a has a gamma distribution as gamma(120,12). Type B mice tumor counts are unknown distribution.

#### Results
It appears that mice type B have a higher affinity for tumorigenesis than type A (according to our Monte Carlo simulation with gamma prior). Matching the predicted higher tumor count of type B mice in 70% of our simulations (Monte Carlo with Poisson model).  The Poisson model fits the mice type A well. However, it does not fit the type B mice very well and appears to consistently underpredict their standardized tumor count average.
