
# Issues with Assigning Sequential Numbers to Categorical Predictors

Assigning sequential numbers to levels of a categorical predictor is inadequate because there is no meaningful order to the groups. Categorical variables do not imply rank order or interval information. Assigning consecutive values (e.g., 1, 2, 3) wrongly assumes:

1. The categories have an inherent order.
2. The relationship between predictor and outcome is linear.

If a single numeric variable was used, the relationship would change based on how the groups are ordered (unless the variable is ordinal). Also, using one parameter estimate would prevent researchers from examining specific pairwise group differences.

---

## Dummy Coding for Categorical Variables with More Than Two Levels

For a categorical variable with $N$ levels, you must use $N-1$ dummy-coded regressors. Dummy coding works as follows:

1. **Select a Reference Group:** Choose one group as the reference.
2. **Code the Reference Group:** Assign 0 to all $N-1$ regressors.
3. **Code the Target Groups:** For each of the remaining groups, assign 1 for that group's regressor and 0 for all others.

**Example (3 Levels: Alcohol, Depress, Healthy; 'healthy' as reference):**

| Group   | alcohol\_d3 (Reg. 1) | depress\_d3 (Reg. 2) |
|---------|:--------------------:|:---------------------:|
| alcohol |          1           |          0            |
| depress |          0           |          1            |
| healthy |          0           |          0            |

---

## Interpretation of Dummy-Coded Parameter Estimates

The predicted outcome ($\hat{Y}$) for any observation $i$ is:

$$
\hat{Y}_i = b_0 + b_1 X_{i1} + b_2 X_{i2} + \dots
$$

- **Intercept ($b_0$):** The predicted value (mean) for the reference group.  
  For the model  
  $$
  \hat{Y} = b_0 + b_1(\text{alcohol\_d3}) + b_2(\text{depress\_d3})
  $$
  the mean for the healthy group (where both regressors are 0) is just $b_0$.

- **Regressor Estimates ($b_j$):** Each $b_j$ represents the contrast (mean difference) between the target group (coded 1 for that regressor) and the reference group.

    - For the 'alcohol' group:
      $$
      \hat{Y}_{alcohol} = b_0 + b_1(1) + b_2(0) = b_0 + b_1
      $$
      The estimate $b_1$ is the difference $(b_0 + b_1) - b_0 = b_1$.

---

## Contrast Coding for Categorical Variables with More Than Two Levels

For $m$ levels, use $m-1$ contrast-coded predictors. Contrast codes must satisfy two conditions:

1. **Sum to Zero:** For each contrast, the sum of all $\lambda$ values must equal zero:
   $$
   \sum_k \lambda_k = 0
   $$

2. **Orthogonality:** For any pair of contrasts, the sum of the products of their $\lambda$ values across groups must be zero:
   $$
   \sum_k \lambda_{1k} \lambda_{2k} = 0
   $$

Researchers usually use unit weights so the slope ($b_j$) equals the exact mean difference.

- **Coefficients for Set U** (with $u$ groups vs $v$ groups in Set V):  
  All groups in $U$ get coefficient $+\frac{1}{u}$, all groups in $V$ get $-\frac{1}{v}$, and groups not in $U$ or $V$ get 0.

### Examples

**3-Level Example: Patient vs Healthy (C1), Alcohol vs Depress (C2)**

| Group   | Patient vs Healthy (C1) | Alcohol vs Depress (C2) | Logic                      |
|---------|:-----------------------:|:-----------------------:|:--------------------------|
| alcohol |        0.333            |         0.5             | C1: $1/3$; C2: $1/2$       |
| depress |        0.333            |        -0.5             | C1: $1/3$; C2: $-1/2$      |
| healthy |       -0.667            |         0.0             | C1: $-2/3$; C2: 0          |

**4-Level Example:**

| Group    | 1,2 vs 3,4 (C1) | 1 vs 2 (C2) | 3 vs 4 (C3) | Logic                  |
|----------|:---------------:|:-----------:|:-----------:|:-----------------------|
| Group 1  |      0.5        |    0.5      |    0.0      | C1: $2/4$; C2: $1/2$   |
| Group 2  |      0.5        |   -0.5      |    0.0      | C1: $2/4$; C2: $-1/2$  |
| Group 3  |     -0.5        |    0.0      |    0.5      | C1: $-2/4$; C3: $1/2$  |
| Group 4  |     -0.5        |    0.0      |   -0.5      | C1: $-2/4$; C3: $-1/2$ |

---

## Interpretation of Contrast-Coded Parameter Estimates

- **Intercept ($b_0$):** The mean of all group means.
- **Regressor Estimates ($b_j$):** The size of the specific mean comparison (contrast) tested by that regressor, calculated as:

  $$
  b_j = \frac{\sum_k \lambda_k \bar{Y}_k}{\sum_k \lambda_k^2}
  $$

If unit weights are used, $b_j$ is the exact mean difference for the contrast.

---

## Calculating Predicted Means for Any Group

Predicted mean ($\hat{Y}$) for any group can be calculated by substituting that group's coding pattern into the model equation:

$$
\hat{Y}_i = b_0 + b_1 X_{i1} + b_2 X_{i2} + \cdots
$$

- **Dummy Codes:** 0s (reference group: $\hat{Y} = b_0$); 1s for target group $j$: $\hat{Y}_j = b_0 + b_j$.
- **Contrast Codes:** Substitute the lambda codes for each regressor; the predicted value $\hat{Y}_k$ matches the group mean $\bar{Y}_k$ for all groups when using a full set of contrasts.

---

## Superiority of Pairwise Contrasts in a Linear Model

