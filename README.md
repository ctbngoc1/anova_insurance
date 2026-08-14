# Multi-factor ANOVA on US Health Insurance Charges

## Overview

This project applies Multi-factor Analysis of Variance (Multi-factor ANOVA) to examine how various demographic and lifestyle factors influence medical insurance charges as part of a university course assignment. The analysis focuses on k-factor ANOVA method with $k \geq 2$, allowing for the assessment of multiple factors simultaneously and providing insights into their effects on medical insurance costs. The code was developed and executed using RStudio.

## Data

This project uses the insurance dataset, which contains 1338 observations and 7 variables, including demographic, lifestyle and health-related information on individuals in the United States. The dataset is publicly available at: <https://www.kaggle.com/datasets/mirichoi0218/insurance>

The outcome variable of interest is *charges*, representing the medical insurance costs. All remaining variables were treated as explanatory factors in multi-factor ANOVA.

The dataset contains no missing values. Categorical variables (*sex, smoker,* and *region*) were converted into factor variables. Numeric variables (*age, bmi,* and *children*) were discretized into meaningful categories and then treated as factor variables for ANOVA analysis. Additionally, 7 outlier observations were identified and removed from the dataset.

## Methods

Group sample sizes across factor-level combinations were examined. Since multiple observations were present within each group and group sizes were unequal, a replicated multi-factor ANOVA with an unbalanced design was employed.

*Interaction effects* were evaluated hierarchically, starting from the six-way interaction and proceeding down to two-way interactions. Because all six factors appeared in at least one significant two-way interaction, *main effects* were not interpreted in isolation. Afterwards, *post hoc Tukey’s HSD tests* were performed to examine differences in mean insurance charges across relevant factor-level combinations for each interaction.

The ANOVA model assumptions were assessed using residual diagnostic plots, the Shapiro-Wilk normality test and the Levene’s homoscedasticity test. When violations were detected, a Box-Cox transformation of the response variable was considered and applied to improve model adequacy.

## Results

Among all interaction terms considered, only 7 two-way interactions were identified as statistically significant: *age-children, sex-bmi, sex-smoker, bmi-children, bmi-smoker, children-smoker,* and *smoker-region*. Consequently, the final ANOVA model explains insurance charges through 6 factors and these 7 significant two-way interactions. The multi-factor ANOVA analysis indicates that medical insurance charges are primarily driven by interaction effects among factors rather than isolated main effects. Specifically, the effect of each factor on insurance charges depends on the factors it significantly interacts with.

Post hoc Tukey’s HSD tests revealed statistically significant differences in mean insurance charges across most combinations of factor levels within these interactions. In a few cases, certain group combinations did not differ significantly, such as between males and females within the lower BMI category, and between non-smokers across some demographic groups.

Smoking status is involved in 4 out of the 7 significant two-way interactions. This shows that smoking consistently modifies the effect of other factors on insurance charges. Also, according to post hoc results, most significant differences occur between smoker vs non-smoker combinations, and some non-smoker subgroup comparisons aren't significantly different. Therefore, smoking status is considered a key factor that amplifies cost differences across other variables.

Assumption diagnostics indicated that the ANOVA model violated the normality assumption. As the Box-Cox transformation didn't improve normality, the original ANOVA model was retained. Consequently, the inferential results should be interpreted with caution. Alternative modeling approaches may be more appropriate for drawing robust statistical inferences from the insurance dataset.
