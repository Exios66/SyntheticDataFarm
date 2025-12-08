# Generalized Linear Models (GLM) for Categorical Outcomes

The **generalized linear model (GLM)** is used for cases where the dependent variable is categorical, particularly when it is **dichotomous** (i.e., only two possible outcome values). Standard least-squares regression is inappropriate for categorical outcomes because:

- Predicted values can be outside the valid range (e.g., getting 0.74 or 1.22 when outcome can only be 0 or 1).
- Errors are not normally distributed, violating core regression assumptions.

GLMs are also helpful when normality or constant variance assumptions are systematically violated (e.g., with count data), and alternative models like Poisson regression are preferable.

---

## Logit Link Function and Binomial Distribution

When your outcome is dichotomous, use a GLM with the **logit link** and **binomial distribution**. Instead of predicting category labels directly, you model the **probability (or odds)** of one outcome. This is called **logistic regression**.

---

## Log Link Function and Poisson Distribution

A **Poisson GLM** with a **log link** is used for modeling **count data**, especially when the distribution is thick-tailed or normality assumptions do not hold. Least-squares regression coefficients may be unbiased but inefficient for such data, so the log-link Poisson model is preferred.

---

## Odds and Probability Calculations

Logistic regression uses transformations among probabilities, odds, and logits:

1. **Probability ($p$) to Odds:**
   $$
   \text{Odds} = \frac{p}{1-p}
   $$

2. **Odds to Probability:**
   $$
   \hat{p} = \frac{\text{Odds}}{1 + \text{Odds}}
   $$

3. **Model Log-Odds (Logit) from Model:**
   The predicted log-odds (logit) comes from the linear model:
   $$
   \text{logit}_i = b_0 + b_1 X_i
   $$
   Or, equivalently, the logit is defined as:
   $$
   \text{logit} = \log(\text{Odds})
   $$

4. **Logit to Odds:**
   $$
   \text{Odds} = e^{\text{logit}}
   $$

---

## Odds Ratio and Interpretation

An **odds ratio** is simply a ratio of two odds.

- **Categorical Predictor:** The odds ratio tells you how many times more likely the outcome is in one group vs. a reference group.  
  Example: If the odds ratio for tap water vs. bottled water is 6.12, then tap water drinkers are **6.12 times more likely** to become sick.

- **Quantitative Predictor:** The odds ratio for a one-unit predictor increase is $e^{b_j}$.  
  Example: If $b_j = 1.33$, the odds increase by $e^{1.33} \approx 3.78$ for each unit of the predictor.

Odds ratios are the preferred effect size in logistic regression because predictors have a **multiplicative effect** on the odds: each unit increase multiplies the odds by a constant factor.

---

## Visualizing Logistic Regression: Probability Curves

In logistic regression, the relationship between a predictor ($X$) and the predicted probability ($\hat{p}$) of an outcome is **non-linear** (an S-shaped or sigmoid curve):

- **Intercept ($b_0$):**  
  Controls the probability when $X = 0$ (or when $X$ is centered, when $X$ is at its mean).  
  A more positive $b_0$ shifts the curve up (higher probabilities when $X$ is zero).

- **Slope ($b_1$):**  
  Controls the steepness of the S-curve. Larger $|b_1|$ means probability moves rapidly from 0 to 1 as $X$ increases.

---

## Approaches to Testing Parameter Estimates in Logistic Regression

Three main approaches:

1. **Model Comparison (Deviance Difference):**
   - Compare the deviance (DEV) of a full model (A) to a nested (compact) model (C).
   - The difference $DEV(C) - DEV(A)$ is approximately chi-square ($\chi^2$) distributed, with degrees of freedom equal to the difference in the number of parameters ($P_A - P_C$).

2. **Wald Chi-square Test:**
   - Compute $\left(\frac{b_j}{s_{b_j}}\right)^2$, where $b_j$ is the coefficient and $s_{b_j}$ its standard error.

3. **Confidence Interval Approach:**
   - Check if the confidence interval for $b_j$ includes 0, or if the interval for the odds ratio includes 1.

**Note:** Model comparison by deviance difference (Approach 1) is the fundamental way to assess the value of additional predictors in logistic regression—analogous to comparing sums of squared errors in least-squares regression.

---

## Handling Categorical and Multiple Predictors

- **Categorical Predictors:**  
  Code categorical predictors (e.g., with contrast or dummy codes), just as in least-squares regression. Using a full set of codes allows each cell's predicted probability to be estimated.

- **Multiple Predictors:**  
  Multiple predictors (continuous, categorical, interactions) can be included, as in multiple regression. Model comparisons based on deviance differences are used to determine if the addition of predictors improves the model.
