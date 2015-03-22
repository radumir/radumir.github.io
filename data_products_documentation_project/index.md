---
title       : Data Products Documentation Project
subtitle    : 
author      : Mirescu C-tin Radu
job         : programmer
framework   : io2012        # {io2012, html5slides, shower, dzslides, ...}
highlighter : highlight.js  # {highlight.js, prettify, highlight}
hitheme     : tomorrow      # 
widgets     : [mathjax]            # {mathjax, quiz, bootstrap}
mode        : selfcontained # {standalone, draft}
knit        : slidify::knit2slides
---

## Quadratic Equation Solver Shiny Application Documentation

The shiny application from [http://radumir.shinyapps.io/DataProductsProject/](http://radumir.shinyapps.io/DataProductsProject/ "Shiny application") is focused on solving quadratic equations in the set of real numbers.

### Theoretical aspects

A quadratic equation is one of the form:

$$a*x^2+b*x+c=0$$

The solutions of it are get by the formula:

$$x=\frac{-b \pm \sqrt{b^2 - 4 a c}}{2a}$$

The formula could not be applied as is for all combinations of coefficients since there are some conditions that should be met (like denominator should not be 0 and the part under square root to be positive).

--- .class #id 

## The interface

The interface of the application is like the one in the bellow image that shows the relation between the controls and the equation coefficients.

![Interface example][interfaceImg]

[interfaceImg]: assets/img/interface.png  "Interface example"

--- .class #id

## Limit cases

1. Undefined equation


```r
a <- 0; b <- 0; c <- 0
```

2. Impossible equation


```r
a <- 0; b <- 0; c <- 3 #The c could be anything that's different than 0.
```

3. Linear equation


```r
a <- 0; b <- abs(rnorm(1))*1000+1; c <- rnorm(1)*1000
x = -c/b
x
```

```
## [1] -0.4986406
```


---

## Normal quadratic equation with 2 solutions


```r
solutions <- abs(rnorm(3)*1000)+1
a <- solutions[1]; b <- -(solutions[2]+solutions[3])*solutions[1]
c <- solutions[1]*solutions[2]*solutions[3]; delta <- b^2 - 4*a*c
```

In this case we should have the solutions

```r
c( (-b-sqrt(delta))/(2*a), (-b+sqrt(delta))/(2*a))
```

```
## [1]   61.81877 1055.41146
```

that should be the same with


```r
c( solutions[2], solutions[3] )
```

```
## [1] 1055.41146   61.81877
```

