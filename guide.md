# Complete ANOVA Guide for Minitab - Weightlifting Theme. Diogo Marques 
- Last revision: 11/12/2025

## Introduction: ANOVA purpose → comparing group means. 
It is called Analysis of Variance because it uses the variance in the data to do it. It does not compare means directly.
It asks this question:
"How much of the total variance in Y (the outcome) is explained by the group differences?"

ANOVA splits total variability into two parts:
- 1. Variance between groups (explained variance) -> How much the group means differ from each other.
- 2. Variance within groups (unexplained variance) ->How much individuals vary inside each group.

Then it calculates:
F = Between-group variance / Within-group variance

If the groups are truly different, then:
>between-group variance ↑ high
>within-group variance stays relatively small
>F becomes ↑ large
>p-value ↓ small
>meaning the means are different

! So the goal is comparing mean differences, but the method is analyzing variances.

## Table of Contents
1. [Types of ANOVA](#types-of-anova)
2. [Procedure](#procedure-for-anova)
3. [Graphical Interpretations](#graph-interpretation)
4. [Further Tests](#further-tests)
5. [Terminology](#terminology)
---
## BGN INDEX
# types-of-anova
## Types of ANOVA (UNIVARIATE)
### Main Classification
**1. By Number of Factors:**
- One-way ANOVA (1 factor)
- Two-way ANOVA (2 factors)
- Three-way ANOVA (3+ factors)
- 4-Way, 5-Way... and so on

**2. By Design:**
- **Between-subjects** (different people in each group)
- **Repeated measures** (same people tested multiple times)
- **Mixed** (combination of both)

**3. By Factor Type:**
- **Fixed factors** (you choose specific levels you care about)
- **Random factors** (levels are randomly sampled from many possible)
- **Mixed** (combination of both)

**4. By Cell Structure**
- **Balanced ANOVA** (equal n per cell)
- **Unbalanced ANOVA** (unequal n)

**5. By Additional Modelling Constraints**
- **ANOVA with blocking** / Randomized block design (RBD)
- **Nested ANOVA** (hierarchical factors)
- **Crossed ANOVA** (all factor combinations tested)

**6. Special Case** ANOVAs
- **ANCOVA** (ANOVA + covariates)

**7. Variance corrections / assumption fixes**
- **Welch’s ANOVA** (heterogeneous variances)
- **Greenhouse–Geisser** / Huynh–Feldt–corrected RM ANOVA
- **Sphericity-corrected repeated-measures ANOVA**
## END INDEX

---
## BGN EXPLANATION  1. By Number of Factors
---
# 1. **BY NUMBER OF FACTORS**
## **1A. One-way ANOVA (1 factor)**
**Scenario:** Compare squat 1RM across three training programs.
'''
Program   Squat_1RM
A         150
A         155
A         160
B         140
B         138
B         145
C         165
C         170
C         172
'''
---
## **1B. Two-way ANOVA (2 factors, crossed)**
**Scenario:** Squat 1RM by Program and Gender.
Program	Gender	Squat_1RM
       A	M	160
       A	M	158
       A	M	162
       A	M	155
       A	M	157
       A	M	159
       A	M	161
       A	M	156
       A	M	163
       A	M	154
       A	F	130
       A	F	128
       A	F	132
       A	F	127
       A	F	129
       A	F	131
       A	F	125
       A	F	133
       A	F	126
       A	F	134
       B	M	170
       B	M	168
       B	M	172
       B	M	165
       B	M	167
       B	M	169
       B	M	171
       B	M	166
       B	M	173
       B	M	164
       B	F	140
       B	F	138
       B	F	142
       B	F	137
       B	F	139
       B	F	141
       B	F	135
       B	F	143
       B	F	136
       B	F	144

---
## **1C. Three-way ANOVA (3 factors, crossed)**
**Scenario:** Program × Gender × Experience.
Program   Gender   Experience   Squat_1RM
A         M        Novice       120
A         M        Advanced     170
A         F        Novice       100
A         F        Advanced     135
B         M        Novice       130
B         M        Advanced     180
B         F        Novice       105
B         F        Advanced     140

## END EXPLANATION 1. By Number of Factors

---
## BGN EXPLANATION 2. By Design
---
# 2. **BY DESIGN**
## **2A. Between-subjects ANOVA**
Use the same dataset as one-way ANOVA and Any higher-order factorial ANOVA
As long as Each observational unit is measured once and belongs to only one combination of factors.
So you can have a ton of measurements inside each cell. 
✅ Valid between-subjects factorial ANOVA
- No row appears twice
- No unit is measured across multiple levels
- Multiple measurements per cell are allowed
- Units do not cross factor boundaries

✅ 1. Between-Subjects ANOVA
✔ Each subject/unit appears in only ONE condition
✔ No repeated measurements
✔ Different people (or stores or items) in each group
Lifter   Program   Squat_1RM
1        A         150
2        A         155
3        B         145
4        B         142
5        C         170
6        C         168

## Example: Footfall readings from different days or different customers ##
✅ Table 1: Meets the Between-Subjects Condition
- Each row is a unique unit.
Store   Time        Footfall
1       Morning     52
1       Morning     49
1       Afternoon   80
1       Afternoon   83
1       Evening     70
2       Morning     45
2       Morning     47
2       Afternoon   77
2       Evening     65

✅ 2. Within-Subjects / Repeated-Measures ANOVA
✔ Same subjects measured multiple times
✔ They experience all conditions
✔ Time or condition = within-subject factor
Example (Same lifters measured at 3 times)
Lifter   Time     Squat_1RM
1        Pre      150
1        Mid      155
1        Post     160
2        Pre      140
2        Mid      145
2        Post     150
3        Pre      165
3        Mid      170
3        Post     175


❌ Table 2: Does NOT Meet Between-Subjects Condition. It is a repeated measurements because each store/athlete is measured in 3 different time periods.
- Here the same unit (Store 1) is measured repeatedly across times. This requires repeated-measures, not between-subjects.

/short format
Store   Morning   Afternoon   Evening
1       50        80          70
2       45        77          65
3       60        90          85

/same but long format
Store   Time        Footfall
1       Morning     50
1       Afternoon   80
1       Evening     70
2       Morning     45
2       Afternoon   77
2       Evening     65

## **2B. Repeated-measures ANOVA = Within-Subjects**
**Scenario:** Same lifters measured 4 times.
Lifter	Week1	Week2	Week3	Week4
1	    100	    105	    108	    112
2	    120	    122	    125	    130
3	     90	    95	     98	    100

## **2C. Mixed design (between + within)**
**Scenario:** Program (between) × Time (within).
✔ One factor = Program (A vs B) → between-subjects
✔ One factor = Time (Pre vs Post) within-subjects
✔ Subjects belong to one group but measured over time
Lifter	Program	Week1	Week2	Week3
1	          A	   80	   82	   85
2	          A	   75	   78	   80
3	          B	   80	   85	   90
4	          B	   70	   76	   82


## END EXPLANATION 2. By Design

---
## BGN EXPLANATION 3. BY FACTOR TYPE
---
# 3. **BY FACTOR TYPE**
## **3A. Fixed-factor ANOVA**
All datasets qualify.
---
## **3B. Random-factor ANOVA**
**Scenario:** Coach is randomly sampled.
## **Simple random-factor design**
Coach   CJ_1RM
C1      140
C1      145
C2      150
C2      155
C3      135
C3      138


---
## **3C. Mixed (fixed + random)**
**Scenario:** Program = fixed, Coach = random.
## **Larger mixed model example (random coach + fixed program)**
Program   Coach   Athlete   Squat_1RM
A         C1      1         150
A         C1      2         152
A         C2      3         155
A         C2      4         157
B         C3      5         160
B         C3      6         162
B         C4      7         158
B         C4      8         161

Program = fixed factor
Coach = random factor
Athlete nested within Coach (if needed)
Could also add: Sex, Experience, Time, Equipment…
This becomes a multi-factor mixed ANOVA, perfectly valid and used in real research.

---
## END EXPLANATION 3. BY FACTOR TYPE
---

---
## BGN EXPLANATION 4. BY CELL STRUCTURE
---
# 4. **BY CELL STRUCTURE**
## **4A. Balanced ANOVA**
Program   Gender   Squat_1RM
A         M        160
A         M        158
A         F        130
A         F        132
B         M        170
B         M        168
B         F        140
B         F        142
---
## **4B. Unbalanced ANOVA**
**Scenario:** Unequal sample sizes.
Program   Deadlift_1RM
A         180
A         185
B         175
B         170
B         178
C         200

---
## END EXPLANATION 4. BY CELL STRUCTURE
---

---
## BGN EXPLANATION 5. ADDITIONAL DESIGN TYPE
---
# 5. **ADDITIONAL DESIGN TYPES**
## **5A. Randomized Block Design (Blocking/RBD)**
**Blocks:** Lifters
**Treatment:** Barbell Type
Lifter   Barbell   Squat_1RM
1        Standard  150
1        Power     152
1        Olympic   155
2        Standard  160
2        Power     165
2        Olympic   168
3        Standard  140
3        Power     142
3        Olympic   145

🔥 Key Difference between RBD and RM:
Repeated Measures:
We care about how the SAME subject responds across meaningful conditions
(e.g., time, load, session).

Randomized Block Design:
We do NOT care about differences in subjects — they are included ONLY to reduce noise. We care about the result not the athletes.

for instance:
## A-Store 1 Morning, Afternoon, Evening
Store   Time        Footfall
1       Morning     120
1       Afternoon   150
1       Evening     200

👉 This could be repeated measures
👉 OR it could be a randomized block design
depending on the research question

- If your research question is:"Does footfall change by time of day?"
Then Time = repeated-measures factor
Store = random effect / blocking factor
→ Mixed or repeated-measures ANOVA

- If your research question is: "Which promotion type increases footfall?"
(but stores differ naturally)
Then:
Store = block
Promotion = treatment
→ Randomized Block ANOVA

Identical data structure, different purpose.

## B - Barbell Example (Your RBD Dataset)
Lifter   Barbell   Squat_1RM
1        Standard  150
1        Power     152
1        Olympic   155
2        Standard  160
2        Power     165
2        Olympic   168
3        Standard  140
3        Power     142
3        Olympic   145

Here:
You do NOT care how lifter 1 changes across barbells.
You ONLY care about barbell type.
Lifters differ strongly → they are blocking units (treated as random variability).

---
## **5B. Nested/Hierarchical ANOVA**
This is when lower-level units belong to only one higher-level unit, and do NOT cross the factor levels.
Gym → Athletes (Athlete A1 is only in Gym 1). athletes are nested within gyms, not shared across them.
**Scenario:** Athletes nested within Gyms.
Gym   Athlete   Bench_1RM
G1    A1        110
G1    A2        115
G1    A3        120
G2    A4        125
G2    A5        130
G2    A6        128

---
## **5C. Crossed ANOVA**
What does “crossed” mean?
A factor is crossed when every level of one factor appears with every level of another factor.
Visual example: Program × Gender
	        Male	Female
Program A	   ✔	    ✔
Program B	   ✔	    ✔
Every program has both genders → crossed design.
Already represented by 2-way and 3-way designs.

Opposite of crossed = nested
If men appear only in Program A and women only in Program B → not crossed → nested.

---
## END EXPLANATION 5. ADDITIONAL DESIGN TYPE
---

---
## BGN EXPLANATION 6. SPECIAL CASE — ANCOVA
---
# 6. **SPECIAL CASE — ANCOVA**
ANCOVA is a blend of ANOVA + Regression.
- ANOVA compares group means (e.g., Program A vs Program B)
- Regression adjusts for continuous variables that influence the outcome (e.g., Bodyweight)

⭐ ANCOVA answers this question:
Do Programs A and B differ in Squat 1RM, after statistically controlling for bodyweight?

🤔 Why do this?
Because heavier lifters naturally squat more — so bodyweight may distort the comparison.

Example dataset:
Program   Bodyweight   Squat_1RM
A         80           150
A         82           152
A         78           148
B         90           170
B         88           168
B         92           172

⚠️ Key ANCOVA Assumptions
- 1. Linearity
Relationship between covariate and outcome is linear.
- 2. Homogeneity of regression slopes
The covariate affects each group equally.
(like saying weight influences squat the same way in Program A and B)
- 3. Independence of covariate and factor
Groups should not differ massively in the covariate (mild differences are OK).
---
## END EXPLANATION 6. SPECIAL CASE — ANCOVA
---

---
## BGN EXPLANATION 7. VARIANCE / ASSUMPTION CORRECTIONS
---
# 7. **VARIANCE / ASSUMPTION CORRECTIONS**
## **7A. Welch's ANOVA (unequal variances)**
Program   Press_1RM
A         60
A         61
A         62
B         70
B         80
B         85
C         90
C         120
C         150
---
## **7B. Greenhouse–Geisser / Huynh–Feldt RM ANOVA**
Requires repeated measures with likely sphericity violation.
sphericity is the assumption that differences between all pairs of repeated conditions have equal variancess. it's violation is common in repeated measures, necessitating the GG correction.

Lifter   T1   T2   T3   T4
1        90   95   110  118
2        85   89   101  112
3        100  104  117  130
4        95   99   108  115
**Note:** Minitab does not automatically compute GG/HF; user must verify sphericity.

---
## END EXPLANATION 7. VARIANCE / ASSUMPTION CORRECTIONS
---

# procedure-for-anova
## Minitab Procedure
### 1. Do the ANOVA First
Stat > ANOVA > General Linear Model > Fit General Linear Model 
- under graphs: check 4-in-one
- click ok.
### 2. Then do the normality test on the RESI column
Stat > Basic Statistics > Normality Test
- variable: RESI
- test for Normality: Anderson-Darling
! this will show a QQ-graph.

#### Decision Rule
Hypotheses
>Null hypothesis (H₀): The residuals are normally distributed.
>Alternative hypothesis (H₁): The residuals are not normally distributed.
>we use the p-value. the AD is the test statistic. so we would need the Critical value from a table.
At a significance level (α) is 0.05 (5%).
- If p-value ≤ 0.05: Reject H₀ → Conclude there is sufficient evidence that the residuals are not normally distributed.
- If p-value > 0.05: Fail to reject H₀ → There is insufficient evidence to say the residuals are not normally distributed.

### 3. Then do the Equal Variances Check test on the original response column
>to be able to use an ANOVA we need:
>> 0. anovas are not that dependent on size, like inteh central limit theorem where we have a rought heuristics value os 30. we can have less than this in ANOVA, it's just that larger n improves the model.
>> 1. Independence or Observations/Residuals. You see this in the 4-in-1 plot "versus order" .if it is a randomr fluctuation, no patterns->satisfied.
>> 2. normality of residuals
>> 3. Homogeneity of Variances (Equal Variances / Homoscedasticity). You check in the 4-in-1 graphs Residuals vs. Fitted Values plot: Points should have constant vertical spread (no funnel shape—narrower on one end, wider on the other).
>> to check Homogeneity of Variances(Equal Variances / Homoscedasticity) you do:
Stat > ANOVA > Test for Equal Variances
- Response Variable is the original Response Variable (not RESI)
- Factors are the original factors.
#### Decision Rule
- If p-value ≤ 0.05: Reject H₀ → Conclude there is sufficient evidence that the variances are not equally distributed.
- If p-value > 0.05: Fail to reject H₀ → There is insufficient evidence to say the variances are not equally distributed.

# about all these 1.2.3.4 ANOVA satisfaction points.
> if you get normality of residuals and the remaining points also clear, the ANOVA test results hold. if you didn't get normality of residuals or a pass in any of the others tests, you would need to transform the dataset in the initial response variable.
>> If no simple transformation works, use:
Non-parametric tests (Kruskal-Wallis instead of one-way ANOVA).

# graph-interpretation
## Minitab graphs (four-in-one)
### 1. Normal Probability Plot(also called QQ( Quantile-Quantile) plot) (top-left)
- Points should fall roughly along the straight diagonal line for normality
### 2. Versus Fits (top-right: Residuals vs. Fitted Values)
- Points should be randomly scattered around the horizontal line at residual = 0.
- No patterns (e.g., no funnel shape or curves).
- Constant spread (homoscedasticity) and no systematic trends (linearity).
### 3. Histogram (bottom-left)
- Shows the distribution of residuals. It should be roughly symmetric and bell-shaped. It can highlight some skewness or outliers.
### 4. Versus Order (bottom-right: Residuals vs. Observation Order)
- Plots residuals in the order data were collected. Checks for independence—residuals should show no patterns (e.g., no trends, cycles, or autocorrelation, which could occur with time-series or ordered data).
- Points should fluctuate randomly around 0 with no trends, drifts, or systematic patterns over the observations to show normality.

# further-tests
if after doing the ANOVA and checking its normality/homogeneity/independence of residuals hold, and if in the ANOva test under one factor you have p-value less than the significance level, and as long as you have at least 3 levels of a factor you can do a a posteriori test to check which pairwise comparisons are significant.

To do this you choose:
Stat > ANOVA > General Linear Model > Comparisons
Choose:
- Response Variable
- Method: Tukey and Bonferroni
- Choose: the factor which you got a p-value < significance level

You will get a table with both methods.->Tukey is Less conservative, Bonferroni is more conservative.

📌 Quick Ranking (Most → Least conservative under pairwise comparisons)
    Scheffé
    Bonferroni (very conservative)
    Tukey HSD (moderate)
    Fisher LSD (least conservative; high Type I error risk)

To check the conclusions you can create an Interactions Plot to see the pairs
Stats > ANOVA > Interaction Plot
> If lines cross → interaction.

You can also do a Main effects Plot
It will plot the average mean, and if you have as factors say like the anova 2-way example about: Men/Women and Program A/B and as response variable Squat_1RM, you will see for instance, that Program B produces above average results and that men get higher average "squats"

# terminology
- Factors -> always categorical
- Each Factor Has levels(Gender: Male, Female)
- Groups = Levels
- ANOVA is a regression model. Minitab will produce the model. 
Squat = β0 ​ +β1​(Program) + β2​(Gender) + β3​(Program × Gender) + ϵ
And same as a regression model you have R-Squared to see its fit.
- Multicollinearity = when two or more predictors(Xᵢ) give the same information. 
Imagine you ask three people the same question:
Person A says the same thing as Person B
Person C also repeats their answer
You don’t actually have three separate pieces of information — just one repeated three times.
This is what multicollinearity is inside regression.

Multicolinearity ONLY affects:
- - statistical significance
- - interpretability of coefficients

- VIF = Variance Inflation Factor
It tells you whether a predictor (X variable) is too correlated with other predictors, which causes:
- unstable coefficient estimates
- inflated standard errors
- unreliable p-values
- weird or opposite-sign coefficients

- - This problem is called multicollinearity.

🔢 What VIF measures
For each predictor Xi
VIFᵢ = 1 / (1−Rᵢ^2)

where 
Rᵢ^2 comes from a regression where
Xᵢ is predicted by all the other predictors.

So VIF literally answers:

How well can the other predictors "explain" this predictor?

If they explain a lot → Xᵢ is redundant → VIF large.

🟩 How to read VIF in Minitab
VIF value	Interpretation
1:	        Perfect — no multicollinearity ("no inflation")
1–5:	    Acceptable
5–10:	    Problematic — strong correlation with other predictors
> 10	    Severe multicollinearity — coefficients unstable

- About Regression Variables
Portuguese term	       English term	                   Symbol in regression
Variável explicada	   dependent variable, response	    Y
Variável explicativa   independent variable, predictor	X

- Bias-Variance Trade-off
We want low bias, low variance, but in practice, this doesnt happen.
- - In Simple models → high bias, low variance
- - In Complex models → low bias, high variance.

