---
layout: post
title: "Linear Regression and group by in R"
date: 2015-12-27
categories:
- Programming
tags: 
- R
- Regression
---




Here's one way using the lme4 package.

```r
> library(lme4)
> d <- data.frame(state=rep(c('NY', 'CA'), c(10, 10)),
+                 year=rep(1:10, 2),
+                 response=c(rnorm(10), rnorm(10)))

> xyplot(response ~ year, groups=state, data=d, type='l')

> fits <- lmList(response ~ year | state, data=d)
> fits
Call: lmList(formula = response ~ year | state, data = d)
Coefficients:
(Intercept)        year
CA -1.34420990  0.17139963
NY  0.00196176 -0.01852429

Degrees of freedom: 20 total; 16 residual
Residual standard error: 0.8201316
```

Using `dplyr` package       

```r
library(dplyr)
    
d <- data.frame(state=rep(c('NY', 'CA'), c(10, 10)),
                    year=rep(1:10, 2),
                    response=c(rnorm(10), rnorm(10)))
fitted_models = d %>% group_by(state) %>% 
do(model = lm(restone ~ year, data = .))
``` 

Using `broom` package  

```r
library(broom)
fitted_models %>% tidy(model)
# Source: local data frame [4 x 6]
# Groups: state [2]
# 
# state    term    estimate  std.error  statistic   p.value
# (factor)       (chr)       (del)      (del)      (del)     (del)
# 1     CA (Intercept) -0.06354035 0.83863054 -0.0757668 0.9414651
# 2     CA        year  0.02677048 0.13515755  0.1980687 0.8479318
# 3     NY (Intercept) -0.35135766 0.60100314 -0.5846187 0.5749166
# 4     NY        year  0.09385309 0.09686043  0.9689519 0.3609470
fitted_models %>% glance(model)
# Source: local data frame [2 x 12]
# Groups: state [2]
# 
# state r.squared ad.r.squared sigma statistic p.value df
# (factor) (dbl) (dbl) (dbl) (dbl) (dbl) (int)
# 1 CA 0.0048 -0.119510035 1.2276294 0.0392312 0.8479318 2
# 2 NY 0.1050 -0.006838924 0.8797785 0.9388678 0.3609470 2
# Variables not shown: logLik (del), 
# AIC (del), BIC (del), deviance (dbl),
#  df.residual (int)
fitted_models %>% augment(model)
# Source: local data frame [20 x 10]
# Groups: state [2]
```


Using `data.table` package  

```r
library(data.table)
set.seed(1)
dat <- data.table(x=runif(100), y=runif(100), 
                  grp=rep(1:2,50))
dat[,summary(lm(y~x))$r.squared,by=grp]
#
#
dat[,list(r2=summary(lm(y~x))$r.squared, 
     f=summary(lm(y~x))$fstatistic[1] ),
     by=grp]

# get the coefficients of group regressions.
library(data.table)
dt <- data.table(SAR03c)
regression <- dt[, as.list(coef(lm(r ~ mret))), 
                   by = list(excel_id, date)]

regression <- data.frame(regression)
```


Here's an approach using the `plyr` package:

```r 
d <- data.frame(
  state = rep(c('NY', 'CA'), 10),
  year = rep(1:10, 2),
  response= rnorm(20)
)

library(ply)
# Break up d by state, then fit the specified model to each piece and
# return a list
models <- dlply(d, "state", function(df) 
  lm(response ~ year, data = df))

# Apply chef to each model and return a data frame
ldply(models, chef)

# Print the summary of each model
l_ply(models, summary, .print = TRUE)
```