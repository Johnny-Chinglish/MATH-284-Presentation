# The LASSO Method for Variable Selection in the Cox Model

## Robert Tibshirani, 1997

Tibshirani's 1997 paper is the main paper for my MATH 284 presentation. The paper extends the lasso idea to Cox proportional hazards regression, so that variable selection and coefficient shrinkage can be carried out within the Cox partial likelihood framework.

The central idea is to estimate the Cox regression coefficients under an $L_1$ constraint:

$$
\sum_j |\beta_j| \leq s.
$$

This constraint shrinks coefficients toward zero and can set some coefficients exactly equal to zero. As a result, the method produces a sparse Cox model that is easier to interpret than a full model and often more stable than stepwise selection.

### Key Contributions

* **Extends the lasso to Cox regression:** The paper adapts the lasso to the Cox proportional hazards model by applying an $L_1$ constraint to the Cox partial likelihood.

* **Combines shrinkage and variable selection:** The method shrinks coefficient estimates toward zero and can set some coefficients exactly equal to zero.

* **Produces interpretable sparse models:** Variables with zero coefficients are removed from the fitted Cox model, leading to a simpler final model.

* **Avoids modeling the baseline hazard:** The method works through the Cox partial likelihood, so no parametric form for $\lambda_0(t)$ is required.

* **Provides an alternative to stepwise selection:** The lasso gives a continuous regularization path and can be more stable than discrete stepwise selection procedures.

# Background and Origins

This presentation is centered on **Tibshirani (1997)**. The two background papers are included because they explain where the 1997 Cox lasso paper comes from.

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

# Historical Context: Talks and Interviews

The following videos provide historical context for the two methodological lineages behind this presentation: Cox proportional hazards regression and lasso shrinkage.

<div style="display: grid; grid-template-columns: repeat(auto-fit, minmax(320px, 1fr)); gap: 24px; margin-top: 1rem; margin-bottom: 1rem;">

  <div>
    <p><strong>Sir David Cox</strong></p>
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
    <p><strong>Robert Tibshirani</strong></p>
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

# Presentation Materials

## Presentation Slides

[Open PDF](cox-lasso-1997-slides.pdf)  
<a href="cox-lasso-1997-slides.pdf" download>Download PDF</a>

<iframe src="cox-lasso-1997-slides.pdf" width="100%" height="650px" style="border: 1px solid #ddd;"></iframe>

## Algorithm Handout: Unified Cox Lasso Algorithms

[Open PDF](unified-cox-lasso-algorithms.pdf)  
<a href="unified-cox-lasso-algorithms.pdf" download>Download PDF</a>

<iframe src="unified-cox-lasso-algorithms.pdf" width="100%" height="650px" style="border: 1px solid #ddd;"></iframe>

# Papers

## Main Paper

**Robert Tibshirani (1997). _The LASSO Method for Variable Selection in the Cox Model_.**

This is the main paper for my presentation. It proposes variable selection and shrinkage in Cox proportional hazards regression by optimizing the Cox partial likelihood under an $L_1$ constraint.

[Open PDF](tibshirani-1997-lasso-cox.pdf)  
<a href="tibshirani-1997-lasso-cox.pdf" download>Download PDF</a>

<details>
<summary>Preview PDF</summary>

<iframe src="tibshirani-1997-lasso-cox.pdf" width="100%" height="650px" style="border: 1px solid #ddd;"></iframe>

</details>

## Background Papers

**D. R. Cox (1972). _Regression Models and Life-Tables_.**

This paper is the origin of the Cox proportional hazards regression framework. It introduces regression modeling for censored failure-time data using a hazard function with an arbitrary baseline time component and unknown regression coefficients.

[Open PDF](cox-1972-regression-models-and-life-tables.pdf)  
<a href="cox-1972-regression-models-and-life-tables.pdf" download>Download PDF</a>

<details>
<summary>Preview PDF</summary>

<iframe src="cox-1972-regression-models-and-life-tables.pdf" width="100%" height="650px" style="border: 1px solid #ddd;"></iframe>

</details>

**Robert Tibshirani (1996). _Regression Shrinkage and Selection via the Lasso_.**

This paper is the origin of the lasso method. It introduces least absolute shrinkage and selection for regression, using an $L_1$ constraint to shrink coefficients and set some of them exactly equal to zero.

[Open PDF](tibshirani-1996-lasso.pdf)  
<a href="tibshirani-1996-lasso.pdf" download>Download PDF</a>

<details>
<summary>Preview PDF</summary>

<iframe src="tibshirani-1996-lasso.pdf" width="100%" height="650px" style="border: 1px solid #ddd;"></iframe>

</details>

# Summary and Takeaways

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

The main takeaway is that Tibshirani (1997) turns variable selection in Cox regression into a regularized partial-likelihood problem. The $L_1$ constraint connects classical survival regression with modern penalized regression.

Key takeaways:

* Cox regression provides the survival-analysis framework.
* The lasso provides the shrinkage-and-selection mechanism.
* The Cox lasso combines the two through penalized partial likelihood.
* The resulting model can be sparse, interpretable, and more stable than stepwise selection.
