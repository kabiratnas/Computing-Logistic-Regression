# Logistic Regression Analysis for Instagram Users

## Objective

The objective of this analysis is to demonstrate how to use logistic regression to compare the probability of Instagram usage between two groups—women and men—using sample proportions. We aim to compute and interpret the logistic regression coefficients, including the intercept (log-odds for men), the slope (difference in log-odds between women and men), and the corresponding odds ratio.

## Background

We have a sample of \( n = 1069 \) young persons with the following sample proportions:
- **Women:** 61.08% are Instagram users.
- **Men:** 43.98% are Instagram users.

The data is coded as follows:
- \( x = 1 \) for women
- \( x = 0 \) for men
- \( y \) is an indicator variable for being an Instagram user

We use the logistic regression model:
\[
\log\left(\frac{p}{1-p}\right) = b_0 + b_1 \cdot x
\]
where:
- \( b_0 \) is the intercept (log-odds for men),
- \( b_1 \) is the slope (the difference in log-odds between women and men).

## R Code

The following R code calculates the log-odds, the coefficients \( b_0 \) and \( b_1 \), and the corresponding odds ratio.

```r
# Given sample proportions:
p_women <- 0.6108
p_men   <- 0.4398

# Calculate log-odds for each group:
log_odds_women <- log(p_women / (1 - p_women))
log_odds_men   <- log(p_men / (1 - p_men))

# Print log-odds (rounded to 4 decimal points)
cat("Log-odds for women:", round(log_odds_women, 4), "\n")
cat("Log-odds for men:  ", round(log_odds_men, 4), "\n")

# In the logistic regression model:
# For men (x = 0): log(odds) = b0, so b0 = log_odds_men.
# For women (x = 1): log(odds) = b0 + b1, so b1 = log_odds_women - log_odds_men.
b0 <- log_odds_men
b1 <- log_odds_women - log_odds_men

# Print the coefficients:
cat("b0 (Intercept) =", round(b0, 4), "\n")
cat("b1 (Slope)     =", round(b1, 4), "\n")

# Exponentiating b1 gives the odds ratio:
odds_ratio <- exp(b1)
cat("Odds Ratio (exp(b1)) =", round(odds_ratio, 4), "\n")

Results
When you run the code, you should obtain the following output (all values rounded to 4 decimal points):

Log-odds for women: 0.4507
Log-odds for men: -0.2420
Intercept (
𝑏
0
b 
0
​
 ) for men: -0.2420
Slope (
𝑏
1
b 
1
​
 ): 0.6927
Odds Ratio (
𝑒
𝑏
1
e 
b 
1
​
 
 ): 1.9990
Interpretation
For Men (Reference Group):
The log-odds of being an Instagram user for men is 
−
0.2420
−0.2420. This translates to odds of:

Odds for men
=
𝑒
−
0.2420
≈
0.785.
Odds for men=e 
−0.2420
 ≈0.785.
This means that, for men, the odds of being an Instagram user are approximately 0.785.

For Women:
The log-odds for women are 0.6927 higher than for men. Thus, the log-odds for women are:

−
0.2420
+
0.6927
=
0.4507.
−0.2420+0.6927=0.4507.
Converting these log-odds to odds:

Odds for women
=
𝑒
0.4507
≈
1.569.
Odds for women=e 
0.4507
 ≈1.569.
Odds Ratio:
The slope 
𝑏
1
b 
1
​
  of 0.6927, when exponentiated, gives:

𝑒
0.6927
≈
1.9990.
e 
0.6927
 ≈1.9990.
This odds ratio means that the odds of being an Instagram user are about 2 times higher for women than for men.

In Plain Language:
This analysis shows that if you compare a man and a woman, a woman is roughly twice as likely to be an Instagram user as a man.
