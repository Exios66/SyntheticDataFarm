# Unit 10-12 – Interactions

---

## What is an interaction?

An **interaction** occurs when the effect of one predictor variable on the dependent variable (DV) **is not constant** across all values or levels of another predictor variable. In other words, an interaction between two variables (X₁ and X₂) exists whenever the slope or "simple effect" of one variable depends on the value of the other variable.

---

## How do you create a regressor to test for an interaction between predictors?

To allow for changing slopes, create a **product variable** (the product of the two predictors) and include it as an additional regressor in your model.

- **Two quantitative (continuous) predictors (X₁ and X₂):**  
  The interaction regressor is simply the product X₁ × X₂.  
  *In code:* use `X1:X2` or `X1*X2` (the latter implicitly adds main effects and their interaction).

  ```r
  # Example in R with two continuous predictors
  lm(Y ~ X1 * X2, data = mydata)
  # OR, equivalently (if you want to make it explicit):
  mydata$X1X2 <- mydata$X1 * mydata$X2
  lm(Y ~ X1 + X2 + X1X2, data = mydata)
  ```

- **Two categorical predictors:**  
  The interaction regressor is the product of the **contrast codes** (λ values) for each predictor.

  ```r
  # Suppose groupA and groupB have contrast codes
  # e.g., coded ±0.5
  mydata$groupA_code <- ifelse(mydata$groupA == "A2", 0.5, -0.5)
  mydata$groupB_code <- ifelse(mydata$groupB == "B2", 0.5, -0.5)
  mydata$interaction <- mydata$groupA_code * mydata$groupB_code
  lm(Y ~ groupA_code * groupB_code, data = mydata)
  ```

- **One quantitative and one categorical predictor:**  
  Multiply the quantitative predictor by the contrast code defined for the categorical predictor.

  ```r
  # For categorical coded as ±0.5:
  mydata$interaction <- mydata$X * mydata$G_code
  lm(Y ~ X * G_code, data = mydata)
  ```

---

## How do you interpret the parameter estimates for a model with an interaction?

Given a model:  
**Y = b₀ + b₁X₁ + b₂X₂ + b₃X₁X₂**

- **Interaction Coefficient (b₃):**  
  Indicates how the simple effect (slope) of **each** predictor changes for a one-unit increase on the other predictor. (Symmetric in both predictors.)

- **Component Coefficients (b₁ and b₂):**  
  Each component coefficient estimates the "simple" effect of that variable when the other predictor equals zero.

- **Intercept (b₀):**  
  The predicted outcome when all predictors (and their interaction) are zero.

### *Interpretation differences based on predictor type:*

- **Quantitative–Quantitative:**  
  - b₁ is the simple slope of X₁ when X₂ = 0.  
  - b₃ quantifies the change in X₁'s slope for each one-unit increase in X₂.
- **Categorical–Categorical:**  
  - Main and interaction effects measure differences between cell means (difference of differences).
- **Quantitative–Categorical:**  
  - The categorical parameter estimates mean difference at the zero value of the continuous predictor;  
  - The continuous component estimates simple slope for the reference group (or where categorical = 0);  
  - b₃ shows how the continuous slope changes across categorical groups.

---

## Which parameter estimates change when you rescale predictors in an interaction model?

- **Interaction coefficient (b₃):**  
  **Does not change** when centering or rescaling predictors, provided the main-effects terms are also in the model.
- **Main-effect coefficients (b₁, b₂):**  
  **Do change**, because they estimate the effect when the other predictor is zero—which changes when you center.
- **Intercept (b₀):**  
  **Changes**, as it is the outcome when all predictors are zero.

---

## Describing how the effect of one X changes depending on a second X

In a model:

```r
# General interaction model
Y = [b₀ + b₂*X_Mod] + [b₁ + b₃*X_Mod]*X_Focal
# The simple slope of the focal variable:
# b₁ + b₃ × X_Mod
```

- The **simple slope** of the focal variable is:  
  **b₁ + b₃ × X_Mod**

**Examples:**

- *Quant-Quant:*  
  - E.g., If BC = –1.0 + 6.0×Att + 1.0×PP – 1.0×Att×PP,  
    Simple slope of Att = 6.0 + (–1.0 × PP)

  ```r
  # Suppose PP = 2 for a given case:
  simple_slope_Att <- 6.0 + (-1.0 * 2)  # = 4.0
  ```

- *Dichotomous–Dichotomous:*  
  - b₃ tells you how the mean difference coded by one factor (contrast code λ₁) changes with the other (λ₂).

