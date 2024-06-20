# Analysis of Pollinators
## Table of contents
- [Overview](#overview)
- [Data source](#data-source)
- [Objectives](#objectives)
- [R Data analysis](#R-data-analysis)
- [Visualisation](#visualisation)
- [Conclusion](#conclusion)


## Overview
This dataset contains information on two species of Sea Rocket Cakile maritima (Maritima) and Cakile edentula (Edentula), and their first-generation hybrid plants (F1 Hybrid). Cakile sp. is an invasive weed in Australia and I am interested in investigating the interactions between these species and their insect pollinators. The data was collected on the number of flower plants produced over time. I am interested to see whether there is a correlation between the number of flowers produced by each plant and the number of pollinators visiting the plants.

## Objectives
1. To conduct a thorough audit of the data to see whether it's messy and the level of messiness
2. Clean the data by handling duplicates, missing values and outliers
3.  Create two plots to visualize your data. First, plot boxplots of the Number of pollinators vs Species (use different colors for species and label axes appropriately). Second, plot a scatter plot of the relationship between the Number of Flowers and the Number of Pollinators
4.  Fit a linear model to the response variable (Number of pollinators) and predictor (Number of Flowers). Add the fitted regression line from this linear model to the scatter plot you made in part 3.
5. Check whether there is a strong correlation between the number of flowers each plant produced and the number of pollinators visited them and if so why.
6.   Write down the most appropriate statistical test to see the effect of these two predictors on the number of pollinators. Interpret the output of the statistical test.
7. Check whether there is any significant interaction between species and flower number. Fit a model to test the interaction between the predictors. Interpret the output of the model.
8. State whether my model (the model in 7 above) meets the assumptions. Why?
9. Use the function anova() in R to compare your models (models with and without interaction) in parts 5 and 6 using a likelihood ratio test (LRT). State the null hypothesis for this test, the distribution for the test statistic under the null hypothesis (specify also the degrees of freedom), and give a p-value.
10. Run an appropriate statistical test to test if there is any significant difference between the number of flowers each species (Maritima, Edentula, and F1 Hybrid) produced. Interpret the output of the statistical test. Then, run a post hoc TUKEY test to see which two species produced a significantly higher number of flowers. To run a Tukey post hoc test, use TukeyHSD() function to find confidence intervals for the difference between means for pairs of species, and use this to see which two species produced statistically significantly different numbers of flowers. Interpret the output of the post hoc test.






## Tools
[RStudio](#Rstudio) - To View, manipulate and visualize the data

## R Data Analysis
# Loading the dataset
```r
flowers<- read.csv("C:\\Users\\ADMIN\\Desktop\\pollinators\\pollinators.csv")
```
# Loading necessary packages
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
# Box plot
```r
Box_Plot<- ggplot(flowers, aes(x=Species, y=NumberofPollinator, fill = Species)) +geom_boxplot() +
  labs(title = 'Boxplot of Number of Pollinators by Species',
       x = 'Species',
       y = 'Number of Pollinators') +
  theme_minimal()
print(Box_Plot)
```
# scatter plot
```r
Scatter_Plot<- ggplot(flowers, aes(x=NumberofPollinator, y=NumberofFlowers, colour = Species)) +geom_point() +
  labs(title = 'Scatter Plot of Number of Flowers vs Number of Pollinators',
       x = 'Number of Flowers',
       y = 'Number of Pollinators') +
  theme_minimal()
print(Scatter_Plot)
```
# Fitting a linear regression line
```r
model <- lm(NumberofPollinator ~ NumberofFlowers, data = flowers)
print(model)
```
# Adding the fitted line to the scatter plot
```r
Scatter_Plot <- Scatter_Plot +
  geom_smooth(method = "lm", se = FALSE, color = "black") +
  theme_minimal()

print(Scatter_Plot)
```
# Calculate correlation coefficients
```r
correlation_coef <- cor(flowers$NumberofFlowers, flowers$NumberofPollinator)
print(correlation_coef)
model <- lm(NumberofPollinator ~ NumberofFlowers * Species, data = flowers)
summary(model)
```
# Load necessary libraries
```r
library(stats)
```
# Perform one-way ANOVA
```r
anova_result <- aov(NumberofFlowers ~ Species, data = flowers)
summary(anova_result)
```






