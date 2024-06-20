# Aphids-analysis

## Table of contents
- [Overview](#overview)
- [Data source](#data-source)
- [Objectives](#objectives)
- [R Data analysis](#R-data-analysis)
- [Visualisation](#visualisation)
- [Conclusion](#conclusion)


## Overview
In this problem, I will analyze the data on the effect of a pesticide on aphid mortality [mort]. The file name for this dataset is “aphids.csv”. In this dataset, I tested the mortality rate of four different populations [pop] of aphids when they were exposed to different concentrations [conc] of a particular pesticide. I am interested to see whether any of these populations have developed resistance against this pesticide.

## Objectives
1. To conduct a thorough audit of the data to see whether it's messy and the level of messiness
2. Clean the data by handling duplicates, missing values and outliers
3.  Create two plots to visualize your data. First, plot boxplots of the Number of Pollinator vs Species (use different colors for species and label axes appropriately). Second, plot a scatter plot of the relationship between the Number of Flowers and Number of Pollinator
4.  Fit a linear model to the response variable (Number of pollinators) and predictor (Number of Flowers). Add the fitted regression line from this linear model to the scatter plot you made in part 3.
5. Check whether there is a strong correlation between the number of flowers each plant produced and the number of pollinators visited them and if so why.
6.   Write down the most appropriate statistical test to see the effect of these two predictors on the number of pollinators. Interpret the output of the statistical test.
7. Check whether there is any significant interaction between species and flower number. Fit a model to test the interaction between the predictors. Interpret the output of the model.
8. State whether my model (the model in 7 above) meets the assumptions. Why?
9. Use the function anova() in R to compare your models (models with and without interaction) in parts 5 and 6 using a likelihood ratio test (LRT). State the null hypothesis for this test, the distribution for the test statistic under the null hypothesis (specify also the degrees of freedom), and give a p-value.
10. Run an appropriate statistical test to test if there is any significant difference between the number of flowers each species (Maritima, Edentula, and F1 Hybrid) produced. Interpret the output of the statistical test. Then, run a post hoc TUKEY test to see which two species produced a significantly higher number of flowers. To run a Tukey post hoc test, use TukeyHSD() function to find confidence intervals for the difference between means for pairs of species, and use this to see which two species produced statistically significant different numbers of flowers. Interpret the output of the post hoc test.






## Tools
[RStudio](#Rstudio) - To View, manipulate and visualize the data

## R Data Analysis
## Loading the dataset
```r
flowers<- read.csv("C:\\Users\\ADMIN\\Desktop\\pollinators\\pollinators.csv")
```
## Loading necessary packages
```r
library(dplyr)
library(ggplot2)
```
# Data checks
```r
summary(flowers)
```
# Checking for missing values, duplicates, and outliers
```r
sum(is.na(flowers))
```




