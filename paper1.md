# The LASSO Method for Variable Selection in the Cox Model

## Robert Tibshirani 1997

Tibshirani’s 1997 paper addresses the problem of variable selection in Cox proportional hazards regression, a central model for right-censored survival data. In many biomedical and survival studies, researchers may collect a moderately large set of covariates, but fitting a full Cox model can lead to unstable estimates, high variance, and poor interpretability.

The primary objective of the paper is to adapt the lasso idea to the Cox model by combining variable selection and coefficient shrinkage in a single penalized partial likelihood framework. Instead of using stepwise selection, the method constrains the sum of the absolute values of the Cox regression coefficients:

$$
\sum_j |\beta_j| \le s.
$$

Because of this \(L_1\) constraint, the method shrinks coefficient estimates toward zero and sets some coefficients exactly equal to zero. This produces a simpler, more interpretable Cox model while also reducing estimation variance.

---

## Key Contributions

### Extension of the LASSO to the Cox Model

The paper extends the lasso method, originally developed for linear regression, to Cox proportional hazards regression. The Cox model has the form

$$
\lambda(t \mid x) = \lambda_0(t)\exp(x^\top\beta),
$$

where \(\lambda_0(t)\) is the unspecified baseline hazard and \(\beta\) represents covariate effects. Tibshirani’s method applies an \(L_1\) constraint to the Cox partial likelihood, allowing variable selection without specifying the baseline hazard.

### Variable Selection and Shrinkage in One Framework

Unlike traditional stepwise selection, the Cox lasso performs selection and estimation at the same time. The \(L_1\) constraint shrinks all coefficients and can force some of them to become exactly zero. As a result, the final model can be both sparse and more stable than a full Cox model.

### Alternative to Stepwise Selection

A major motivation of the paper is to provide an alternative to stepwise selection. Stepwise methods make discrete decisions about whether variables enter or leave the model and can be unstable across samples. They may also inflate the apparent importance of selected variables. The lasso instead moves along a continuous shrinkage path, producing a more regularized approach to model selection.

### Penalized Partial Likelihood

The proposed estimator can be written as

$$
\widehat{\beta}(s)
=
\arg\max_{\beta} \ell(\beta)
\quad
\text{subject to}
\quad
\sum_j |\beta_j| \le s,
$$

or equivalently,

$$
\widehat{\beta}(\lambda)
=
\arg\min_{\beta}
\left\{
-\ell(\beta) + \lambda \sum_j |\beta_j|
\right\},
$$

where \(\ell(\beta)\) is the Cox partial log-likelihood. This connects the classical Cox model to modern penalized regression.

# Conversation with Robert Tibshirani

<!-- Interview or related background material will be added here. -->

# Summary

<!-- Summary will be added here. -->

# Presentation

<!-- Presentation slides will be added here. -->

# Paper

<!-- Paper link or PDF will be added here. -->

Download links for the summary, presentation, and paper will be added here later.
