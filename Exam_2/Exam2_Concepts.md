# Unit 7 – Case Analysis

- **What is case analysis and why do we do it?**
- **What are the three primary characteristics of observations that we focus on in case analysis?**
- **When doing univariate and bivariate exploratory data analysis, what plots and summary statistics do we typically review? Which plots are good for which types of variables?**

---

## Leverage

- **What is it?**
- **What metric do we use to identify points with high leverage?**
- **What is the impact of leverage on our models?**

---

## Regression Outliers

- **What are they?**
- **What three metrics do we use to identify regression outliers and which one do we prefer?**
- **What are the two potential impacts of regression outliers on our models?**

---

## Influential Observations

- **What are they?**
- **What metrics do we use to identify influential observations and how are they different from each other?**
- **What is an added variable plot? What do we plot on the x and y axes of this plot?**
  - **X-axis:** Residual of predictor regressed on all other predictors
  - **Y-axis:** Residual of Y regressed on same predictors
- **What are the two potential impacts of influential observations on our models?**
  - **Slope changes**
  - **Inference changes (Type I/II error)**
- **Identify points with high leverage, regression outliers, and influential points on a scatterplot**

## Unit 8 – Model Assumptions

- **What are the five assumptions of the general linear model?**
- **What are the consequences of violating each assumption?**
- **What are the implications of the unreliable X assumption for the use of covariates?**
- **What is a quantile-quantile (quantile comparison) plot and what do we use it for?**
- **What is a spread-location plot and what do we use it for?**
- **What options exist to address problems with non-constant (heterogeneity) variance of residuals?**
- **What is a Component + Residual plot and what do we use it for? What do we plot on the x and y axes of this plot?**

---

## Unit 9 – Transformations

- **What are power transformations and why do we use them?**
- **What are the benefits of the Box-Cox transformation vs. a simple power transformation?**
- **What happens to scores as we ascend and descend the ladder of power transformations?**
- **What is a start and when do we need to use one (two uses)?**
- **How can we use power transformations to address skewed residuals?**
- **How can we use power transformations to address non-constant variance of residuals?**
- **Is it more common to transform y or x to address skew and non-constant variance problems? What about linearity problems (when y and when x)?**
- **What type of linearity problems can power transformations address and what types can it not fix?**
- **What is the Mosteller and Tukey’s bulging rule? What transformations do we use for linearity issues in each quadrant?**

---

## Units 10–12 – Interactions

- **What is an interaction?**
- **How do you create a regressor to test for an interaction between predictors?**
- **How do you interpret the parameter estimates for a model with an interaction between two predictors? How does this change if the predictors are both quantitative, both dichotomous, or one of each?**
- **Which parameter estimates will change (and which won’t) as you change the scaling of predictors in a model with an interaction?**
- **How can you use the model formula (with parameter estimates) to describe how the magnitude of the effect of one X will change depending on a second X? (For models with two quantitative predictors, two dichotomous predictors, and one of each.)**
- **Calculate how any parameter estimate in a model will change if a specific predictor was re-scaled in some way (e.g., mean centered or centered on some other value). Know this for both quantitative predictors and dichotomous predictors.**
- **When do you mean center a quantitative predictor in an interactive model? When do you center on some value other than the mean?**
- **When do you use centered (contrast) codes vs. dummy codes for a dichotomous predictor in an interactive model?**
- **Link parameter estimates from an interactive model to a plot of the model. Know how to do this for models with two quantitative predictors, two dichotomous predictors, and one of each.**
- **What are main and simple effects in a model with an interaction? How do you obtain them? How do you interpret them? How is this different for models with two quantitative predictors, two dichotomous predictors, and one of each?**
- **How do you test for an interaction using a t-test or model comparison? How do you test for main and simple effects in these models?**
- **What is a cell mean, marginal mean, and grand mean in a model with two dichotomous predictors?**
- **Link the parameter estimates from an interactive model with two dichotomous predictors to a table of means. Be able to go both directions so you could write out the model formula (including parameter estimates) for a model from a table of means either when using centered (contrast) codes or dummy codes.**
- **Quantify the magnitude of main effects, simple effects, and an interaction between two dichotomous predictors using a table of means.**

---

## Unit 13 – Categorical Predictors with More Than Two Levels

- **Why can we not simply assign sequential numbers to levels of a categorical predictor?**
- **How do you calculate dummy coded regressors for categorical variables with 3 or more levels (including what codes are assigned to each regressor)?**
- **How do you interpret the parameter estimates for dummy coded regressors?**
- **How do you calculate contrast coded regressors for categorical variables with 3 or more levels (including what codes are assigned to each regressor)? (Know for 3 and 4 level categorical variables given a description of the planned contrasts.)**
- **How do you interpret the parameter estimates for contrast coded regressors?**
- **Be able to calculate predicted means for any level given a model formula that used either dummy or contrast codes**
- **Why are pairwise contrasts using dummy coded regressors in a linear model superior to pairwise t-tests using between-subjects/two group t-tests?**
- **How can you get the test of the third pairwise contrast when using dummy coded regressors for a 3-level categorical predictor?**
- **What is the value of testing for a main effect of a categorical variable? When will you do this?**
- **What model comparison will provide a test of the main effect of a categorical predictor when other predictors are also in the model?**
- **When will sums of squares (SS) for a model with a categorical predictor sum to the full model SS? When will they not?**
- **What is test-wise and family-wise error rates?**
- **When and how do we protect against inflation of family-wise Type I error rates when doing multiple comparisons among levels of a categorical predictor? How is this similar or different when using planned orthogonal contrasts, planned pairwise contrasts, or unplanned contrasts?**
- **How and when should we use Fisher's LSD approach?**
- **How and when should we use Holm-Bonferroni approach?**
- **How is the Holm-Bonferroni approach superior to the Bonferroni approach?**
- **How and when should we use Scheffé test approach?**
- **What is the Bonferroni inequality?**

---

## Unit 14 – The Generalized Linear Model

- **When might you use the generalized linear model?**
- **When would you specifically use a generalized linear model with the logit link function and binomial distribution? What special case analysis is this?**
- **When would you use a generalized linear model with the log link function and Poisson distribution?**
- **Be able to calculate odds or probability from the other. Be able to calculate log-odds from a model.**
- **What is an odds ratio and how do you interpret it for a quantitative predictor or regressor for a categorical predictor?**
- **Why do we use the odds ratio as the preferred effect size in logistic regression?**
- **Be able to compare two simple (one X) logistic plots (in probability units) and tell which has bigger/smaller intercept and slope.**
- **What are the three approaches to testing parameter estimates in logistic regression? Which is preferred and why?**
- **How do we handle categorical predictors and multiple predictors in logistic regression?**

---

## Unit 15 – Power Analysis and Statistical Validity

- **Understand the confusion matrix and its use in discussing statistical validity. Be able to label the four cells of the confusion matrix.**
- **What is the difference between Type I and Type II errors?**
- **What are the factors that affect power in the linear model? How do they affect power? Be able to discuss these relationships with respect to the sampling distribution for a parameter estimate.**
- **What are the two approaches to power analyses? When and why do you do each of them?**
- **What problems are associated with low power studies?**
- **What is positive predictive value and why does it matter?**
- **Why are sample effect size estimates often incorrect (too large) when calculated in studies with low power?**
- **What is the problem of vibration of effects?**
- **What is publication bias and why is it worse for low power studies?**
- **What are the 7 important study characteristics that should be pre-registered?**
