# Statistical Validity, Type I & II Errors, and Power

The statistical validity of a study is often discussed using a framework called the **confusion matrix**, which outlines the four possible outcomes when comparing a researcher's statistical decision to the unknown true state of Nature.

### The Decision Matrix

|                              | **Model C (Null) is correct** | **Model C (Null) is incorrect** |
|------------------------------|--------------------|----------------------|
| **Reject Model C**           | Type I error       | Correct decision     |
| **Do not reject Model C**    | Correct decision   | Type II error        |

---

## Difference Between Type I and Type II Errors

- **Type I error (α):** Occurs when the null hypothesis (Model C) is rejected, but Model C is actually correct. The probability of making a Type I error is denoted by **α** (the significance level).
- **Type II error (β):** Occurs when the null hypothesis is not rejected when it is actually false. The probability of making a Type II error is denoted by **β**.

---

## Factors That Affect Power in the Linear Model

**Power** is the probability of making the correct decision when the null hypothesis (Model C) is incorrect (i.e., correctly rejecting Model C). It is calculated as `1 - β`.

Four key strategies increase power, each relating directly to the sampling distribution for a parameter estimate:

1. **Reduce Error (Decrease MSE):**
    - *Effect on Power:* Increases power.
    - *How:* Reducing error involves controlling random variation and improving data quality, which narrows the confidence interval for the parameter estimate. Reducing mean square error (MSE) makes for more precise estimates, thus increasing power. Improving the model itself (e.g., by adding relevant predictors) can also reduce error.

2. **Increase the Number of Observations (n):**
    - *Effect on Power:* Increases power.
    - *How:* Increasing sample size makes the sampling distribution narrower (the variance is σ²/n), which means more precise parameter estimates and higher power.

3. **Increase the Significance Level (α):**
    - *Effect on Power:* Increases power.
    - *How:* Raising α (allowing a higher risk of Type I error) simultaneously decreases the probability of a Type II error (β), thus increasing power.

4. **Increase Predictor Variance (s²ₓ):**
    - *Effect on Power:* Increases power.
    - *How:* For slope estimates, greater variance in the predictor variable (X) leads to a smaller confidence interval, which improves power.

---

## Two Approaches to Power Analyses

Power analyses are generally framed in terms of timing:

1. **A Priori Power Analysis (Planning):**
    - Used *before* collecting data to answer "what if" questions.
    - Determines the statistical power to detect an effect of a presumed size, and/or how large a sample is required for a chosen level of power.
    - (Cohen suggested power should be at least .8.)

2. **Post Hoc Power Analysis (Confidence Intervals):**
    - Used *after* analysis.
    - Confidence intervals are used as an alternative way to judge the actual power in terms of parameter estimate precision: *narrow* intervals mean high power, *wide* intervals mean low power.

**How to obtain an appropriate value for true proportional reduction in error (\(\eta^2\)) for power analysis:**
- Use PRE values from similar research
- Use Cohen’s suggested "small," "medium," and "large" effects
- Estimate PRE from guessed/expected parameter values

---

## Problems Associated with Low Power Studies

Studies with low power have several serious issues:

- High risk of making a Type II error (missing true effects)
- Risk of concluding an intervention is ineffective when it actually works
- Waste of time and resources on studies unlikely to find effects, even if real

---

## Why Sample Effect Size Estimates Are Often Too Large in Low Power Studies

- The calculated **proportional reduction in error (PRE)** from a sample is a **biased** estimator of the true proportional reduction in error (\(\eta^2\))—it tends to *overestimate* the true value.
- This bias stems from the least-squares procedure's tendency to "capitalize on chance."
- The effect is larger when sample size (n) is small (i.e., when power is low).
- As a result, in low power studies the observed effect size (PRE) from a sample is likely to be *too large* compared to the true effect size (\(\eta^2\)).

---
