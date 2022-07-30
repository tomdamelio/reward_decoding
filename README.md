
2022 NMA project on [Steinmetz dataset](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC6913580/)

# Global and local functional connectivity properties: a reward predictive model approach

Reward coding was extensively studied at the level of single cells in dopaminergic systems, mainly in:
- midbrain (e.g. VTA)
- basal ganglia (e.g. Striatum)

However, several studies have shown that distributed patterns of functional connectivity could represent diverse cognitive phenomena.  

## Questions

*Q1:* Is it possible to predict reward through topological properties of functional connectivity?

*Q2:* Which topological properties (global vs. local patterns) best explain reward predictions?


[INSERTAR IMAGEN REWARD AND NON REWARD]

Figure 1. Example of the functional connectivity of a mouse session according to reward and non-reward conditions (Steinmetz et al, 2019) 


Threee reward classification models (Ridge logistic regression, 5-Fold-CV) were implemented to describe the reward phenomenon.
- Model 1:

[![\\ log(\frac{P(Reward)}{1-P(Reward)}) = \beta_0 + \beta_1X_1 + \beta_2X_2 ... + \beta_{14}X_{14} + \beta_{15}X_{15} + \beta_{16}X_{16} + ... + \beta_{30}X_{30}](https://latex.codecogs.com/svg.latex?%5C%5C%20log(%5Cfrac%7BP(Reward)%7D%7B1-P(Reward)%7D)%20%3D%20%5Cbeta_0%20%2B%20%5Cbeta_1X_1%20%2B%20%5Cbeta_2X_2%20...%20%2B%20%5Cbeta_%7B14%7DX_%7B14%7D%20%2B%20%5Cbeta_%7B15%7DX_%7B15%7D%20%2B%20%5Cbeta_%7B16%7DX_%7B16%7D%20%2B%20...%20%2B%20%5Cbeta_%7B30%7DX_%7B30%7D)](#_)- Model 2:

- Model 3:


It was expected that this model will perform significantly better than chance. As a consequence, we hypothesized that higher values in the centrality of nodes belonging to midbrain structures will be associated with an increase in the probability of reward classification.

We analyzed the spikes related to the presentation of the reward and non-reward from a database from Steinmetz laboratory (2019).We evaluated seven sessions of 39 neuropixel recordings of 400 to 700 neurons from the whole mouse brain during a visual behavioral task. From this data, global and local topological properties of the functional connectivity between neurons (e.g. mean geodesic distance of the whole network and midbrain nodes’ centrality, respectively) were computed. These properties were used as predictors for a reward binary classification logistic regression model. As results, we observed a differentiated topological structure between both conditions, presenting an enhancement centrality of midrabin nodes after a reward presentation.
