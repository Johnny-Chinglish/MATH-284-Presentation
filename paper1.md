# The LASSO Method for Variable Selection in the Cox Model

## Robert Tibshirani 1997

Tibshirani's paper extends the lasso idea from linear regression to Cox proportional hazards regression. The goal is to perform variable selection and coefficient shrinkage at the same time for right-censored survival data.

The main proposal is to estimate the Cox regression coefficients by optimizing the Cox partial likelihood subject to an $L_1$ constraint:

$$
\sum_j |\beta_j| \leq s.
$$

Because of the geometry of this constraint, the method can shrink some coefficients exactly to zero. This gives a sparse Cox model: variables with nonzero coefficients are selected, while variables with zero coefficients are removed from the model.

### Key Contributions

* **Extends the lasso to the Cox model:** The paper adapts the lasso from ordinary regression to Cox proportional hazards regression by applying an $L_1$ constraint to the Cox partial likelihood.

* **Combines variable selection and shrinkage:** The method shrinks coefficient estimates toward zero and can set some coefficients exactly equal to zero.

* **Provides an alternative to stepwise selection:** Unlike stepwise methods, which make discrete keep-or-drop decisions, the lasso produces a continuous shrinkage path and tends to be more stable.

* **Keeps the model interpretable:** Since some coefficients are estimated as zero, the final Cox model can be simpler and easier to interpret.

* **Uses only the Cox partial likelihood:** The method does not require specifying the baseline hazard function $\lambda_0(t)$.

* **Discusses data-driven tuning:** The paper proposes using an approximate generalized cross-validation criterion to choose the constraint parameter $s$.

* **Compares lasso with stepwise selection:** Through real examples and simulations, the paper shows that the lasso can have better prediction accuracy and lower variability than stepwise selection.

# Conversation with Sir David Cox & Robert Tibshirani

<div style="display: grid; grid-template-columns: repeat(auto-fit, minmax(320px, 1fr)); gap: 24px; margin-top: 1rem; margin-bottom: 1rem;">

  <div>
    <h3>Sir David Cox</h3>
    <div style="position: relative; padding-bottom: 56.25%; height: 0; overflow: hidden;">
      <iframe
        src="https://www.youtube.com/embed/TiHCNRUiLKc?start=327"
        title="Conversation with Sir David Cox"
        style="position: absolute; top: 0; left: 0; width: 100%; height: 100%; border: 0;"
        allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share"
        allowfullscreen>
      </iframe>
    </div>
    <p>
      <a href="https://www.youtube.com/watch?v=TiHCNRUiLKc&t=327s" target="_blank">
        Watch on YouTube
      </a>
    </p>
  </div>

  <div>
    <h3>Robert Tibshirani</h3>
    <div style="position: relative; padding-bottom: 56.25%; height: 0; overflow: hidden;">
      <iframe
        src="https://www.youtube.com/embed/3rvl4KV41JE"
        title="Conversation with Robert Tibshirani"
        style="position: absolute; top: 0; left: 0; width: 100%; height: 100%; border: 0;"
        allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share"
        allowfullscreen>
      </iframe>
    </div>
    <p>
      <a href="https://www.youtube.com/watch?v=3rvl4KV41JE" target="_blank">
        Watch on YouTube
      </a>
    </p>
  </div>

</div>

# Summary

The paper begins with the usual Cox proportional hazards model:

$$
\lambda(t \mid x) = \lambda_0(t)\exp(x^\top\beta),
$$

where $\lambda_0(t)$ is an unspecified baseline hazard function and $\beta$ is the vector of regression coefficients. In the standard Cox model, $\beta$ is estimated by maximizing the Cox partial likelihood.

When there are many covariates, however, the full Cox model may be unstable or hard to interpret. Stepwise selection is often used in practice, but it can be unstable because small changes in the data may lead to different selected models. Ridge regression can shrink coefficients, but it generally does not set coefficients exactly equal to zero.

