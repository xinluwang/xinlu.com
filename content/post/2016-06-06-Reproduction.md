---
layout: post
title: "Reproducible Research"
categories:
- Research
---


- Do not do things by hand 
     + remov outliers
     + QA /QC 
     + validating 
     + editing tables and figures
     + moving data around your computer 
     + down load data from a website 


- Do not use GUI (Point and Click) 
     + can not be repeated


- Teach your computer to do the job
     + even if you only do it once
     + down load data from a website, unzip it 


```r
download.file("http://-address- dataset.zip", 
              "project/dataset.zip") 
```


- Do use some version control
     + slow things down
     + add changes in small chunks (don't just do one massive commit)
     + track and snapshot, revert to the old version 
     + software like Github 


- Do not save output 
     + avoid saving data analysis output (tables, figures, summaries, processed data, etc.) 
     + save the data + code that generated the outputs


- Do set your seed 
     + `set.seed()` and to specify the random number generator to use 


- Do think about the entire pipeline 
     + raw data -> processed data -> analysis -> report 


Have we taught a computer to do as much as possible? 
Are we using a version control system? 

- Long scripts should be factored
into smaller functions

- csv是唯一交流的数据文件  

- 数据必须在1G以下   
    + 拆分大的数据集 
    + 原始数据保持`.csv` 格式，中间步骤数据为`.feather`格式
    
- 平台的转换时非常费事的，拆分数据，减少数据集，优化过程所需的时间会更少

- R里面的dataframe 单独存放为Rdata文件。
