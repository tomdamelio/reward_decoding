
2022 NMA project on [Steinmetz dataset](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC6913580/) by:
- Juan Camilo Higuera Calderon
- Thaiz Priscilla Sánchez Costa
- Camilo Berutti
- Joel Angel Gonzales Flores
- Luis Felipe Sarmiento Rivera
- Tomas D'Amelio 

# Global and local functional connectivity properties: a reward predictive model approach

Reward coding was extensively studied at the level of single cells in dopaminergic systems, mainly in:
- **midbrain** (e.g. VTA)
- **basal ganglia** (e.g. Striatum)

However, several studies have shown that distributed patterns of functional connectivity could represent diverse cognitive phenomena.  

## Questions

**Q1:** Is it possible to predict reward through topological properties of functional connectivity?

**Q2:** Which topological properties (global vs. local patterns) best explain reward predictions?

![image](https://user-images.githubusercontent.com/79924152/181863019-feb89509-f7a8-4a72-9c12-6c6dab9b890a.png)

**Figure 1.** Example of the functional connectivity of one mouse session according to reward and non-reward conditions.


## Hypothesis

- Model 1 (logistic regression trained with local and global connectivity variables) would perform significantly better than chance.
- Higher values in the centrality of nodes belonging to midbrain structures will be associated with an increase in the probability of reward classification.

## Methods

We analyzed the spikes related to the presentation of the reward and non-reward from a database from Steinmetz (2019). We evaluated seven sessions of 39 neuropixel recordings of 400 to 700 neurons from the whole mouse brain during a visual behavioral task. From this data, global and local topological properties of the functional connectivity between neurons (e.g. mean geodesic distance of the whole network and midbrain nodes’ centrality, respectively) were computed. These properties were used as predictors for a reward binary classification logistic regression model. 

### Models

Threee reward classification models (Ridge logistic regression, 5-Fold-CV) were implemented to describe the reward phenomenon (to see how we've implemented these models, see `Model_implementation.ipynb` file).
- Model 1: Model trained with **all features**
![image](https://user-images.githubusercontent.com/79924152/181862736-5ac5c900-ffb7-4c2f-8ec0-d77d763c7852.png)

- Model 2: Model trained with **global features** (e.g. mean degree whole-brain network)
![image](https://user-images.githubusercontent.com/79924152/181862831-95453344-79ca-4825-bc1b-d3bb7b6f329b.png)

- Model 3: Model tained with **local features** (e.g. mean degree midbrain nodes)
![image](https://user-images.githubusercontent.com/79924152/181862838-6df2e601-f8ac-4e03-8337-b145200811d4.png)

## Results
Both models trained with local and global variables achieved significant performance (_p_ < 0.001), according to a permutation analysis performed (_n_ permutations = 10000)
![image](https://user-images.githubusercontent.com/79924152/181863040-2887b222-990d-460b-a8db-0d96543f871a.png)
**Figure 2.** Permutation analysis for model trained with local and global variables. Red dot line represents the perfromance achieved by ouy model, while in blue it is represented the distribution of the accuracies from permuted data

![image](https://user-images.githubusercontent.com/79924152/181863222-6ac93a4c-499a-4706-af71-d3742451f3fd.png)
**Figure3.**  Forest plot in which it is represented 95% Confidence intervals of the logistic regression coefficients. In the x axis it is represented the CI. The more extreme this values, the better the predictors. Significant coefficients are shown in light blue.

By inspecting these coefficient it is possible to see, for example, that the mean degree of the network is positively associated with a higher probability of reward, and on the contrary the mean strenght has a negative coefficient. That is to say that when there is a reward, although the number of connections between the network nodes is higher, the strength of these correlations between spikes is lower.
At the local level,  we found that again the average degree and strength is predictive but in the opposite way to what we saw at the global level:  while the average degree of midbrain and basal ganglia have negative values, the average strength has positive association with reward. 
From this, we got mainly two conclusions:
1. Both local and global predictors are useful to explain and predict the reward. 
2. At the local level, in the midbrain and basal ganglia nodes, we found opposite topological properties to what we found at the global level, which could indicate a differential processing of these nodes during reward.

![image](https://user-images.githubusercontent.com/79924152/181863316-5559c28a-1825-44a7-bea8-11c946969d74.png)

**Figure 4.** Cross-validated accuracies by type of model ("local", "global" or "local+global").

We could observe that there would be no difference between the performance of the models that had only local variables or only local variables. However, the model trained with both types of varibels achieved a worse perormance. Is it possible that this is due to the *curse of dimensionality*?