Tibshirani proposes a lasso version of the Cox model. In modern notation, the estimator can be written as

$$
\widehat{\beta}(s)
=
\arg\min_{\beta}
\{-\ell(\beta)\}
\quad
\text{subject to}
\quad
\sum_j |\beta_j| \leq s,
$$

where $\ell(\beta)$ is the Cox partial log-likelihood and $s$ controls the amount of shrinkage.

Equivalently, the method can be written in penalized form as

$$
\widehat{\beta}(\lambda)
=
\arg\min_{\beta}
\left[
-\ell(\beta)
+
\lambda \sum_j |\beta_j|
\right].
$$

The tuning parameter controls the tradeoff between model fit and model simplicity. When the constraint is loose, the estimate is close to the usual Cox partial likelihood estimate. When the constraint is tighter, the coefficients are shrunk toward zero, and some coefficients become exactly zero.

A key computational idea is to approximate the Cox partial likelihood problem by an iteratively reweighted least squares problem. At each step, the method solves a constrained weighted least squares problem, then updates the approximation until the estimates stabilize.

The paper also discusses how to choose the constraint parameter $s$. Tibshirani proposes an approximate generalized cross-validation criterion, which balances the fit of the model against an estimate of model complexity.

The examples and simulations compare the lasso with full Cox regression and stepwise selection. In the lung cancer example, the lasso identifies Karnofsky score as the dominant predictor. In the primary biliary cirrhosis example, the lasso shrinks many weak effects while retaining stronger ones. In simulations, the lasso performs especially well when there are a few large effects or many small effects, often giving lower mean squared error than stepwise selection.

The paper's overall message is that the lasso is a useful model selection tool for Cox regression because it combines shrinkage, variable selection, and interpretability in one framework.

# Presentation

Slides coming soon.

A possible presentation outline:

1. Review the Cox proportional hazards model.
2. Explain why variable selection is difficult in survival analysis.
3. Introduce the lasso idea.
4. Show how the $L_1$ constraint is applied to the Cox partial likelihood.
5. Discuss the computational algorithm.
6. Explain how the tuning parameter $s$ is selected.
7. Summarize the real data examples.
8. Summarize the simulation results.
9. Discuss strengths, limitations, and later extensions.

# Paper

The following papers are listed in the order I plan to discuss them.

## Robert Tibshirani 1997

**The LASSO Method for Variable Selection in the Cox Model**

[Open PDF](tibshirani-1997-lasso-cox.pdf)  
<a href="tibshirani-1997-lasso-cox.pdf" download>Download PDF</a>

<iframe src="tibshirani-1997-lasso-cox.pdf" width="100%" height="650px" style="border: 1px solid #ddd;"></iframe>

## D. R. Cox 1972

**Regression Models and Life-Tables**

[Open PDF](cox-1972-regression-models-and-life-tables.pdf)  
<a href="cox-1972-regression-models-and-life-tables.pdf" download>Download PDF</a>

<iframe src="cox-1972-regression-models-and-life-tables.pdf" width="100%" height="650px" style="border: 1px solid #ddd;"></iframe>

## Robert Tibshirani 1996

**Regression Shrinkage and Selection via the Lasso**

[Open PDF](tibshirani-1996-lasso.pdf)  
<a href="tibshirani-1996-lasso.pdf" download>Download PDF</a>

<iframe src="tibshirani-1996-lasso.pdf" width="100%" height="650px" style="border: 1px solid #ddd;"></iframe>

# Notes

Important points to remember:

* The lasso is useful when we want a Cox model that is both predictive and interpretable.
* The $L_1$ constraint is what allows exact zero coefficients.
* Standardization of covariates is important, because the penalty should treat variables fairly.
* The method should be used together with usual survival model checking, including checking linearity and the proportional hazards assumption.
* The paper focuses on fixed covariates, but the author notes that time-dependent covariates can also be incorporated.
