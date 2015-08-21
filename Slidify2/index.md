---
title       : Shiny App for Predicting Iris Species
subtitle    : 
author      : Lucia
job         : 
framework   : revealjs        # {io2012, html5slides, shower, dzslides, ...}
highlighter : highlight.js  # {highlight.js, prettify, highlight}
hitheme     : tomorrow      # 
widgets     : []            # {mathjax, quiz, bootstrap}
mode        : selfcontained # {standalone, draft}
knit        : slidify::knit2slides
---

## Shiny App for Predicting Iris Species

<br>
<br>
<span style="color:lightblue">Lucia</span>

---

## Intro

The App is used to predict one out of three species of iris (setosa, versicolor and virginica). It takes four variables: sepal length and width, petal length and width. Users can put in the values on the side bar panel and view results on the main panel.

 ![width](App.png)

--- 

## Model

We trained the model based on iris data using linear discriminant analysis.


```r
modlda=train(Species ~., data=iris, method="lda")
```

```
## Error in eval(expr, envir, enclos): could not find function "train"
```

```r
modlda$finalModel$means
```

```
##            Sepal.Length Sepal.Width Petal.Length Petal.Width
## setosa            5.006       3.428        1.462       0.246
## versicolor        5.936       2.770        4.260       1.326
## virginica         6.588       2.974        5.552       2.026
```

```r
modlda$finalModel$scaling
```

```
##                     LD1         LD2
## Sepal.Length  0.8293776  0.02410215
## Sepal.Width   1.5344731  2.16452123
## Petal.Length -2.2012117 -0.93192121
## Petal.Width  -2.8104603  2.83918785
```

---

## Predict

The App predicts the species based on the fitted model and the values users plug in. 
For example, if the user put in (5.1, 3.5, 1.4, 0.2), the App will give the result "setosa".


```r
x <- data.frame(Sepal.Length=5.1, Sepal.Width=3.5, Petal.Length=1.4, Petal.Width=0.2)

predict(modlda, newdata = x)
```

```
## Loading required package: MASS
```

```
## [1] setosa
## Levels: setosa versicolor virginica
```

---

## The End

<span style="color:pink"; font-weight:bold>Thank you!</span>




