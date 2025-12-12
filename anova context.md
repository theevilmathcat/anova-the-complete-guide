# ANOVA test

When to use:

> Test for difference > Continuous response variable (means), parametric assumption satisfied, unpaired test (i.e., independent groups), for 2 or more groups.
Note: For exactly 2 groups, we can use a t-test since they are equivalent. It's a convention: 2 groups: t-test, 3 groups -> ANOVA.

1. We want to know if there is a difference or not between means.
   a) We define the hypotheses: H0: There is no difference (i.e., they are equal) vs H1: There is a difference.
   b) Data goes into the "washing machine" (ANOVA test) and it spits out the result.
   c) We conclude in the end whether there is a difference or not.
2. After performing the test, we validate to see if it meets the ANOVA requirements:
   a) Independence of observations between groups.
   b) Normality of the residuals (of the RESIDUALS, not the response).
   c) Homogeneity of variances ("Homoscedasticity").
   If yes, we can take the conclusion from the ANOVA table and check the p-value of the factor. If < 5%, we conclude that a difference exists.
   If the factor only has 2 levels (e.g., program A vs program B), we stop here.
   If the factor has more than 2 levels (e.g., program A, B, C...) we perform a post-hoc test: Tukey, Bonferroni, Fisher LSD, Scheffe). We aim to find out, given that a difference exists, where the difference lies.
   These tests will group the factor levels into pairs and indicate if there are pairs with a p-value < 5% significance. This/These pair(s) is/are where the difference exists.
   > We then create an interaction plot to show the conclusion.
