# Ensemble Models

Ensemble learning often means that we are using a bunch of models working together instead of just one. The idea is to somehow use this to balance bias vs variance tradeoff.

## Bagging
Bagging is short for Bootstrap aggregation. 
Bagging seems to work especially well for high-variance, low-bias procedures, such as decision trees. 
Decision trees are very good at handling both Categorical and numerical data such if blood pressure > 120 and chest pain > 5. 

**Question**: This would usually require normalizing and I still dont know what happens if the distribution is very wierd.
**Question**: What about imbalanced data?
**Question**: How to compute the variance of parameters?

## Advantages of Decision Trees

- **Simple to understand and interpret.** Trees can be visualized.
- **Requires little data preparation.** Other techniques often require data normalization, creating dummy variables, and removing blank values. Some tree and algorithm combinations support missing values.
- **Handles both numerical and categorical data.** However, the scikit-learn implementation does not currently support categorical variables. Other techniques are usually specialized for datasets with only one type of variable.
- **Performs well even when assumptions are violated.** Decision trees perform well even if the true model from which the data were generated does not fully adhere to the tree's assumptions.

## Disadvantages of Decision Trees

- **Prone to overfitting.** Decision-tree learners can create over-complex trees that generalize poorly. Techniques such as pruning, setting a minimum number of samples per leaf, or limiting the maximum tree depth are necessary to avoid this.
- **Unstable.** Small data variations can result in a completely different tree. Using decision trees in an ensemble can mitigate this problem.
- **Predictions are piecewise constant approximations.** Decision trees make predictions that are neither smooth nor continuous, which makes them poor at extrapolation.
- **Learning an optimal tree is NP-complete.** Practical algorithms use heuristics like greedy algorithms, which make locally optimal decisions at each node but may not yield the globally optimal tree. This can be addressed by training multiple trees in an ensemble, using random sampling of features and data points.
- **Hard to learn certain concepts.** Decision trees struggle to represent problems like XOR, parity, or multiplexer.
- **Bias toward dominant classes.** Decision tree learners can create biased trees if some classes dominate the dataset. Balancing the dataset before fitting the tree is recommended.


Moreover, since each tree generated in bagging is identically distributed (i.d.), the expectation of an average of $B$ such trees is the same as the expectation of any one of them. This means the bias of bagged trees is the same as that of the individual (bootstrap) trees, and the only hope of improvement is through variance reduction. This is in contrast to boosting, where the trees are grown in an adaptive way to remove bias, and hence are not i.d.

An average of $B$ i.i.d. random variables, each with variance $\sigma^2$, has variance $\frac{1}{B} \sigma^2$. If the variables are simply i.d. (identically distributed, but not necessarily independent) with positive pairwise correlation $\rho$, the variance of the average is:


$$\rho \sigma^2 + \frac{1 - \rho}{B} \sigma^2. $$

As $B$ increases, the second term disappears, but the first remains, and hence the size of the correlation of pairs of bagged trees limits the benefits of averaging.

**Advantages of Random Forests**
OOB error: See how the randomforests that did not see an observation do on an observation. This errror is in general good for ensemble models.

**Disadvantages of Random Forests**
When the number of variables is large, but the fraction of relevant variables
small, random forests are likely to perform poorly with small m. At each
split the chance can be small that the relevant variables will be selected. Usually Gradient Boosting gets better!





