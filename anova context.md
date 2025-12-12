# ANOVA Test

## When to Use
> **Use ANOVA when:**
> - You are testing for **differences in means**.
> - The **response variable is continuous**.
> - **Parametric assumptions** are satisfied.
> - The groups are **independent (unpaired)**.
> - There are **2 or more groups**.
>
> **Note:** For exactly **two groups**, a *t-test* is typically used (although ANOVA and t-test are mathematically equivalent in this case).

---

## Steps in Conducting an ANOVA

### 1. Formulate the Hypotheses
- **H0 (Null):** There is no difference between group means (they are equal).
- **H1 (Alternative):** There is a difference between at least one pair of group means.

### 2. Run the ANOVA
- Data goes into the statistical "washing machine" (ANOVA model), and it outputs a result.

### 3. Validate ANOVA Assumptions
After performing the test, we check the ANOVA assumptions:

**a)** **Independence** of observations between groups.

**b)** **Normality of the residuals** (note: the *residuals*, not the raw response values).

**c)** **Homogeneity of variances** ("homoscedasticity").

If all assumptions are not satisfied:
- try first to transform the response variable by using excel to block do either square root of each value or log (x+1) of each value. Then try again the anova. If still not ok, do the Kruskal-Wallis test instead.

If all assumptions are satisfied:
- Look at the **p-value** of the factor in the ANOVA table.
- If **p < 0.05**, we conclude that a significant difference exists.

If the factor has only **2 levels** (e.g., Program A vs Program B), we stop here.
If it has **more than 2 levels**, proceed to post-hoc testing.

## Post-Hoc Testing (If More Than 2 Groups)
If the factor has more than two levels (e.g., programs A, B, C):
- Conduct **post-hoc tests** to identify *where* the differences lie.
- Common post-hoc tests include:
  - **Tukey HSD**
  - **Bonferroni**
  - **Fisher LSD**
  - **Scheffé**

These tests:
- Compare **all pairs of group means**.
- Identify pairs with **p < 0.05**, indicating significant differences.

---

## Visualization
- After identifying significant differences, create an **interaction plot** to visually present the results and highlight where the differences occur.

