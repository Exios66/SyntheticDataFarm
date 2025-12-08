# Concepts Exam 2/2

## 🦡Madison/Curriculum/6️⃣1️⃣0️⃣/Exams

## **UNIT 7 — CASE ANALYSIS (Leverage, Outliers, Influence)**

### **Why Case Analysis?**

Protects model integrity by identifying points that distort estimates or violate assumptions.

### **Three Characteristics**

1. **Leverage** — extreme X-values

2. **Regression Outliers** — extreme Y-values (large residuals)

3. **Influence** — points that change the model if removed

⠀
---

## **Leverage**

* Metric: **Hat values** h_{ii}

* High if: $h_{ii}$ > $2p/n or 3p/n$

* Impact: pulls regression line; potential to become influential

---

## **Regression Outliers**

* Metrics:

  * raw residual

  * standardized residual

  * **studentized (preferred)**

* Cutoffs: |studentized| > 2–3

* Impacts:

  * biases slopes

  * inflates SEs

---

## **Influential Points**

* Metrics:

  * **Cook’s D** > $4/(n–p)$

  * **Dfbetas** > $2/√n$

  * **DFFITS** > $2√(p/n)$

* Impacts:

  * slope changes

  * inference changes (Type I/II error)

---

## **Added-Variable Plot**

**~X-axis~**: residual of predictor regressed on all other predictors

~**Y-axis**~: residual of Y regressed on same predictors

Shows: partial linearity, leverage, influence

---

## **Covratio**

Effect of removing case on precision of β estimates.

$<1 →$ point adds noise

> 1 → point increases precision

> Flag: outside $[1 ± 3p/n]$

---

## **Handling Problem Points**

1. Remove (only if data error)

2. Transform or robustify

3. Report models with & without

⠀
---

## **UNIT 8 — MODEL ASSUMPTIONS**

### **Five GLM Assumptions**

1. Linearity
2. Independence
3. Homoscedasticity
4. Normal residuals
5. Reliable X (no measurement error)

⠀

### **Violations → Consequences**

* nonlinearity → biased slopes
* non-independence → invalid SEs
* heteroscedasticity → inefficient β, wrong SEs
* non-normality → inference issues (small n)
* unreliable X → attenuation bias

---

### **Diagnostic Tools**

* **Normality** → Q–Q Plot
* **Homoscedasticity** → Spread–Location Plot
* **Linearity** → Component + Residual Plot

### **Fixing heteroscedasticity**

* transform Y
* WLS
* HC3 robust SEs
* GLM modeling variance

---

## **UNIT 9 — TRANSFORMATIONS**

### **Purpose**

Fix skew, fix non-constant variance, improve linearity.

### **Power Transformations**

$Y^{(\lambda)}$

### **Box–Cox Advantages**

Empirical estimate of λ → optimal transformation.

---

### **Ladder of Powers**

λ increases → distribution spreads

$λ < 1$ → reduces right skew

λ > 1 → reduces left skew

---

### **Start (shift constant)**

Needed when:

1. Values ≤ 0

2. Change interpretation (recenter)

⠀
---

### **Fixing Problems**

* **Skewed residuals** → log / sqrt / square
* **Heteroscedasticity** → $log(Y)$
* **Linearity** → transform X (common)

### **Power Transforms CAN fix**

* monotonic curvature
* fan shapes

**Cannot fix:** discontinuities, multimodal patterns

---

### **Mosteller–Tukey Bulging Rule**

Use quadrant-based visual pattern to match transform (log, sqrt, 1/X, X², etc.)

---

## **UNITS 10–12 — INTERACTIONS**

### **What is an Interaction?**

Effect of X₁ changes depending on level of X₂.

### **How to Create Interaction Term**

$X_1 \times X_2$

---

## **Interpretation by Variable Type**

### **Two Quantitative**

* Main effect: slope when other predictor = 0

* Interaction: change in slope of X₁ per unit X₂

### **Two Dichotomous**

* Interaction = “difference of differences”

### **One Quant + One Dichotomous**

* Different slopes for each group

---

## **Scaling Effects**

* Intercepts change

* Main effects change

* **Interaction term does NOT change in magnitude**

---

## **Centering Rules**

* Mean-center quantitative predictors when zero is meaningless

* Center at meaningful value to interpret slope there

* **Categorical:** use contrast codes for balanced interpretation; dummy codes for reference-group interpretation

---

## **Main vs Simple Effects**

