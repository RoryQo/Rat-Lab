# Rat Lab Bayesian Analysis 
  
## Table of Contents
1. [Overview](#overview)
2. [Results](#results)
3. [Analysis Methodology](#analysis-methodology)
4. [Data and Simulation](#data-and-simulation)
5. [Findings](#findings)
6. [Model Evaluation](#model-evaluation)

## Overview
A cancer lab is investigating the rate of tumorigenesis in two types of mice. Type A mice have been extensively studied, and existing data suggests that their tumor counts follow a Poisson distribution with a mean of 12. The parameter $\theta_A\$ follows a gamma distribution defined as gamma(120, 12). In contrast, the distribution of tumor counts for Type B mice is unknown.

## Results
The analysis indicates that Type B mice exhibit a higher affinity for tumorigenesis compared to Type A mice. This conclusion is supported by Monte Carlo simulations, where Type B mice had predicted higher tumor counts in 70% of the simulations. While the Poisson model effectively fits the tumor count data for Type A, it underpredicts the standardized tumor counts for Type B mice.

## Analysis Methodology
Bayesian analysis was employed, utilizing Monte Carlo simulations to estimate the tumorigenesis rates. We compared the tumor counts between the two mouse types by generating samples from their respective posterior distributions.

```{r}
# Theta_a_mont and theta_b_mont from above
# select 1000 random samples from a poisson distribution with the thetas calculated from previous monte carlo simulation

y_a_mont <- rpois(1000, theta_a_mont)
y_b_mont <- rpois(1000, theta_b_mont)


# Print probability
cat("P(theta_b < theta_a | y_a, y_b) =",mean(y_a_mont > y_b_mont))
```

## Data and Simulation
The data includes tumor counts for both mouse types:
- **Type A:** 10 samples with counts: [12, 9, 12, 14, 13, 13, 15, 8, 15, 6]
- **Type B:** 13 samples with counts: [11, 11, 10, 9, 9, 8, 7, 10, 6, 8, 8, 9, 7]

The analysis included prior distributions based on previous studies and conducted Monte Carlo simulations to estimate the tumor counts.

## Findings
### Probability of Tumorigenesis Affinity
Using Monte Carlo simulations, we assessed the probability that the tumorigenesis affinity $\theta_A\$ is higher than $\theta_B\$:
- There is a strong probability that $\theta_A\$ exceeds $\theta_B\$ based on the simulations.

### Effect of Sample Size
For varying values of $n_0\$, we evaluated the probability that $\theta_B < \theta_A\$:
- As $n_0\$ increases, the probability that $\theta_A\$ is greater than $\theta_B\$ decreases, demonstrating that conclusions are relatively stable against prior assumptions.

### Comparison of Posterior Distributions
We also examined the probability that the samples $\tilde{Y_B} < \tilde{Y_A}\$ from the posterior distributions:
- Similar to previous findings, as n_0 increases, the probability decreases, indicating a sensitivity to the prior.

## Model Evaluation
### Type A Mice
The Poisson model fits the tumor counts for Type A mice well, as evidenced by the observed statistics closely aligning with the model's predicted values.

<img src="https://github.com/RoryQo/R-Rat-Lab/raw/main/Graph1.jpg" alt="Rat Lab Graph" style="width: 400px;" />


### Type B Mice
For Type B mice, the Poisson model does not provide a good fit; the observed statistics deviate significantly from the model's predictions, indicating a need for further investigation into the distribution of tumor counts in this group.

<img src="https://raw.githubusercontent.com/RoryQo/R-Rat-Lab/main/graph2.jpg" alt="Graph Image" width="400" />

