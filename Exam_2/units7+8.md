# Unit 7 - Case Analysis

## What is case analysis and why do we do it?

Case analysis is conducted to identify unusual or excessively influential data points. It is an important first step in understanding your data. These problematic data points may bias results or reduce the power to detect effects by inflating standard errors or decreasing $R^2$.

---

## What are the three primary characteristics of observations that we focus on in case analysis?

The three primary characteristics that researchers focus on in case analysis are:

1. **Leverage**
2. **Regression outlier**
3. **Influence**

---

## When doing univariate and bivariate exploratory data analysis, what plots and summary statistics do we typically review? Which plots are good for which types of variables?

Univariate exploratory data analysis often reviews summary statistics such as:

- Mean
- Standard deviation (SD)
- Minimum (p0)
- Median (p50)
- Maximum (p100)

**For visualizations:**

- **Numeric Variables (Univariate):**  
  - Histograms  
  - Density plots  
  - Rug plots  
  - Box plots (display median, 25th and 75th percentiles, and outliers)  
  - Violin plots (show the shape and tails of the distribution; can be overlaid on box plots)  

- **Numeric vs. Numeric Variables (Bivariate):**  
  - Scatterplots (possibly with a simple line or a LOWESS line to assess relationship shape)  

- **Categorical vs. Numeric Variables (Bivariate):**  
  - Grouped box and violin plots  

---

### Leverage

**What is it?**  
Leverage is a property of the predictors; the outcome variable is not considered for leverage analysis. An observation's leverage increases as its distance from the mean of all predictors increases. With multiple predictors, leverage measures the distance from the centroid (the point of means) of the predictor variables.

**What metric do we use to identify points with high leverage?**  
Hat values ($h_i$) provide an index of leverage. Hat values are bounded between $1/N$ and $1$, and the mean hat value in a sample equals $P/N$, where $P$ is the number of parameters and $N$ is the sample size.

**What is the impact of leverage on our models?**  
High leverage points that are fit well by the model are often desirable: they increase $R^2$ and the variance for the predictor, thus reducing the standard error (SE) for predictors and yielding more power. When high leverage points are fit well, they do not alter coefficients ($b$s).

---

# Unit 8 - Model Assumptions

## What are the five assumptions of the general linear model?

All general linear model (GLM) procedures commonly make these five assumptions (except the first, all are expressed and assessed with respect to residuals around the prediction line, $\hat{Y}$):

1. **Exact X:** The independent variables (IVs) are assumed to be known exactly (i.e., without measurement error).
2. **Independence:** Residuals are independently distributed.
3. **Normality:** All residual distributions are normally distributed.
4. **Constant variance (Homoscedasticity):** All residual distributions have a constant variance.
5. **Linearity:** All residual distributions are assumed to have means equal to zero.

---

## What are the consequences of violating each assumption?

| Assumption                   | Consequence of Violation                                                                 |
|------------------------------|-----------------------------------------------------------------------------------------|
| **Exact X**                  | Leads to biased (inaccurate) estimates of regression coefficients.                      |
| **Independence**             | Can compromise the validity of statistical tests by causing inaccurate standard errors. |
| **Normality**                | Leads to inefficient standard errors (low power, Type II errors).                       |
| **Constant variance**        | Efficiency (precision of estimation) is impaired, and coefficient SEs become inaccurate. Coefficients remain unbiased. |
| **Linearity**                | Leads to inaccurate (biased) parameter estimates.                                       |

---

## What are the implications of the unreliable X assumption for the use of covariates?

Violations of the unreliable X assumption (i.e., measurement error in predictors) mean that covariates only control for the measured construct to the degree that they are reliable (and valid). Analyses that rely on unreliable covariates do not control the construct’s variance well.

---

## What is a quantile-quantile (quantile comparison) plot and what do we use it for?

A normal quantile-quantile (QQ) plot is used to detect whether the distribution of errors deviates from normality. It shows the percentile distribution of the data (errors) against what would be expected if the distribution were normal. For perfectly normal data, the points lie along a straight line.

---

## What is a spread-location plot and what do we use it for?

A spread-location plot (spread-level plot) helps diagnose whether residuals have constant variance. It plots the log of the absolute studentized residuals versus the log of the predicted values. Increasing spread ("funnel" shape) indicates violations of constant variance.

---

## What options exist to address problems with non-constant (heterogeneity) variance of residuals?

- Apply power transformations to the outcome variable ($Y$)
- Use weighted least squares
- Apply heteroscedasticity-corrected standard errors (e.g., White-corrected SEs)

---

## What is a Component + Residual plot and what do we use it for? What do we plot on the x and y axes of this plot?

A Component + Residual plot (partial residual plot) is used to detect if the linearity assumption is violated. If so, coefficients may be biased.

- **Y-axis:** The partial residual $(e_i(j) = e_i + b_j X_{ij})$  
- **X-axis:** The focal predictor ($X$)

This plot helps isolate the effect of a specific predictor, making it easier to see its unique contribution and identify observations that impact that effect.
