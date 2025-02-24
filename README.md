# <div align="center">Mice Types Tumorgenesis Propensity</div>  
    
    
<table align="center">
  <tr>
    <td colspan="2" align="center"><strong>Table of Contents</strong></td> 
  </tr>
  <tr>
    <td>1. <a href="#overview">Overview</a></td>
    <td>4. <a href="#data-and-simulation">Data and Simulation</a></td>
  </tr>
  <tr>
    <td>2. <a href="#results">Results</a></td>
    <td>5. <a href="#findings">Findings</a></td>
  </tr>
  <tr>
    <td>3. <a href="#analysis-methodology">Analysis Methodology</a></td>
    <td>6. <a href="#model-evaluation">Model Evaluation</a></td>
  </tr>
</table>


## Overview
A cancer lab is investigating the rate of tumorigenesis in two types of mice. Type A mice have been extensively studied, and existing data suggests that their tumor counts follow a Poisson distribution with a mean of 12. The parameter $\theta_A\$ follows a gamma distribution defined as gamma(120, 12). In contrast, the distribution of tumor counts for Type B mice is unknown.

## Results

The results from our analysis provide compelling evidence of a significant difference between Type A and Type B mice in terms of their tumorigenesis rates.

- **Type B Mice** exhibit a higher affinity for tumorigenesis when compared to Type A mice. This was confirmed through extensive Monte Carlo simulations, where Type B mice were shown to have higher predicted tumor counts in 70% of the simulations.
  
- **Poisson Model Fit**: The Poisson model, which is effective for Type A mice, underpredicts the standardized tumor counts for Type B mice. This discrepancy suggests that the Poisson model is not suitable for Type B, leading to the use of the model as a **lower boundary** for the tumorigenesis propensity of Type B mice. Even when treating the Poisson model as a conservative estimate, the simulations show a **stronger propensity for tumorigenesis in Type B mice** compared to Type A.

- **Implication**: This result underscores that Type B mice have a **significantly higher propensity** for developing tumors, a distinction that becomes clearer as we treat the Poisson model as a lower bound for their tumor rates.


## Analysis Methodology

The study employed **Bayesian analysis** in combination with **Monte Carlo simulations** to estimate and compare the tumorigenesis rates between the two mouse types. The goal was to generate posterior distributions for each type of mouse based on the observed tumor count data.

### Steps Involved:
1. **Monte Carlo Simulation**: We used the results from prior distributions and conducted simulations to generate a range of tumor counts for both mouse types.
2. **Comparison of Posterior Distributions**: We compared the tumor count distributions between Type A and Type B mice, providing a statistical foundation to determine which group has a higher tumorigenesis propensity.


## Data and Simulation

The data for this study includes tumor counts from both mouse types, obtained through experimental observations.

- **Type A Tumor Counts**: 10 samples with counts: [12, 9, 12, 14, 13, 13, 15, 8, 15, 6]
- **Type B Tumor Counts**: 13 samples with counts: [11, 11, 10, 9, 9, 8, 7, 10, 6, 8, 8, 9, 7]

### Approach:
- **Prior Distributions**: Prior distributions were derived based on existing research data for Type A mice, while Type B data were used to derive posterior distributions.
- **Monte Carlo Simulations**: These were conducted to estimate the tumor counts and generate relevant posterior distributions for both mouse types.

```{r}
# Theta_a_mont and theta_b_mont from above
# select 1000 random samples from a poisson distribution with the thetas calculated from previous monte carlo simulation

y_a_mont <- rpois(1000, theta_a_mont)
y_b_mont <- rpois(1000, theta_b_mont)


# Print probability
cat("P(theta_b < theta_a | y_a, y_b) =",mean(y_a_mont > y_b_mont))
```

## Findings

### Probability of Tumorigenesis Affinity
The Monte Carlo simulations revealed a strong probability that the tumorigenesis affinity of Type A mice, $\theta_A$, is higher than that of Type B mice, $\theta_B$. This was based on the comparison of the posterior distributions derived from the simulation.

- The simulation results suggest that, in general, Type B mice show a higher tendency for tumor development, even with the conservative estimate provided by the Poisson model for Type B.

### Effect of Sample Size on Tumorigenesis Probability
In further analysis, we explored the effect of varying sample sizes, $n_0$, on the probability of Type B mice having a higher tumor count than Type A mice.

- **Increasing Sample Size**: As $n_0$ increases, the probability that $\theta_A$ exceeds $\theta_B$ decreases, making the conclusions more stable and less sensitive to prior assumptions.
  
### Comparison of Posterior Distributions
By comparing the posterior distributions of tumor counts for Type A and Type B, we assessed the probability that samples from Type B have fewer tumors than samples from Type A. 

- As expected, larger sample sizes lead to a stronger differentiation between the two types, reinforcing the conclusion that Type B mice have a significantly higher tumorigenesis rate.

## Model Evaluation

### Type A Mice
The Poisson model fits the tumor count data for Type A mice well. The observed tumor count statistics closely match the predictions of the Poisson model, suggesting that the model accurately represents the tumor distribution for Type A.

<img src="https://github.com/RoryQo/R-Rat-Lab/raw/main/Figures/Graph1.jpg" alt="Rat Lab Graph" style="width: 400px;" />

### Type B Mice
For Type B mice, the Poisson model does not provide a good fit. The observed tumor count statistics deviate significantly from the model's predictions. This discrepancy suggests that Type B mice require a more complex model or a different distribution to accurately represent their tumor count data.

<img src="https://raw.githubusercontent.com/RoryQo/R-Rat-Lab/main/Figures/graph2.jpg" alt="Graph Image" width="400" />

