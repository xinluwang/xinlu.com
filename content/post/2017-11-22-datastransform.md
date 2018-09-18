---
layout: post
title: "用R进行数据格式转换(SAS, Stata)"
categories:
- Programming
- Research

Tags:
- data
- R
- SAS
- Stata
---

 ​      我们在进行合作研究的时候，经常面临的的一个问题就是，一个Co-author给的数据集是stata格式的(.dta), 而我们用的是SAS，或者相反，还有很多研究者习惯用SAS清洗数据，完成后用Stata 跑回归，在这些情况下我们都会面临一个数据格式转换的问题，那么今天我们就来谈一下如何用R来帮助格式转换。

> 为什么是R? 因为它是开源的，你可以在没有安装SAS和Stata的情况下完成`.sas7bdat`和`.dta`的转换

看到R有些人可能就要关闭文章了，因为不想又学一个软件，其实，我们完成数据转换不需要真正的搞懂R的code，只需要跟着我一步一步来就可以了，比把大象装冰箱还简单。

1. 下载安装R 
到R的[官网](https://cloud.r-project.org/)下载安装对应平台的R程序。

2. 安装需要的packages


```
# 类似于Stata的 ssc install
install.packages('haven', repos = 'http://cran.us.r-project.org') 
# 表示我们要从R的官网安装一个包名字叫 haven
```
然后我们就可以用啦 ~ 

### SAS 转 Stata
把下面的code粘贴单R的console里面，等着


```
library(haven) # 加载包
dataset <- read_sas("C:/example.sas7bdat")  # 把SAS数据读进来

# 把它导出为14版本的stata数据
# version 可以是8 -14 的任何一个  
# 你也可以借此完成不同的stata版本数据的转化
write_dta(dataset, "C:/example.dta", version = 14)  
```
### Stata 转 SAS

把下面的code粘贴单R的console里面，等着

```
library(haven) # 加载包
dataset <- read_dta("C:/example.dta")  # 把Stata数据读进来
write_sas(dataset, "C:/example.sas7bdat")  # 把它导出为SAS格式
```
> 转换完成仍会保留你为变量加的标签哦

而`haven`还可以转换其他的格式如下表所示：

| NAME | FUNCTION |
|----------|------------------------------------|
|`read_dta()` | Read and write Stata DTA files. |
|`read_por()` | Read SPSS (SAV & POR) files. Write SAV files.|
|`read_sas()` | Read and write SAS files.|
|`read_sav()` | Read SPSS (SAV & POR) files. Write SAV files.|
|`read_xpt()` | Read and write SAS transport files|
|`write_dta()`  | Read and write Stata DTA files.|
|`write_sas()`  | Read and write SAS files.|
|`write_sav()`  | Read SPSS (SAV & POR) files. Write SAV files.|
|`write_xpt()`  | Read and write SAS transport files|
 
### One more thing 

当然，如果你想导入`.csv`可以用 `readr` package, 如果导入`.xls`, `.xlsx` 可以用`readxl` package，安装方法如上，使用方法也很简单。你也可以导入`.csv` 然后用上面的程序导出SAS或者Stata格式或者SPSS格式，都十分方便。