- *Quant–Categorical:*  
  - Simple slope for the quantitative predictor changes between categorical groups (b₃ quantifies this change).

---

## How do parameter estimates change if you rescale a predictor?

Suppose you recenter predictor X₂ to X₂′ = X₂ – c:

- Substitute X₂ = X₂′ + c into the original model.
- The **interaction coefficient (b₃):** remains unchanged.
- The **main effect for X₁:**  
  New coefficient = original b₁ + b₃ × c  
  (That is, it's the simple effect of X₁ at X₂ = c).
- The **intercept:**  
  New intercept = b₀ + b₂ × c + b₃ × 0 (if centering on X₂ only).
- For **categorical predictors**:  
  If contrast code scaling changes (e.g., ±1 → ±0.5), the coefficient scales in proportion to the sum of squared codes.

  ```r
  # Example: Center X2 at c
  mydata$X2c <- mydata$X2 - c
  model <- lm(Y ~ X1 * X2c, data = mydata)
  # The interaction coefficient matches the original
  # Main effect coefficients and intercept have new interpretations
  ```

---

## When do you mean center a quantitative predictor in interactive models?

1. **Mean-center**:  
   To make main-effect coefficients interpretable—so they estimate the simple effect at the average value of the other predictor.

   ```r
   # Mean-centering
   mydata$X1c <- mydata$X1 - mean(mydata$X1, na.rm=TRUE)
   mydata$X2c <- mydata$X2 - mean(mydata$X2, na.rm=TRUE)
   model <- lm(Y ~ X1c * X2c, data = mydata)
   ```

2. **Center at a specific value:**  
   To estimate the simple effect at a specific value c (rather than at the mean).

   ```r
   # Center at a specific value (e.g., c = 10)
   mydata$X2c10 <- mydata$X2 - 10
   model <- lm(Y ~ X1 * X2c10, data = mydata)
   ```

---

## Should you use contrast codes or dummy codes for a dichotomous predictor in an interaction model?

- **Generally use contrast codes (e.g., ±0.5 or ±1):**
  - These allow for theoretically motivated comparisons and, with balanced designs, help ensure non-redundant regressors and that R² partitions as expected.

    ```r
    # Example: contrast codes
    mydata$G_code <- ifelse(mydata$Group == "B", 0.5, -0.5)
    ```

- **Dummy codes** compare each non-reference group to a single reference group. They're not orthogonal, so the R² partitioning doesn't sum neatly.

    ```r
    # Example: dummy code
    mydata$G_dummy <- ifelse(mydata$Group == "B", 1, 0)
    ```

---

## Linking parameter estimates from an interactive model to plots

- **Two quantitative predictors:** (center predictors)  
  - Plots show non-parallel lines for simple effect of X₁ at selected levels of X₂.
  - b₀: predicted value at means (zero for centered).
  - b₁, b₂: simple slopes of X₁ or X₂ at the zero of the other.
  - b₃: controls degree of non-parallelism (interaction).

  ```r
  # Example: Plotting simple slopes
  library(ggplot2)
  mydata$X2_group <- cut(mydata$X2, breaks = quantile(mydata$X2, probs = c(0, 0.33, 0.66, 1)), labels = c("Low", "Medium", "High"))
  ggplot(mydata, aes(x = X1, y = Y, color = X2_group)) +
    geom_point(alpha = 0.3) +
    geom_smooth(method = "lm", se = FALSE)
  ```

- **Two categorical predictors:**  
  - Plots show cell means; non-parallel lines indicate interaction.
  - Main effect: horizontal distance between means.
  - Interaction: difference of differences (non-parallelism).

  ```r
  # Example: Cell means plot
  with(mydata, tapply(Y, list(groupA, groupB), mean))
  interaction.plot(mydata$groupA, mydata$groupB, mydata$Y)
  ```

- **Quantitative × Categorical:**  
  - Plots show regression lines for each group of the categorical predictor.
  - Categorical coefficient: difference in adjusted means at mean of quantitative predictor.
  - Interaction: difference in slopes between groups.

  ```r
  ggplot(mydata, aes(x = X, y = Y, color = factor(G))) +
    geom_point(alpha = 0.3) +
    geom_smooth(method = "lm", se = FALSE)
  ```

---

## What are main and simple effects in a model with an interaction? How do you obtain and interpret them?

**Main Effect:**  

- The overall effect of an IV on the DV, averaging across the other IV(s).
- For quantitative predictors, must be mean-centered to interpret as the main effect.

**Simple Effect:**  

- The effect of an IV at a particular level of the other IV(s).
- For quantitative: center the moderator at the value of interest (c).
- For categorical: use contrast codes to compare specific means.

| Concept         | Definition/Interpretation                 | Obtaining/Testing Method                                              |
|-----------------|------------------------------------------|----------------------------------------------------------------------|
| Main Effect     | Overall effect, averaging across others   | Mean-center predictors; test component coefficient with t or F test   |
| Simple Effect   | Effect at a specific value of moderator   | Center moderator at value c; test focal coefficient                   |

  ```r
  # Main effect (mean-centered predictors)
  mydata$X_c <- mydata$X - mean(mydata$X, na.rm=TRUE)
  lm(Y ~ X_c + Z + X_c:Z, data = mydata)

  # Simple effect (center moderator at value c)
  c <- 40
  mydata$Z_c <- mydata$Z - c
  lm(Y ~ X + Z_c + X:Z_c, data = mydata)
  ```

---

## How do you test for interaction and main/simple effects?

**Testing for interaction:**  

1. **Model comparison:**  
   - **Full model:** includes component terms and their interaction  
   - **Additive (no interaction):** includes only component terms
2. **Statistical test:**  
   - Calculate proportional reduction in error (PRE), then F statistic:

     ```r
     # Fit full and reduced (additive) models
     fit_full <- lm(Y ~ X1 * X2, data = mydata)
     fit_add <- lm(Y ~ X1 + X2, data = mydata)
     anova(fit_add, fit_full)
     # Output F statistic and p-value for interaction
     ```

     - PA = # parameters in full model  
     - PC = # in compact model

3. **Interpretation:**  
   - If F exceeds critical value → interaction significant.
   - If testing a single interaction term, F is equivalent to t².

**Testing main/simple effects:**  

- **Main effect:**  
  - Mean-center all variables; test component coefficient.
- **Simple effect:**  
  - Center moderator at value (c) of interest for quantitative predictors; for categorical, construct appropriate contrast code(s).

---

## Mean Types in Two-Dichotomous Predictor Models

- **Cell Mean:** Mean DV for a specific pair of levels (A and B).
- **Marginal Mean:** Mean for levels of one factor, averaging over the other.
- **Grand Mean:** Mean across all observations (equals average of cell means if balanced).

  ```r
  # Suppose mydata has columns groupA and groupB (both dichotomous) and outcome Y
  aggregate(Y ~ groupA + groupB, data = mydata, mean)
  # Marginal means:
  aggregate(Y ~ groupA, data = mydata, mean)
  mean(mydata$Y) # grand mean
  ```

---

## Link parameter estimates to a table of means

Suppose for two factors A and B, cell means are Y₁₁, Y₁₂, Y₂₁, Y₂₂.

- **Contrast Codes (±1):**

  ```r
  # Suppose Yij are cell means
  # Parameter estimates (for ±1 coding):
  b0 <- 0.25 * (Y11 + Y12 + Y21 + Y22)
  b1 <- 0.25 * ((Y21 + Y22) - (Y11 + Y12))  # A main
  b3 <- 0.25 * (Y22 - Y21 - Y12 + Y11)      # Interaction (A × B)
  ```

- **Dummy Codes (A1=0, A2=1; B1=0, B2=1):**

  ```r
  b0 <- Y11                    # Mean of reference (A1, B1)
  b1 <- Y21 - Y11              # A main effect at B1 = 0
  b3 <- (Y22 - Y12) - (Y21 - Y11)  # Difference-in-differences (interaction)
  ```

---

## Quantifying Magnitude of Main, Simple, and Interaction Effects

Given a table of means:

- **Main Effect (Factor A):**

  ```r
  Mag_A <- 0.5 * ((Y21 + Y22) - (Y11 + Y12))
  ```

- **Simple Effect (A at B1):**

  ```r
  Mag_A_at_B1 <- Y21 - Y11
  ```

- **Interaction (Difference of Simple Effects):**

  ```r
  Mag_Interaction <- (Y22 - Y12) - (Y21 - Y11)
  ```

A nonzero interaction coefficient means the simple effect of each predictor changes as the other changes. If this is zero, effects are additive.

*When testing simple effects in a categorical (dichotomous-dichotomous) context with contrast codes, custom codes allow you to focus on a specific subset (e.g., comparing Drug A vs. Drug B only among those receiving Treatment).*
