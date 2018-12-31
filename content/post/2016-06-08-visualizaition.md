---
layout: post
title: "Data Visualization Tools"
date: 2016-06-08

---

来自知乎问题[有哪些值得推荐的数据可视化工具？](https://www.zhihu.com/question/19929609)的总结

### [Tagxedo](http://www.tagxedo.com) 的在线词云生成工具

Python的`word cloud`模块，结合`jibe`分词模块可以实现分词并生成词云。

**遮罩**用于定义词云的形状。

### Google Books Ngrams

谷歌扫描的三千万册书进行分词并做词频统计，沿着整个历史时间轴来研究语言在历史中的变迁。
在Ngrams中，分别输入首字母大写的“Science, Philosophy, Religion”，和小写的“science, philosophy, religion”，我们得到如下两张图。在大写的图中（下图一），可以清楚看到在公元1600到1800年间，宗教是压倒性强势，然后是哲学，相比之下，科学还是没影的事。但1850年是转折点，科学慢慢占据优势，比宗教和哲学加起来都大。

### 百度[Echarts](http://echarts.baidu.com/)

动态类型切换：
大规模散点图：（感觉这个超级酷炫的！好像还有专利的）

### Google Chart API，Google sheets for world map

在Google Video和Google Finance中使用了它，后来觉得，如果能开放它让其他用户也使用的话，会是件不错的事情。 
Google Chart API工具从简单的折线图到复杂的分级树形图，他的图表库里提供了海量的模版可供选择。但Google Chart有个大问题：图表在客户端生成，这意味着那些不支持JavaScript的设备将无法使用。

### [Tableau Public](https://public.tableau.com/s/download)（Business Intelligence and Analytics）

这是Tableau的免费版本。操作简单，出的成品很有美感。学生可以免费。

### R packages

- `library(ggplot2)` 
- `library(leaflet)` Leaflet是为移动端友好型交互地图所做的开源JavaScript库 [github](https://github.com/rstudio/leaflet)
- `devtools::install_github("chgrl/leafletR")` [github](https://github.com/chgrl/leafletR)

### [WolframAlpha](http://www.wolframalpha.com/)

WolframAlpha把自己称作计算型知识引擎、谷歌在分析领域的劲敌。它最棒的一点是在显示图表时可以不需要任何配置就响应数据请求。如果你用的是公开的数据，那么你只需一个简单的小部件生成器就能在你的网页上轻松加入可视化数据。

### flowingdata

http://flowingdata.com/