Pairwise contrasts using dummy-coded regressors (or other suitable coding) in a linear model are generally superior to separate pairwise t-tests. The linear model uses the full error term (from all groups/subjects) when computing mean square error (MSE), giving a more robust and powerful estimate of error variance ($\sigma^2$) than a t-test using only two groups.

---

## Testing the Third Pairwise Contrast (Three Levels)

For a three-level categorical variable analyzed with two dummy regressors (e.g., $b_1$ for G1 vs G3, $b_2$ for G2 vs G3), the third contrast (G1 vs G2) is simply $b_1 - b_2$.

To directly obtain the statistical test for this contrast, recode the categorical variable to set one of the groups involved (e.g., G2) as the reference. The new model's coefficient for the non-reference group (G1) will directly estimate the G1 vs G2 difference.

---

## Value and Use of the Main Effect (Omnibus Test)

The omnibus test for a categorical variable's main effect (model with all categorical predictors vs. the mean-only model) tells you if at least one contrast among the groups is significant.

However, this test is often not very informative because it doesn't reveal which groups differ. Researchers usually prefer specific, focused single-degree-of-freedom contrasts. The omnibus test is sometimes reported due to tradition, but is not needed for Type I error protection and can sometimes reduce statistical power.

---

## Model Comparison for Main Effect with Other Predictors

When including covariates, test the main effect of a categorical predictor by comparing:

1. **Augmented Model (Model A):** Contains regressors for the categorical variable *and* all other predictors.
2. **Compact Model (Model C):** Contains only regressors for other predictors (no categorical regressors).

The $F$-test compares the models to assess whether adding the categorical predictor improves fit beyond the other predictors.

---

## When Do Contrasts Sum to the Full $R^2$?

The sum of Sums of Squares Reduced (SSR) or $\Delta R^2$ from individual contrasts equals the total $R^2$ *only if* regressors are orthogonal.

- **They sum:** With a full set of orthogonal contrast-coded regressors (e.g., planned orthogonal contrasts), the explained variances are separate and add up.
- **They do not sum:** With non-orthogonal regressors (e.g., dummy codes), some explained variance overlaps; thus, the $\Delta R^2$s do not add to the total model $R^2$.

---

## Definitions: Test-wise and Family-wise Error Rates

- **Test-wise error rate:** The chance of a Type I (false positive) or Type II (false negative) error in a single statistical test.
- **Family-wise error rate:** The probability of at least one Type I or II error across a family of comparisons.

In psychological research, it is important to control both, especially the family-wise Type I error, because running many tests increases the chance of a false positive somewhere.

### Protecting Against Inflation of Family-wise Type I Error

To control family-wise error rate when running multiple comparisons:

| Contrast Type | How Protection Works | How It Differs from Other Types |
|--|--|--|
| **Planned Orthogonal Contrasts (POCs)** | No correction typically needed; orthogonal contrasts test different variance components. Omnibus test not needed for Type I error. | Each contrast is a different 'family' (asks a distinct question). |
| **Planned, Non-Orthogonal Pairwise Contrasts** | Use Holm-Bonferroni (or Fisher LSD for 3-level factors); correction strictly controls $\alpha$ across the family. | Comparisons are related; Holm-Bonferroni is less conservative and more powerful than Bonferroni. |
| **Unplanned/Post-hoc Contrasts** | Use Scheffe test, adjusting critical value to control error regardless of number of comparisons. | These are data-driven exploratory contrasts; Scheffe is most conservative. |

---

## Fisher LSD (Least Significant Difference) Method

The Fisher LSD is a "protected" approach for planned, non-orthogonal contrasts (especially with three levels):

1. **Requirement:** First, test the omnibus (main effect). If it's *not* significant, stop.
2. **If Significant:** Proceed to conduct pairwise comparisons (e.g., using dummy codes) at the usual $\alpha$ level *without* further correction.

Because you only run individual tests if the omnibus test is significant, the family-wise error rate is controlled.

---

## Holm-Bonferroni Method

The Holm-Bonferroni procedure is a flexible, powerful way to maintain family-wise Type I error control for multiple planned comparisons:

1. **When to use:** Planned, non-orthogonal contrasts (limit the number of tests to avoid loss of power).
2. **Procedure:**
   - Rank $k$ tests by increasing $p$-values.
   - Compare the lowest $p$ to $\alpha/k$, the next lowest to $\alpha/(k-1)$, etc.
   - As soon as a $p$-value fails to be significant, stop testing and retain all remaining null hypotheses.
   - Adjusted $p$-values are always as large as the maximum of all previously adjusted $p$-values.

Holm-Bonferroni is always at least as powerful (or more) than the standard Bonferroni method.

---

## Scheffé Test

The Scheffé test is a very conservative approach for unplanned/post-hoc comparisons:

1. **When to use:** Complete exploratory ("fishing expedition") comparisons.
2. **Procedure:**
   - Adjust the calculated $F$ statistic for a given comparison using the number of groups ($m$):
     - Divide the calculated $F$ by $(m-1)$ or
     - Compare the obtained $F$ to the critical $F$ value multiplied by $(m-1)$.

Only worth applying if the omnibus (grand mean vs. means model) test is significant.

---

## Bonferroni Inequality

The Bonferroni inequality is the mathematical basis for family-wise Type I error correction:

$$
\alpha_{set} \leq (\text{set size}) \times \alpha_{test}
$$

To keep the total probability of a Type I error below $\alpha$, set the per-comparison alpha at $\alpha/c$, where $c$ is the number of comparisons. Choose the critical value for each test using this adjusted $\alpha$.
