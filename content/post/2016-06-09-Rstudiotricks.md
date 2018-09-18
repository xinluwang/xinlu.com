---
layout: post
title: "R and Rstudio Tricks"
date: 2016-06-09
categories:
- Programming

Tags:
- RStudio
- R
---

### Shortcut 

- `Alt`+`-` gives the assign operator `<-`
- `Ctrl`+`Alt`+`Left/right arrow` switches between open files
- `Ctrl`+`Space` gives autocomplete options
- `Ctrl`+`Left/right arrow` jumps one word
- `Ctrl`+`shift`+`C` to un-comment, simply re-highlight and hit `Ctrl`+`shift`+`C` again. 
- The `Tab` key on your keyboard will help you (particularly in RStudio) by offering ways to finish your code. If you start typing mea and hit tab, it will suggest mean() among other things. If you type mean(~hwy, data=vehicles, and hit tab, it will tell you the other arguments you can use for the mean() function.

### Useful build-in function

- `str()`
- `head()` and `tail()`
- `summary()`
- `table()`

### Use back ticks to reference non standard names

- ``` df$`1` ```
- ``` lm(`2`~`1`,data=df) ```

### Use `library(foreach)` 

```r
x <- seq(0,10, 0.1)

foreach(i = 1:101) %do% {
    lp[i] <- x[i]^i
    }
```

### combine and split *dataframe* from and into small chunks 

```r
foo <- list()
foo[[1]] <- data.frame(a=1:5, b=11:15)
foo[[2]] <- data.frame(a=101:105, b=111:115)
foo[[3]] <- data.frame(a=200:210, b=300:310)
food <- do.call(rbind, foo)
row.names(food) <- as.character(seq(1, nrow(food), 1))

## split 
foo <- split(food, (as.numeric(row.names(food))-1) %/% 100)
##  every 100 observations as one chunks 
```

### Instead of using *dplyr*

- `ifelse()`
- `df$column2[df$column1 == x] <- y`
- `transform(sales, euro = revenue * usd2eur)` 
- `subset(sales, product %in% c(1, 2), select =c('name'))`


### using *with()* and *within()* 

```r
with(mtcars, summary(mpg))
with(mtcars, summary(mpg, disp, wt))

with(mtcars, {
nokeepstats <- summary(mpg)
keepstats <<- summary(mpg)
}
)
```

> The `within()` function is similar to the `with()` function , but allows you to modify the data frame.

```r
leadership <- 
within(leadership, 
{agecat <- NA
 agecat[age > 75] <- "Elder"
 agecat[age >= 55 & age <= 75] <- "Middle Aged"
 agecat[age < 55] <- "Young"
 }
 )
```

### *dplyr* inequality Join



```r
FundsWithReturns <- left_join(FundMonths, Returns, 
                                FundID == FundID, 
                                yearmonth > gmonth +3, 
                                yearmonth <= gmonth + 15)

FundsWithReturns <- left_join(FundMonths, Returns, 
                                "FundID", 
                                yearmonth > gmonth +3, 
                                yearmonth <= gmonth + 15) 

FundsWithReturns <- left_join(FundMonths, Returns, 
                    by=c("FundID”, 
                         "yearmonth > gmonth +3",
                         "yearmonth <= gmonth + 15")
                        )

FundsWithReturns <- sqldf('select d1.*, d2.ReturnRf
                        from FundMonths d1 
                        left join Returns d2
                        on d1.FundID = d2.FundID
                        and d1.yearmonth - 3 > d2.gmonth
                        and d1.yearmonth - 15 <= d2.gmonth')
```


### 用完之后及时的remove temp items 

```r
rm(object1, object2)
```

### 做好标注,注释在Rstudio

```r
# 20160430 #### 
```
前面一个#后面四个#### 就可以在备注里面显示出来模块并直接索引到该段程序。统一注释的风格。