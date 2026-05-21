# The LASSO Method for Variable Selection in the Cox Model

## Robert Tibshirani 1997

Tibshirani's 1997 paper is the main paper for my MATH 284 presentation. The paper extends the lasso idea to Cox proportional hazards regression, so that variable selection and coefficient shrinkage can be performed within the Cox partial likelihood framework.

The central idea is to estimate the Cox regression coefficients under an $L_1$ constraint:

$$
\sum_j |\beta_j| \leq s.
$$

This constraint shrinks coefficients toward zero and can set some coefficients exactly equal to zero. As a result, the method produces a sparse Cox model that is easier to interpret than a full model and often more stable than stepwise selection.

### Key Contributions

* **Extends the lasso to the Cox model:** The paper adapts the lasso from ordinary regression to Cox proportional hazards regression by applying an $L_1$ constraint to the Cox partial likelihood.

* **Combines variable selection and shrinkage:** The method shrinks coefficient estimates toward zero and can set some coefficients exactly equal to zero.

* **Provides an alternative to stepwise selection:** Unlike stepwise methods, which make discrete keep-or-drop decisions, the lasso produces a continuous shrinkage path and tends to be more stable.

* **Keeps the model interpretable:** Since some coefficients are estimated as zero, the final Cox model can be simpler and easier to interpret.

* **Uses only the Cox partial likelihood:** The method does not require specifying the baseline hazard function $\lambda_0(t)$.

* **Discusses data-driven tuning:** The paper proposes using an approximate generalized cross-validation criterion to choose the constraint parameter $s$.

* **Compares lasso with stepwise selection:** Through real examples and simulations, the paper shows that the lasso can have better prediction accuracy and lower variability than stepwise selection.

# Background and Origins

This presentation is centered on **Tibshirani (1997)**. The two background papers are included because they explain where the 1997 paper comes from.

Conceptually, the 1997 paper combines two earlier ideas:

$$
\text{Cox proportional hazards regression}
+
\text{lasso shrinkage and selection}
\longrightarrow
\text{lasso for the Cox model}.
$$

**Cox (1972)** provides the survival-analysis framework: proportional hazards regression, censored failure-time data, and inference through a likelihood that does not require specifying the full baseline hazard.

**Tibshirani (1996)** provides the statistical-learning framework: the lasso, which uses an $L_1$ constraint to shrink coefficients and produce sparse, interpretable models.

# Talks and Interviews

The following videos provide background context on the two main figures behind this presentation: Sir David Cox, whose proportional hazards model is the foundation of modern survival regression, and Robert Tibshirani, who introduced the lasso and later adapted it to the Cox model.

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

# Presentation

Slides coming soon.

A possible presentation outline:

1. Review the Cox proportional hazards model.
2. Explain the variable selection problem in Cox regression.
3. Introduce the original lasso idea.
4. Show how the $L_1$ constraint is applied to the Cox partial likelihood.
5. Discuss computation and tuning.
6. Summarize the examples and simulations.
7. Discuss strengths, limitations, and later extensions.

# Papers

## Main Paper

### Robert Tibshirani 1997

**The LASSO Method for Variable Selection in the Cox Model**

This is the main paper for my presentation. It proposes variable selection and shrinkage in Cox proportional hazards regression by optimizing the Cox partial likelihood under an $L_1$ constraint.

[Open PDF](tibshirani-1997-lasso-cox.pdf)  
<a href="tibshirani-1997-lasso-cox.pdf" download>Download PDF</a>

<details>
<summary>Preview PDF</summary>

<iframe src="tibshirani-1997-lasso-cox.pdf" width="100%" height="650px" style="border: 1px solid #ddd;"></iframe>

</details>

## Background Papers

### D. R. Cox 1972

**Regression Models and Life-Tables**

This paper is the origin of the Cox proportional hazards regression framework. It introduces regression modeling for censored failure-time data using a hazard function with an arbitrary baseline time component and unknown regression coefficients.

[Open PDF](cox-1972-regression-models-and-life-tables.pdf)  
<a href="cox-1972-regression-models-and-life-tables.pdf" download>Download PDF</a>

<details>
<summary>Preview PDF</summary>

<iframe src="cox-1972-regression-models-and-life-tables.pdf" width="100%" height="650px" style="border: 1px solid #ddd;"></iframe>

</details>

### Robert Tibshirani 1996

**Regression Shrinkage and Selection via the Lasso**

This paper is the origin of the lasso method. It introduces least absolute shrinkage and selection for regression, using an $L_1$ constraint to shrink coefficients and set some of them exactly equal to zero.

[Open PDF](tibshirani-1996-lasso.pdf)  
<a href="tibshirani-1996-lasso.pdf" download>Download PDF</a>

<details>
<summary>Preview PDF</summary>

<iframe src="tibshirani-1996-lasso.pdf" width="100%" height="650px" style="border: 1px solid #ddd;"></iframe>

</details>

# Summary

The paper begins with the Cox proportional hazards model:

$$
\lambda(t \mid x) = \lambda_0(t)\exp(x^\top\beta),
$$

where $\lambda_0(t)$ is an unspecified baseline hazard function and $\beta$ represents the covariate effects. The usual Cox estimator maximizes the Cox partial likelihood without specifying the baseline hazard.

The problem is that when there are many covariates, the full Cox model may be unstable and hard to interpret. Stepwise selection is commonly used, but it can be unstable because small changes in the data may lead to different selected models. Ridge regression can shrink coefficients, but it usually does not set coefficients exactly to zero.

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

When the constraint is loose, the estimate is close to the usual Cox partial likelihood estimate. When the constraint is tighter, coefficients are shrunk toward zero, and some coefficients become exactly zero. This gives a sparse Cox model.

A key computational idea is to approximate the Cox partial likelihood problem by an iteratively reweighted least squares problem. At each step, the method solves a constrained weighted least squares problem and then updates the approximation.

The paper also discusses how to choose the constraint parameter $s$. Tibshirani proposes an approximate generalized cross-validation criterion, which balances model fit against an estimate of model complexity.

The overall message is that the lasso is useful for Cox regression because it combines shrinkage, variable selection, and interpretability in one framework.
