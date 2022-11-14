---
title: "10. ANCOVAs and multiple regression"
author: "jsg"
date: "Last compiled on 14 November, 2022 08:27"
output:
  html_document:
    toc: true
    toc_float: true
    keep_md: true
    self_contained: true
---

Before doing this, review the ** Combining Multiple Explanatory Variables in Linear Models** lecture set slides from 
https://sites.google.com/view/biostats/lessons/ancova-and-multiple-regression and
the  **10_ANCOVA_and_Regression.R**
script in the lecture files folder of the
[CUNY-BioStats github repository](https://github.com/jsgosnell/CUNY-BioStats). 
Make sure you are comfortable with null and alternative hypotheses and appropriate plots
for all examples.

Remember you should

* add code chunks by clicking the *Insert Chunk* button on the toolbar or by
pressing *Ctrl+Alt+I* to answer the questions!
* **knit** your file to produce a markdown version that you can see!
* save your work often 
  * **commit** it via git!
  * **push** updates to github
  
## Example

Following the iris example from class


```r
set.seed(13)
iris_example_species <-data.frame(
  Species = c(rep("x",25), rep("y", 25), rep("z", 25)),
  Sepal_Length = runif(75,2,4 ),
  #no difference based on species or sepal length
  Petal_no_impacts = runif (75, 4, 6))
#no difference based on species
iris_example_species$Petal_no_impact_species <- 
  iris_example_species$Sepal_Length * 2 + rnorm(75)
#no impact of petal length
iris_example_species$Petal_no_relationship <-rnorm(75) +
  c(rep(2,25), rep(3,25), rep(4,25))
#impact of species and petal length but no interaction
iris_example_species$Petal_no_interaction <- 
  iris_example_species$Sepal_Length * 2 + rnorm(75) +
  c(rep(2,25), rep(3,25), rep(4,25))
#impact of species and petal length with interaction
iris_example_species$Petal_interaction <- 
  iris_example_species$Sepal_Length * c(rep(-2, 25),rep(2,25), rep(5,25)) + 
  c(rep(2,25), rep(3,25), rep(4,25)) + rnorm(75)
```


Plot the data


```r
library(ggplot2)
ggplot(iris_example_species, aes(x= Sepal_Length, y = Petal_interaction, color = Species)) +
  geom_point(size = 3)+
  xlab("Sepal Length") +
  ylab("Petal Length") +
  ggtitle("Impact of Sepal Length and Species on Petal Length") +
  theme(axis.title.x = element_text(face="bold", size=28), 
        axis.title.y = element_text(face="bold", size=28), 
        axis.text.y  = element_text(size=20),
        axis.text.x  = element_text(size=20), 
        legend.text =element_text(size=20),
        legend.title = element_text(size=20, face="bold"),
        plot.title = element_text(hjust = 0.5, face="bold", size=32))
```

![](10_ANCOVA_and_multiple_regression_files/figure-html/unnamed-chunk-2-1.png)<!-- -->

Note the impact of sepal length appears to depend on species.


```r
library(car)
```

```
## Loading required package: carData
```

```r
Anova(lm(Petal_interaction ~ Sepal_Length * Species, iris_example_species), 
      type = "III")
```

```
## Anova Table (Type III tests)
## 
## Response: Petal_interaction
##                       Sum Sq Df F value    Pr(>F)    
## (Intercept)            2.096  1  1.6503    0.2032    
## Sepal_Length          28.875  1 22.7307 1.001e-05 ***
## Species                2.920  2  1.1494    0.3228    
## Sepal_Length:Species 159.284  2 62.6954 3.027e-16 ***
## Residuals             87.651 69                      
## ---
## Signif. codes:  0 '***' 0.001 '**' 0.01 '*' 0.05 '.' 0.1 ' ' 1
```

Interaction is significant, so follow up for each species. this ends in regression!

```r
summary(lm(Petal_interaction ~ Sepal_Length, 
         iris_example_species[iris_example_species$Species == "x",]))
```

```
## 
## Call:
## lm(formula = Petal_interaction ~ Sepal_Length, data = iris_example_species[iris_example_species$Species == 
##     "x", ])
## 
## Residuals:
##     Min      1Q  Median      3Q     Max 
## -2.1788 -0.9693  0.2359  0.5302  1.6908 
## 
## Coefficients:
##              Estimate Std. Error t value Pr(>|t|)    
## (Intercept)    1.5724     1.1058   1.422    0.168    
## Sepal_Length  -1.8824     0.3567  -5.277 2.35e-05 ***
## ---
## Signif. codes:  0 '***' 0.001 '**' 0.01 '*' 0.05 '.' 0.1 ' ' 1
## 
## Residual standard error: 1.018 on 23 degrees of freedom
## Multiple R-squared:  0.5477,	Adjusted R-squared:  0.528 
## F-statistic: 27.85 on 1 and 23 DF,  p-value: 2.35e-05
```
Significant negative relationship for species x.



```r
summary(lm(Petal_interaction ~ Sepal_Length, 
           iris_example_species[iris_example_species$Species == "y",]))
```

```
## 
## Call:
## lm(formula = Petal_interaction ~ Sepal_Length, data = iris_example_species[iris_example_species$Species == 
##     "y", ])
## 
## Residuals:
##     Min      1Q  Median      3Q     Max 
## -2.4904 -0.7587  0.2401  0.8115  1.3829 
## 
## Coefficients:
##              Estimate Std. Error t value Pr(>|t|)    
## (Intercept)    3.7147     1.2584   2.952  0.00715 ** 
## Sepal_Length   1.8307     0.4127   4.436  0.00019 ***
## ---
## Signif. codes:  0 '***' 0.001 '**' 0.01 '*' 0.05 '.' 0.1 ' ' 1
## 
## Residual standard error: 1.142 on 23 degrees of freedom
## Multiple R-squared:  0.4611,	Adjusted R-squared:  0.4376 
## F-statistic: 19.68 on 1 and 23 DF,  p-value: 0.00019
```
Positive relationship for species y


```r
summary(lm(Petal_interaction ~ Sepal_Length, 
           iris_example_species[iris_example_species$Species == "z",]))
```

```
## 
## Call:
## lm(formula = Petal_interaction ~ Sepal_Length, data = iris_example_species[iris_example_species$Species == 
##     "z", ])
## 
## Residuals:
##     Min      1Q  Median      3Q     Max 
## -2.4143 -0.5861 -0.1689  0.7747  3.1415 
## 
## Coefficients:
##              Estimate Std. Error t value Pr(>|t|)    
## (Intercept)    4.0916     1.5034   2.722   0.0122 *  
## Sepal_Length   5.1553     0.5402   9.543 1.83e-09 ***
## ---
## Signif. codes:  0 '***' 0.001 '**' 0.01 '*' 0.05 '.' 0.1 ' ' 1
## 
## Residual standard error: 1.213 on 23 degrees of freedom
## Multiple R-squared:  0.7984,	Adjusted R-squared:  0.7896 
## F-statistic: 91.07 on 1 and 23 DF,  p-value: 1.834e-09
```

and z!  

## Practice

### 1
  

1.  Data on FEV (forced expiratory volume), a measure of lung function, can
be found at 

http://www.statsci.org/data/general/fev.txt

More information on the dataset is available at 

http://www.statsci.org/data/general/fev.html.

Does the impact of age on FEV differ among genders? Consider how your answer to 
this differs from the previous assignment!

### 2

2. Data on home gas consumption at various temperatures before and after new insulation was installed has been collected @ 

http://www.statsci.org/data/general/insulgas.txt

More information on the data is available @

http://www.statsci.org/data/general/insulgas.html

Is there any relationship between these factors?  How would you test this,
and what type of plot would you produce to accompany your analysis?

### 3

3.  Data on the height, diameter, and volume of cherry trees was collected for
use in developing an optimal model to predict timber volume.  Data is available @ 

http://www.statsci.org/data/general/cherry.txt

Use the data to justify an optimal model.

### 4

4.  Over the course of five years, a professor asked students in his stats class 
to carry out a simple experiment.  Students were asked to measure their pulse 
rate, run for one minute, then measure their pulse rate again.  The students 
also filled out a questionnaire.  Data  include:

Variable | Description
:-:  | :-:
Height | Height (cm)
Weight | Weight (kg)
Age    | Age (years)
Gender | Sex (1 = male, 2 = female)
Smokes | Regular smoker? (1 = yes, 2 = no)
Alcohol | Regular drinker? (1 = yes, 2 = no)
Exercise | Frequency of exercise (1 = high, 2 = moderate, 3 = low)
Change | Percent change in pulse (pulse after experiment/pulse before experiment)
Year | Year of class (93 - 98)

Using the available data (available at 

https://docs.google.com/spreadsheets/d/e/2PACX-1vToN77M80enimQglwpFroooLzDtcQMh4qKbOuhbu-eVmU9buczh7nVV1BdI4T_ma-PfWUnQYmq-60RZ/pub?gid=942311716&single=true&output=csv )

determine the optimal subset of explanatory variables that should be used to
predict change pulse rate (Change) (focusing on main effects only, no 
interactions) and explain your choice of methods.  Interpret your results. Make
sure you can explain any changes you needed to make to the dataset or steps you 
used in your analysis.