* **Main effect:** effect at X = 0

* **Simple effect:** effect at specified value of moderator

* Test via t-tests or model comparison.

---

## **Linking Model to Plots**

* Two quant: plot lines w/ different slopes

* Two dichotomous: 2×2 means table

* One each: different lines per group

---

## **Means Terminology**

* **Cell mean** — each group combo

* **Marginal mean** — averaged over one factor

* **Grand mean** — average of all

---

## **UNIT 13 — CATEGORICAL PREDICTORS (3+ LEVELS)**

### **Why not use 1,2,3,…?**

Regression would impose linear trend.

---

## **Dummy Coding (k levels)**

k–1 dummies; reference = all zeros

Interpretation: difference from reference

---

## **Contrast Coding**

Codes sum to 0; tests specific hypotheses

Interpretation = effect for contrast comparison

---

## **Predicted Means**

Plug codes into regression formula.

---

## **Multiple Comparisons**

* **Fisher LSD**: after significant omnibus F

* **Holm–Bonferroni**: preferred, more power

* **Scheffé**: most conservative, used for any contrast

* **Bonferroni inequality**: basis for adjustments

---

## **UNIT 14 — GENERALIZED LINEAR MODEL**

### **When to Use GLM?**

Non-normal Y: binary, count, proportion.

---

### **Logistic Regression**

* Link: logit

* Dist: binomial

* Effect size: **odds ratio**

* OR = multiplicative change in odds

### **Poisson Regression**

* Link: log

* Dist: Poisson

---

### **Testing Parameters**

* Wald

* Score

* **Likelihood Ratio Test (preferred)**

---

## **UNIT 15 — POWER ANALYSIS & VALIDITY**

## **Confusion Matrix**

Hit | Miss

False Alarm | Correct Rejection

---

## **Type I vs II**

**Type I = false positive**

**Type II = false negative**

---

## **Power ↑ with**

n ↑, effect size ↑, reliability ↑, variance ↓, alpha ↑

---

## **Problems with Low Power**

* inflated effect sizes
* instability
* Type S/M errors
* publication bias
* vibration of effects

---

## **Positive Predictive Value**

Probability that significant findings are true.

Low with low power.

---

## **Two Power Analysis Types**

* **A priori** — recommended

* **Post hoc** — not meaningful

---

## **Seven Preregistered Elements**

Hypotheses, variables, data structure, exclusion rules, analysis plan, power, outcome reporting.

---
Below is a **clean, professional Markdown visualization** of the *confusion matrix*, with precise labeling and explanations tailored for exam use and statistical validity discussions.

---

## **📊**

## **Confusion Matrix (Markdown Visualization)**

|                                        | **Actual Positive** (Effect Present) | **Actual Negative** (No Effect)     |
|----------------------------------------|--------------------------------------|-------------------------------------|
| **Predicted Positive**                 | **True Positive (TP)**               | **False Positive (FP)**             |
| ==🔴***(Statistically significant)***== | ==🟣*(Hit / Power)*==                 | ==🟣*(Type I Error / False Alarm)*== |
| **Predicted Negative**                 | **False Negative (FN)**              | **True Negative (TN)**              |
| ==🔴*(Not significant)*==               | ==🟡*(Type II Error / Miss)*==        | ==🟡*(Correct Rejection)*==          |

---

## **🔍**

## **Explanation of Each Cell**

### **1. True Positive (TP)**

### **—**

### **Hit / Power**

* You conclude an effect is present.

* The effect **is** truly present.

* This is the desirable outcome when a real effect exists.

* In hypothesis testing language:

  * You reject H_0 correctly.

### **2. False Positive (FP)**

### **—**

### **Type I Error / False Alarm**

* You conclude an effect exists.

* No real effect exists.

* Probability of this error = **α** (alpha).

* In research credibility: these inflate false discoveries.

### **3. False Negative (FN)**

### **—**

### **Type II Error / Miss**

* You conclude there is **no** effect.

* A real effect exists.

* Probability of this error = **β** (beta).

* Power = 1 - β.

* Common in low-power studies.

### **4. True Negative (TN)**

### **—**

### **Correct Rejection**

* You conclude no effect exists.

* No effect exists.

* This is correct retention of the null hypothesis.

---

## **🎯**

## **Why the Confusion Matrix Matters in Statistical Validity**

Understanding this matrix is essential because it frames:

### **A. Statistical Validity**

* Power (TP rate)

