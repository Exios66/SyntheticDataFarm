# Unit 9 - Transformations

## What are power transformations and why do we use them?

Power transformations are a group of transformations in the family of powers and roots (e.g., powers, roots if *p* is a fraction, or inverse powers if *p* is negative).

We use power transformations because the General Linear Model (GLM) makes strong assumptions about the structure of data, which often are not met in practice. Transforming the response variable (*Y*) or the predictor variable(s) (*X*) can help the data conform more closely to GLM assumptions.

---

## What are the benefits of the Box-Cox transformation vs. a simple power transformation?

The Box-Cox transformation provides a form that is similar to a simple power transformation (X<sup>p</sup>) but adds convenience in certain cases. The Box-Cox function is:

$$
X(p) \equiv \frac{X^p - 1}{p}
$$

This is a linear function of X<sup>p</sup> and thus has the same essential effect on the data as a simple power transformation.

**Key structural benefits of Box-Cox:**

1. **Preserving Direction:** Dividing by *p* preserves the direction of X, which matters especially when *p* is negative (since simple power transformations can reverse direction).
2. **Matching Level/Slope:** The Box-Cox function matches the level and slope of the curve at X = 1.
3. **Log Transformation Inclusion:** The log transformation (when *p* = 0) is handled directly in the Box-Cox formulation.

---

## What happens to scores as we ascend and descend the ladder of power transformations?

- The effect of a power transformation depends on whether we move up or down from *p* = 1 (no transformation):

  - **Descending the ladder** from *p* = 1 toward *p* = -2: Large values of X are compressed and small values are spread out.
  - **Ascending the ladder** from *p* = 1 towards *p* = 3: The opposite happens—large values are spread out and small values are compressed.

---

## What is a "start" and when do we need to use one? (two uses)

A *start* is a positive constant added to every value in the data.

A start is needed when:

1. **Ensuring Monotonicity and Definition:** Power transformations only make sense when all X values are positive. Transformations like log(X) or X<sup>p</sup> are undefined for zero or negative values, and applying them to such data could change the order of the scores. Adding a start makes all values positive.
2. **Increasing Effectiveness:** Power transformations are most effective when the ratio of the largest to smallest value is large; using a negative start can sometimes increase this ratio, thereby maximizing the transformation's effectiveness.

---

## How can we use power transformations to address skewed residuals?

Transforming the response variable (*Y*) is a common way to correct skewness in the distribution of residuals.

- **For positive skew** (most common): Transform *Y* down the ladder (e.g., using the log transformation).
- **For negative skew:** Transform *Y* up the ladder.

---

## How can we use power transformations to address non-constant variance of residuals?

When the spread of errors increases as the predicted value $\hat{Y}$ increases (i.e., violation of constant variance/homoscedasticity):

- **Increasing spread (most common):** Transform *Y* down the ladder.
- **Decreasing spread:** Transform *Y* up the ladder.

*Note: Problems of unequal spread and skewness often co-occur, and transforming *Y* down the ladder can often address both.*

---

## Is it more common to transform *Y* or *X* to address skew and non-constant variance? What about linearity problems?

- For skewness and non-constant variance, it is more common to transform the **outcome variable (*Y*)**.
- For linearity problems:
  - If only one predictor (*X*) is problematic, transform *X*.
  - If all *X* variables show similar nonlinearity, transform *Y*.

---

## What type of linearity problems can power transformations address, and which can they not?

- **Can address:** Simple monotonic relationships (i.e., make these more linear).
- **Cannot address:** More complex relationships (e.g., quadratic or cubic effects), which require polynomial regression or other specialized transformations (like the logit transformation).
