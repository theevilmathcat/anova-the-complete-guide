# ANOVA (Univariate) Design Options - Quick Reference

## Foundation
ANOVA (Analysis of Variance) is a **linear regression model** for analyzing differences between group means.
It achieves this by comparing variances rather than means directly.
If group means truly differ, the variance between groups (how much group means vary from the overall mean) will be large relative to the variance within groups (how much individual observations vary within each group). ANOVA compares these two sources of variance using an F-statistic:
F = Variance Between Groups / Variance Within Groups
When group means are truly different, the between-group variance will be substantially larger than the within-group variance, producing a large F-statistic. When there are no real differences between groups, both variance components reflect only random variation, and the F-statistic will be close to 1.
This is the concept of anova: partitioning total variance into systematic (between-group) and random (within-group) components, to determine whether group differences are meaningful or just noise.

---

## Design Dimensions for Univariate ANOVA

### 1. **Data Balance**
- **Balanced**: Equal number of observations in each cell
- **Unbalanced**: Unequal observations across cells

### 2. **Factor Structure**
**By Factor Type:**
- **Fixed effects**: Factor levels are specifically chosen and exhaustive (e.g., three specific drug doses)
- **Random effects**: Factor levels are randomly sampled from a larger population (e.g., random sample of schools)
- **Mixed models**: Combination of fixed and random effects

**By Factor Arrangement:**
- **Crossed**: All levels of one factor occur with all levels of another factor
- **Nested (Hierarchical)**: Levels of one factor are unique within levels of another (e.g., students nested within classrooms)

### 3. **Observation Structure**
**Independent Variables:**
- **Factors**: Categorical independent variables
- **Levels/Groups**: Categories within each factor

**Dependent Variable:**
- **Response**: Continuous variable being measured
- **Cells**: Each cell represents one unique combination of factor levels
- **Replicates**: Number of observations within each cell (can be 1 or more)

### 4. **Measurement Design**
- **Between-subjects**: Each participant experiences only one condition
- **Within-subjects (Repeated measures)**: Each participant experiences multiple conditions

### 5. **Additional Control Variables**
- **Covariates (ANCOVA)**: Add continuous predictors to control for confounding variables or increase statistical power
- **Blocking (e.g., Randomized Block Design)**: Group experimental units to control for nuisance variation

---

## Multivariate Extension

### MANOVA/MANCOVA
When you have **multiple dependent variables** analyzed simultaneously:

**Key Differences from Univariate ANOVA:**
- Models **covariance structure** between dependent variables
- Uses **multivariate test statistics** (Wilks' Lambda, Pillai's Trace, Hotelling-Lawley Trace, Roy's Largest Root)
- Requires **multivariate normality** and **homogeneity of variance-covariance matrices**
- More powerful when DVs are correlated and change in the same direction
- Significant effects require follow-up analyses (discriminant analysis, linear combinations) to interpret which combinations of outcomes differ

---

## Design Checklist

When planning an ANOVA, specify:
- [ ] Balanced or unbalanced?
- [ ] Fixed, random, or mixed effects?
- [ ] Crossed or nested factors?
- [ ] Between-subjects or within-subjects?
- [ ] Number of replicates per cell?
- [ ] Any covariates (ANCOVA)?
- [ ] Any blocking factors?
