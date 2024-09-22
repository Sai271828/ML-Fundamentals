# Model Assessment and Selection

**Model Selection:** estimating the performance of different models in order to choose the best one
**Model Assessment:** having chosen a final model, estimating the prediction error on new data

When there is a rich dataset, we can divide the data into train, validation and test. Usually the train data is 50%, validation and the test data are both 25% of the entire dataset.

## Bias-Variance

Assume that we have a model $f$ to predict $Y = f(X) +\epsilon$ where $E(\epsilon) =0$ and $Var(\epsilon) = \sigma_{\epsilon}^2$. The expectation of the prediction error of a regression fit, $\hat{f} (X)$ at a point $X=x_0$, using square loss is
$$
\begin{align*}
Err(x_0) = & E[ ( Y - \hat{f}(X) )^2 | X=x_0 ] \\
 = & \sigma_{\epsilon}^2 + [ E \hat{f} (x_0) - f(x_0) ]^2 + E[ \hat{f}(x_0) - E \hat{f} (x_0) ]^2 \\
 = & \sigma_{\epsilon}^2 + \text{Bias}^2(\hat{f}(x_0)) + \text{Var}(\hat{f}(x_0)) \\
 = & \text{ Irreducible error + Bias}^2 + \text{Variance}

\end{align*}
$$