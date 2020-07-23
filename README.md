# Data_Science_Linear_Regression
# HarvardX: PH125.7x | Data Science: Linear Regression

## Abstract
This is the 7th course in the HarvardX Professional Certificate in Data Science, a series of courses that prepare you to do data analysis in R, from simple computations to machine learning.

The textbook for the Data Science course series is [freely available online](https://rafalab.github.io/dsbook/).

## Learning Objectives
- How linear regression was originally developed by Galton
- What confounding is and how to detect it
- How to examine the relationships between variables by implementing linear regression in R

## Course Overview

There are three major sections in this course: introduction to linear regression, linear models, and confounding.

### Introduction to Linear Regression

In this section, you’ll learn the basics of linear regression through this course’s motivating example, the data-driven approach used to construct baseball teams. You’ll also learn about correlation, the correlation coefficient, stratification, and the variance explained.

### Linear Models

In this section, you’ll learn about linear models. You’ll learn about least squares estimates, multivariate regression, and several useful features of R, such as tibbles, lm, do, and broom. You’ll learn how to apply regression to baseball to build a better offensive metric.

### Confounding

In the final section of the course, you’ll learn about confounding and several reasons that correlation is not the same as causation, such as spurious correlation, outliers, reversing cause and effect, and confounders. You’ll also learn about Simpson’s Paradox.

## Introduction to Linear Regression

In the Introduction to Regression section, you will learn the basics of linear regression.

After completing this section, you will be able to:
- Understand how Galton developed linear regression.
- Calculate and interpret the sample correlation.
- Stratify a dataset when appropriate.
- Understand what a bivariate normal distribution is.
- Explain what the term variance explained means.
- Interpret the two regression lines.
    
This section has three parts: Baseball as a Motivating Example, Correlation, and Stratification and Variance Explained.

The textbook for this section is available [here](https://rpubs.com/faisalcep/dsLinearRegression)

## Assessment 1 - Motivating Example: Moneyball

1. What is the application of statistics and data science to baseball called?

- [ ] A. Moneyball
- [X] B. Sabermetrics
- [ ] C. The “Oakland A’s Approach”
- [ ] D. There is no specific name for this; it’s just data science.

## Assessment 2 - Baseball Basics

1. Which of the following outcomes is not included in the batting average?

- [ ] A. A home run
- [X] B. A base on balls
- [ ] C. An out
- [ ] D. A single

2. Why do we consider team statistics as well as individual player statistics?

- [X] A. The success of any individual player also depends on the strength of their team.
- [ ] B. Team statistics can be easier to calculate.
- [ ] C. The ultimate goal of sabermetrics is to rank teams, not players.

## Assessment 3 - Bases on Balls or Stolen Bases?

1. You want to know whether teams with more at-bats per game have more runs per game. What R code below correctly makes a scatter plot for this relationship?

- [ ] A.
```{r}
Teams %>% filter(yearID %in% 1961:2001 ) %>%
    ggplot(aes(AB, R)) + 
    geom_point(alpha = 0.5)
```
- [X] B.
```{r}
Teams %>% filter(yearID %in% 1961:2001 ) %>%
    mutate(AB_per_game = AB/G, R_per_game = R/G) %>%
    ggplot(aes(AB_per_game, R_per_game)) + 
    geom_point(alpha = 0.5)
```
- [ ] C.
```{r}
Teams %>% filter(yearID %in% 1961:2001 ) %>%
    mutate(AB_per_game = AB/G, R_per_game = R/G) %>%
    ggplot(aes(AB_per_game, R_per_game)) + 
    geom_line()
```
- [ ] D.
```{r}
Teams %>% filter(yearID %in% 1961:2001 ) %>%
    mutate(AB_per_game = AB/G, R_per_game = R/G) %>%
    ggplot(aes(R_per_game, AB_per_game)) + 
    geom_point()
```
2. What does the variable “SOA” stand for in the Teams table?

- [ ] A. sacrifice out
- [ ] B. slides or attempts
- [X] C. strikeouts by pitchers
- [ ] D. accumulated singles

## Assessment 4 - Correlation

1. While studying heredity, Francis Galton developed what important statistical concept?

- [ ] A. Standard deviation
- [ ] B. Normal distribution
- [X] C. Correlation
- [ ] D. Probability

2. The correlation coefficient is a summary of what?

- [X] A. The trend between two variables
- [ ] B. The dispersion of a variable
- [ ] C. The central tendency of a variable
- [ ] D. The distribution of a variable

## Assessment 5- Correlation Coefficient

1. Below is a scatter plot showing the relationship between two variables, x and y.

![Scatter plot](https://user-images.githubusercontent.com/17474099/88270104-6a324080-ccd5-11ea-9cbd-90df12de22bd.png)

From this figure, the correlation between x and y appears to be about:

- [X] A. -0.9
- [ ] B. -0.2
- [ ] C. 0.9
- [ ] D. 2

## Assessment 6- Sample Correlation is a Random Variable

1. Instead of running a Monte Carlo simulation with a sample size of 25 from our 179 father-son pairs, we now run our simulation with a sample size of 50.

Would you expect the mean of our sample correlation to increase, decrease, or stay approximately the same?

- [ ] A. Increase
- [ ] B. Decrease
- [X] C. Stay approximately the same

2. Instead of running a Monte Carlo simulation with a sample size of 25 from our 179 father-son pairs, we now run our simulation with a sample size of 50.

Would you expect the standard deviation of our sample correlation to increase, decrease, or stay approximately the same?

- [ ] A. Increase
- [X] B. Decrease
- [ ] C. Stay approximately the same

## Assessment 7- Anscombe’s Quartet/Stratification

1. Look at the figure below. The slope of the regression line in this figure is equal to what, in words?

![Scatter plot of son and father heights with son heights on the y-axis and father heights on the x-axis](https://user-images.githubusercontent.com/17474099/88270632-373c7c80-ccd6-11ea-8dec-eb7315a564b1.png)

- [X] A. Slope = (correlation coefficient of son and father heights) * (standard deviation of sons’ heights / standard deviation of fathers’ heights)
- [ ] B. Slope = (correlation coefficient of son and father heights) * (standard deviation of fathers’ heights / standard deviation of sons’ heights)
- [ ] C. Slope = (correlation coefficient of son and father heights) / (standard deviation of sons’ heights * standard deviation of fathers’ heights)
- [ ] D. Slope = (mean height of fathers) - (correlation coefficient of son and father heights * mean height of sons).

2. Why does the regression line simplify to a line with intercept zero and slope when we standardize our x and y variables? Try the simplification on your own first!

A. When we standardize variables, both x and y will have a mean of one and a standard deviation of zero. When you substitute this into the formula for the regression line, the terms cancel out until we have the following equation:  $y_i=px_i$.

B. When we standardize variables, both x and y will have a mean of zero and a standard deviation of one. When you substitute this into the formula for the regression line, the terms cancel out until we have the following equation: $y_i = px_i$.

C. When we standardize variables, both x and y will have a mean of zero and a standard deviation of one. When you substitute this into the formula for the regression line, the terms cancel out until we have the following equation:  yi=pxi

.

    What is a limitation of calculating conditional means?

A. Each stratum we condition on (e.g., a specific father’s height) may not have many data points.
B. Because there are limited data points for each stratum, our average values have large standard errors.
C. Conditional means are less stable than a regression line.
D. Conditional means are a useful theoretical tool but cannot be calculated.
Assessment 8- Bivariate Normal Distribution

    A regression line is the best prediction of Y given we know the value of X when:

A. X and Y follow a bivariate normal distribution.
B. Both X and Y are normally distributed.
C. Both X and Y have been standardized.
D. There are at least 25 X-Y pairs.

    Which one of the following scatterplots depicts an x and y distribution that is NOT well-approximated by the bivariate normal distribution?

A.

Assessment 9- Variance Explained

    We previously calculated that the correlation coefficient between fathers’ and sons’ heights is 0.5.

Given this, what percent of the variation in sons’ heights is explained by fathers’ heights?

A. 0%
B. 25%
C. 50%
D. 75%
Linear Models Overview

In the Linear Models section, you will learn how to do linear regression.

After completing this section, you will be able to:

    Use multivariate regression to adjust for confounders.
    Write linear models to describe the relationship between two or more variables.
    Calculate the least squares estimates for a regression model using the lm function.
    Understand the differences between tibbles and data frames.
    Use the do function to bridge R functions and the tidyverse.
    Use the tidy, glance, and augment functions from the broom package.
    Apply linear regression to measurement error models.

This section has four parts: Introduction to Linear Models, Least Squares Estimates, Tibbles, do, and broom, and Regression and Baseball.

The textbook for this section is available here
Assessment 1- Confounding: Are BBs More Predictive?

    Why is the number of home runs considered a confounder of the relationship between bases on balls and runs per game?

A. Home runs is not a confounder of this relationship.
B. Home runs are the primary cause of runs per game.
C. The correlation between home runs and runs per game is stronger than the correlation between bases on balls and runs per game.
D. Players who get more bases on balls also tend to have more home runs; in addition, home runs increase the points per game.
Assessment 2- Stratification and Multivariate Regression

    As described in the video, when we stratified our regression lines for runs per game vs. bases on balls by the number of home runs, what happened?

A. The slope of runs per game vs. bases on balls within each stratum was reduced because we removed confounding by home runs.
B. The slope of runs per game vs. bases on balls within each stratum was reduced because there were fewer data points.
C. The slope of runs per game vs. bases on balls within each stratum increased after we removed confounding by home runs.
D. The slope of runs per game vs. bases on balls within each stratum stayed about the same as the original slope.
Assessment 3- Linear Models

    We run a linear model for sons’ heights vs. fathers’ heights using the Galton height data, and get the following results:

> lm(son ~ father, data = galton_heights)

Call:
lm(formula = son ~ father, data = galton_heights)

Coefficients:
(Intercept)    father  
    35.71       0.50  

Interpret the numeric coefficient for “father.”

A. For every inch we increase the son’s height, the predicted father’s height increases by 0.5 inches.
B. For every inch we increase the father’s height, the predicted son’s height grows by 0.5 inches.
C. For every inch we increase the father’s height, the predicted son’s height is 0.5 times greater.

    We want the intercept term for our model to be more interpretable, so we run the same model as before but now we subtract the mean of fathers’ heights from each individual father’s height to create a new variable centered at zero.

galton_heights <- galton_heights %>%
    mutate(father_centered=father - mean(father))

We run a linear model using this centered fathers’ height variable.

> lm(son ~ father_centered, data = galton_heights)

Call:
lm(formula = son ~ father_centered, data = galton_heights)

Coefficients:
(Intercept)    father_centered  
    70.45          0.50  

Interpret the numeric coefficient for the intercept.

A. The height of a son of a father of average height is 70.45 inches.
B. The height of a son when a father’s height is zero is 70.45 inches.
C. The height of an average father is 70.45 inches.
Assessment 4- Least Squares Estimates (LSE)

    The following code was used in the video to plot RSS with  β0=25

    .

beta1 = seq(0, 1, len=nrow(galton_heights))
results <- data.frame(beta1 = beta1,
                      rss = sapply(beta1, rss, beta0 = 25))
results %>% ggplot(aes(beta1, rss)) + geom_line() + 
  geom_line(aes(beta1, rss), col=2)

In a model for sons’ heights vs fathers’ heights, what is the least squares estimate (LSE) for  β1
if we assume  β0^

is 36?

A. 0.65
B. 0.5
C. 0.2
D. 12

    The least squares estimates for the parameters  β0,β1...βn

    minimize the residual sum of squares.

Assessment 5- The lm Function

    Run a linear model in R predicting the number of runs per game based on the number of bases on balls and the number of home runs. Remember to first limit your data to 1961-2001.

What is the coefficient for bases on balls?

A. 0.39
B. 1.56
C. 1.74
D. 0.027
Assessment 6- LSE are Random Variables

    We run a Monte Carlo simulation where we repeatedly take samples of N = 100 from the Galton heights data and compute the regression slope coefficients for each sample:

B <- 1000
N <- 100
lse <- replicate(B, {
  sample_n(galton_heights, N, replace = TRUE) %>% 
    lm(son ~ father, data = .) %>% .$coef 
})

lse <- data.frame(beta_0 = lse[1,], beta_1 = lse[2,]) 

What does the central limit theorem tell us about the variables beta_0 and beta_1?

A. They are approximately normally distributed.
B. The expected value of each is the true value of $\beta_0$ and $\beta_1$ (assuming the Galton heights data is a complete population).
C. The central limit theorem does not apply in this situation.
D. It allows us to test the hypothesis that β0=0
and β0=1

.

    In an earlier video, we ran the following linear model and looked at a summary of the results.

$\beta_0 $
> mod <- lm(son ~ father, data = galton_heights)
> summary(mod)

Call:
lm(formula = son ~ father, data = galton_heights)

Residuals:
   Min     1Q  Median     3Q    Max 
-5.902  -1.405  0.092    1.342  8.092 

Coefficients:
                 Estimate  Std. Error  t value     Pr(>|t|)  
(Intercept)     35.7125     4.5174       7.91    2.8e-13 ***
father           0.5028     0.0653       7.70    9.5e-13 ***
---
Signif. codes:  0 ‘***’ 0.001 ‘**’ 0.01 ‘*’ 0.05 ‘.’ 0.1 ‘ ’ 1
$\beta_0 $

What null hypothesis is the second p-value (the one in the father row) testing?

A. β1=1
, where β1 is the coefficient for the variable “father.”
B. β1=0.503, where β1

is the coefficient for the variable “father.”
C. $\beta_1 = 0$, where $\beta_1$ is the coefficient for the variable "father."
Assessment 7- Predicted Variables are Random Variables

    Which R code(s) below would properly plot the predictions and confidence intervals for our linear model of sons’ heights?

galton_heights %>% ggplot(aes(father, son)) +
  geom_point() +
  geom_smooth()

B.

galton_heights %>% ggplot(aes(father, son)) +
  geom_point() +
  geom_smooth(method = "lm")

C.

model <- lm(son ~ father, data = galton_heights)
predictions <- predict(model, interval = c("confidence"), level = 0.95)
data <- as.tibble(predictions) %>% bind_cols(father = galton_heights$father)

ggplot(data, aes(x = father, y = fit)) +
  geom_line(color = "blue", size = 1) + 
  geom_ribbon(aes(ymin=lwr, ymax=upr), alpha=0.2) + 
  geom_point(data = galton_heights, aes(x = father, y = son))

model <- lm(son ~ father, data = galton_heights)
predictions <- predict(model)
data <- as.tibble(predictions) %>% bind_cols(father = galton_heights$father)

ggplot(data, aes(x = father, y = fit)) +
  geom_line(color = "blue", size = 1) + 
  geom_point(data = galton_heights, aes(x = father, y = son))

Assessment 8- Advanced dplyr: Tibbles

    What problem do we encounter when we try to run a linear model on our baseball data, grouping by home runs?

A. There is not enough data in some levels to run the model. B. The lm function does not know how to handle grouped tibbles. C. The results of the lm function cannot be put into a tidy format.

    Tibbles are similar to what other class in R?

A. Vectors
B. Matrices
C. Data frames
D. Lists
Assessment 9- Tibbles: Differences from Data Frames

    What are some advantages of tibbles compared to data frames?

A. Tibbles display better.
B. If you subset a tibble, you always get back a tibble.
C. Tibbles can have complex entries.
D. Tibbles can be grouped.
Assessment 10- do

    What are two advantages of the do command, when applied to the tidyverse?

A. It is faster than normal functions.
B. It returns useful error messages.
C. It understands grouped tibbles.
D. It always returns a data.frame.

    You want to take the tibble dat, which we’ve been using in this video, and run the linear model R ~ BB for each strata of HR. Then you want to add three new columns to your grouped tibble: the coefficient, standard error, and p-value for the BB term in the model.

You’ve already written the function get_slope, shown below.

get_slope <- function(data) {
  fit <- lm(R ~ BB, data = data)
  sum.fit <- summary(fit)

  data.frame(slope = sum.fit$coefficients[2, "Estimate"], 
             se = sum.fit$coefficients[2, "Std. Error"],
             pvalue = sum.fit$coefficients[2, "Pr(>|t|)"])
}

What additional code could you write to accomplish your goal?

dat %>% 
  group_by(HR) %>% 
  do(get_slope)

B.

dat %>% 
  group_by(HR) %>% 
  do(get_slope(.))

dat %>% 
  group_by(HR) %>% 
  do(slope = get_slope(.))

dat %>% 
  do(get_slope(.))

Assessment 11- broom

    The output of a broom function is always what?

A. A data.frame
B. A list
C. A vector

    You want to know whether the relationship between home runs and runs per game varies by baseball league. You create the following dataset:

dat <- Teams %>% filter(yearID %in% 1961:2001) %>%
  mutate(HR = HR/G,
         R = R/G) %>%
  select(lgID, HR, BB, R)

What code would help you quickly answer this question?

A.

dat %>% 
  group_by(lgID) %>% 
  do(tidy(lm(R ~ HR, data = .), conf.int = T)) %>% 
  filter(term == "HR")

dat %>% 
  group_by(lgID) %>% 
  do(glance(lm(R ~ HR, data = .)))

dat %>% 
  do(tidy(lm(R ~ HR, data = .), conf.int = T)) %>% 
  filter(term == "HR")

dat %>% 
  group_by(lgID) %>% 
  do(mod = lm(R ~ HR, data = .))

Assessment 12- Building a Better Offensive Metric for Baseball

    What is the final linear model we use to predict runs scored per game?

A. lm(R ~ BB + HR)
B. lm(HR ~ BB + singles + doubles + triples)
C. lm(R ~ BB + singles + doubles + triples + HR)
D. lm(R ~ singles + doubles + triples + HR)

    We want to estimate runs per game scored by individual players, not just by teams. What summary metric do we calculate to help estimate this?

Look at the code from the video for a hint:

pa_per_game <- Batting %>% 
  filter(yearID == 2002) %>% 
  group_by(teamID) %>%
  summarize(pa_per_game = sum(AB+BB)/max(G)) %>% 
  .$pa_per_game %>% 
  mean

A. pa_per_game: the mean number of plate appearances per team per game for each team
B. pa_per_game: the mean number of plate appearances per game for each player
C. pa_per_game: the number of plate appearances per team per game, averaged across all teams

    Imagine you have two teams. Team A is comprised of batters who, on average, get two bases on balls, four singles, one double, and one home run. Team B is comprised of batters who, on average, get one base on balls, six singles, two doubles, and one triple.

Which team scores more runs, as predicted by our model?

A. Team A
B. Team B
C. Tie
D. Impossible to know
Assessment 13- On Base Plus Slugging (OPS)

    The on-base-percentage plus slugging percentage (OPS) metric gives the most weight to:

A. Singles
B. Doubles
C. Triples
D. Home Runs
Assessment 14- Regression Fallacy

    What statistical concept properly explains the “sophomore slump”?

A. Regression to the mean
B. Law of averages
C. Normal distribution
Assessment 15- Measurement Error Models

    In our model of time vs. observed_distance, the randomness of our data was due to:

A. sampling B. natural variability C. measurement error

    Which of the following are important assumptions about the measurement errors in this experiment?

A. The measurement error is random
B. The measurement error is independent
C. The measurement error has the same distribution for each time i

    Which of the following scenarios would violate an assumption of our measurement error model?

A. The experiment was conducted on the moon. B. There was one position where it was particularly difficult to see the dropped ball. C. The experiment was only repeated 10 times, not 100 times.
Confounding Overview

In the Confounding section, you will learn what is perhaps the most important lesson of statistics: that correlation is not causation.

After completing this section, you will be able to:

    Identify examples of spurious correlation and explain how data dredging can lead to spurious correlation.
    Explain how outliers can drive correlation and learn to adjust for outliers using Spearman correlation.
    Explain how reversing cause and effect can lead to associations being confused with causation.
    Understand how confounders can lead to the misinterpretation of associations.
    Explain and give examples of Simpson’s Paradox.

This section has one part: Correlation is Not Causation.

The textbook for this section is available here
Assessment 1- Correlation is Not Causation: Spurious Correlation

    In the video, we ran one million tests of correlation for two random variables, X and Y.

How many of these correlations would you expect to have a significant p-value (p>0.05), just by chance?

A. 5,000
B. 50,000
C. 100,000
D. It’s impossible to know

    Which of the following are examples of p-hacking?

A. Looking for associations between an outcome and several exposures and only reporting the one that is significant.
B. Trying several different models and selecting the one that yields the smallest p-value.
C. Repeating an experiment multiple times and only reporting the one with the smallest p-value.
D. Using a Monte Carlo simulations in an analysis.
Assessment 2- Correlation is Not Causation: Outliers

    The Spearman correlation coefficient is robust to outliers because:

A. It drops outliers before calculating correlation.
B. It is the correlation of standardized values.
C. It calculates correlation between ranks, not values.
Assessment 3- Correlation is Not Causation: Reversing Cause and Effect

    Which of the following may be examples of reversed cause and effect?

A. Past smokers who have quit smoking may be more likely to die from lung cancer.
B. Tall fathers are more likely to have tall sons. C. People with high blood pressure tend to have a healthier diet.
D. Individuals in a low social status have a higher risk of schizophrenia.
Assessment 4- Correlation is Not Causation: Confounderss

    What can you do to determine if you are misinterpreting results because of a confounder?

A. Nothing, if the p-value says the result is significant, then it is.
B. More closely examine the results by stratifying and plotting the data.
C. Always assume that you are misinterpreting the results.
D. Use linear models to tease out a confounder.

    Look again at the admissions data using ?admissions. What important characteristic of the table variables do you need to know to understand the calculations used in this video? Select the best answer.

A. The data is from 1973.
B. The columns “major” and “gender” are of class character, while “admitted” and “applicants” are numeric.
C. The data is from the “dslabs” package.
D. The column “admitted” is the percent of student admitted, while the column “applicants” is the total number of applicants.

    In the example in the video, major selectivity confounds the relationship between UC Berkley admission rates and gender because:

A. It was harder for women to be admitted to UC Berkeley.
B. Major selectivity is associated with both admission rates and with gender, as women tended to apply to more selective majors.
C. Some majors are more selective than others
D. Major selectivity is not a confounder.
Assessment 5- Simpson’s Paradox

    Admission rates at UC Berkeley are an example of Simpson’s Paradox because:

A. It appears that men have higher a higher admission rate than women, however, after we stratify by major, we see that on average women have a higher admission rate than men.
B. It was a paradox that women were being admitted at a lower rate than men.
C. The relationship between admissions and gender is confounded by major selectivity.