* Type I error rate (FP rate)

* Type II error rate (FN rate)

* True negative rate (specificity)

### **B. Positive Predictive Value (PPV)**

* The probability that a statistically significant result is a **true** effect depends on:

  * power

  * alpha

  * prior probability of true effects

  * publication bias

### **C. Application in Power Analysis**

* Increasing power moves probability mass from **FN → TP**.

* Adjusting alpha moves probability mass between **FP ↔ TN**.

---

```svg
<?xml version="1.0" encoding="UTF-8"?>
<svg width="900" height="640" viewBox="0 0 900 640" xmlns="http://www.w3.org/2000/svg" role="img" aria-labelledby="title desc">
  <title id="title">Annotated Confusion Matrix</title>
  <desc id="desc">4-cell confusion matrix with labels, short explanations, and legend: True Positive, False Positive, False Negative, True Negative.</desc>

  <!-- Background -->
  <rect x="0" y="0" width="900" height="640" fill="#ffffff"/>

  <!-- Headers -->
  <text x="300" y="48" font-family="Segoe UI, Arial, sans-serif" font-size="18" font-weight="700" fill="#222">Confusion Matrix</text>
  <text x="300" y="74" font-family="Segoe UI, Arial, sans-serif" font-size="12" fill="#444">Predicted vs Actual — explanation & annotated cells</text>

  <!-- Axis labels -->
  <text x="110" y="130" font-family="Segoe UI, Arial, sans-serif" font-size="14" fill="#222">Actual</text>
  <text x="720" y="130" font-family="Segoe UI, Arial, sans-serif" font-size="14" fill="#222" transform="rotate(-90 720,130)">Predicted</text>

  <!-- Matrix grid -->
  <!-- cell sizes: 380x200, top-left at (160,150) -->
  <g stroke="#222" stroke-width="1">
    <rect x="160" y="150" width="380" height="200" fill="#dff6e7" /> <!-- TP -->
    <rect x="540" y="150" width="380" height="200" fill="#fdecea" /> <!-- FP -->
    <rect x="160" y="350" width="380" height="200" fill="#fff4e6" /> <!-- FN -->
    <rect x="540" y="350" width="380" height="200" fill="#e8f2ff" /> <!-- TN -->
  </g>

  <!-- Quadrant titles -->
  <text x="170" y="175" font-family="Segoe UI, Arial, sans-serif" font-size="13" font-weight="700" fill="#0a7a2a">True Positive (TP)</text>
  <text x="550" y="175" font-family="Segoe UI, Arial, sans-serif" font-size="13" font-weight="700" fill="#b40000">False Positive (FP)</text>
  <text x="170" y="375" font-family="Segoe UI, Arial, sans-serif" font-size="13" font-weight="700" fill="#cc7000">False Negative (FN)</text>
  <text x="550" y="375" font-family="Segoe UI, Arial, sans-serif" font-size="13" font-weight="700" fill="#0a4ea6">True Negative (TN)</text>

  <!-- Explanations inside cells -->
  <foreignObject x="170" y="190" width="360" height="130">
    <div xmlns="http://www.w3.org/1999/xhtml" style="font-family: 'Segoe UI', Arial, sans-serif; font-size:12px; color:#0a7a2a; line-height:1.3;">
      <strong>Hit / Power</strong>
      <div>Model predicts positive & effect truly present. Desired outcome when effect exists.</div>
      <div style="margin-top:6px;"><em>Statistical terms:</em> reject H<sub>0</sub> correctly</div>
    </div>
  </foreignObject>

  <foreignObject x="550" y="190" width="360" height="130">
    <div xmlns="http://www.w3.org/1999/xhtml" style="font-family: 'Segoe UI', Arial, sans-serif; font-size:12px; color:#8b0000; line-height:1.3;">
      <strong>Type I Error / False Alarm</strong>
      <div>Model predicts positive but no real effect exists.</div>
      <div style="margin-top:6px;"><em>Probability:</em> α (alpha)</div>
    </div>
  </foreignObject>

  <foreignObject x="170" y="390" width="360" height="130">
    <div xmlns="http://www.w3.org/1999/xhtml" style="font-family: 'Segoe UI', Arial, sans-serif; font-size:12px; color:#cc7000; line-height:1.3;">
      <strong>Type II Error / Miss</strong>
      <div>Model predicts negative but an effect truly exists.</div>
      <div style="margin-top:6px;"><em>Probability:</em> β (beta); Power = 1 − β</div>
    </div>
  </foreignObject>

  <foreignObject x="550" y="390" width="360" height="130">
    <div xmlns="http://www.w3.org/1999/xhtml" style="font-family: 'Segoe UI', Arial, sans-serif; font-size:12px; color:#0a4ea6; line-height:1.3;">
      <strong>Correct Rejection</strong>
      <div>Model predicts negative & there is no true effect.</div>
      <div style="margin-top:6px;"><em>Desirable when true null holds.</em></div>
    </div>
  </foreignObject>

  <!-- Row/Column headings for matrix orientation -->
  <text x="110" y="195" font-family="Segoe UI, Arial, sans-serif" font-size="12" fill="#333" font-weight="600">Actual Positive</text>
  <text x="110" y="405" font-family="Segoe UI, Arial, sans-serif" font-size="12" fill="#333" font-weight="600">Actual Negative</text>

  <text x="340" y="136" font-family="Segoe UI, Arial, sans-serif" font-size="12" fill="#333" font-weight="600">Predicted Positive</text>
  <text x="740" y="136" font-family="Segoe UI, Arial, sans-serif" font-size="12" fill="#333" font-weight="600">Predicted Negative</text>

  <!-- Legend -->
  <g transform="translate(60,520)">
    <rect x="0" y="0" width="780" height="100" fill="#fafafa" stroke="#ddd" rx="8" />
    <text x="14" y="22" font-family="Segoe UI, Arial, sans-serif" font-size="13" font-weight="700" fill="#222">Legend & Quick formulas</text>

    <g>
      <rect x="14" y="34" width="16" height="12" fill="#dff6e7" stroke="#bbb"/>
      <text x="36" y="44" font-family="Segoe UI, Arial, sans-serif" font-size="12" fill="#222">TP (Hit) — correct detection (power)</text>

      <rect x="260" y="34" width="16" height="12" fill="#fdecea" stroke="#bbb"/>
      <text x="282" y="44" font-family="Segoe UI, Arial, sans-serif" font-size="12" fill="#222">FP — Type I error (α)</text>

      <rect x="470" y="34" width="16" height="12" fill="#fff4e6" stroke="#bbb"/>
      <text x="492" y="44" font-family="Segoe UI, Arial, sans-serif" font-size="12" fill="#222">FN — Type II error (β)</text>

      <rect x="650" y="34" width="16" height="12" fill="#e8f2ff" stroke="#bbb"/>
      <text x="672" y="44" font-family="Segoe UI, Arial, sans-serif" font-size="12" fill="#222">TN — correct rejection</text>
    </g>

    <!-- Quick metrics -->
    <text x="14" y="72" font-family="Segoe UI, Arial, sans-serif" font-size="12" fill="#111">
      Power = TP / (TP + FN)  &nbsp;&nbsp; | &nbsp;&nbsp;  Type I error rate = FP / (FP + TN) = α
    </text>
    <text x="14" y="92" font-family="Segoe UI, Arial, sans-serif" font-size="12" fill="#111">
      Positive Predictive Value (PPV) = TP / (TP + FP)
    </text>
  </g>

  <!-- Annotations: arrows showing trade-offs -->
  <defs>
    <marker id="arrow" markerWidth="8" markerHeight="8" refX="7" refY="4" orient="auto" markerUnits="strokeWidth">
      <path d="M0,0 L8,4 L0,8 z" fill="#666"></path>
    </marker>
  </defs>

  <!-- Arrow from FP to note about alpha -->
  <line x1="700" y1="200" x2="820" y2="200" stroke="#b40000" stroke-width="2" marker-end="url(#arrow)" />
  <text x="824" y="204" font-family="Segoe UI, Arial, sans-serif" font-size="12" fill="#b40000">α (Type I rate)</text>

  <!-- Arrow from FN to power -->
  <line x1="380" y1="460" x2="240" y2="520" stroke="#cc7000" stroke-width="2" marker-end="url(#arrow)" />
  <text x="160" y="528" font-family="Segoe UI, Arial, sans-serif" font-size="12" fill="#444">β (Type II) ↓ → Power ↑</text>

  <!-- Accessibility note -->
  <text x="16" y="620" font-family="Segoe UI, Arial, sans-serif" font-size="11" fill="#666">
    Save as .svg to preserve interactivity/quality. Use colors and cell text for accessibility; check contrast for slide use.
  </text>
</svg>
```
