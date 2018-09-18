---
layout: post
title: "Code and Data for the Social Sciences"
date: 2016-06-07
categories:
- Research

Tags:
- bash
- version control
---

### Automate everything 

- Automate everything that can be automated.
- Write a single script that executes all code from beginning to end.
- 写一个terminal执行文件，可以执行不同软件的结果。 
> let’s add another key script to the directory, called `rundirectory.bat`, which is a Windows shell script. Its contents look like this:

```
---- rundirectory.bat ----
stattransfer export_to_csv.stc
statase -b mergefiles.do
statase -b cleandata.do
statase -b regressions.do
statase -b figures.do
pdflatex tv_potato.tex
```
The `rundirectory.bat` script works like a roadmap.

### Version control 

- Store code and data under version control.
- Run the whole directory before checking it back in.

### Directory 

- Separate directories by function.
- Separate files into inputs and outputs.
- Make directories portable.

project路径区分 input 和 output，还要按照功能区分路径。 

- Generally four file folders for one project:
	+ ```/input``` 原始数据保持`.csv` 格式	
	+ ```/code```
	+ ```/output```中间步骤数据为`.feather`格式
	+ ```/temp```

### Documentation

- Don’t write documentation you will not maintain.
- Code should be self-documenting.

### Team management

Try not to use Email. Use one task management for team work.

### Code style

- Keep it short and purposeful
- Make your functions shy
- Order your functions for linear reading.
- Us descriptive names
- Separate slow code from fast code.
- Store more output from slow code.


### Convert `sas7bdat` to `csv`

`sas7bdat_to_csv` is a python command, to convert `.sas7bdat` file into `.csv` format.

```
cd /Volumes/database/conferencepre/DailyVolumeData/ 
sas7bdat_to_csv Volume_2004.sas7bdat volume2004.csv
```

### Lyx

```
\input{untitled.txt} 
```


### Generate dummy variables

```r
dummies = table(1:length(year),as.factor(year)) 
A <- model.matrix(y ~ x + catVar,binom) 
head(A)

## in regression, use + factor(year)
####################################

year = c(1995, 1996)
dummy = as.numeric(year >= 1995)

```

### Import other files into Bibtex


1. zotero to endnote to bidtex 
	- 如果直接用zotero导入bides，它会产生自己的citekey跟bides的规则不一样，通过导入endnote会把cite key丢失，然后再用temporary cite key 打开，这样cite key产生的贵的就一样了， `Author-year-aa`    
2. then use bibdesk to open it with **"Open Using temporary cite keys…"**

#### Alternatively method:  

This method can avoid generating duplicated cite keys.

1. In Endnote, `Edit` -> `output styles` -> `Bibtex Export`.
2. Select items you intend to copy in Endnote, then, `Edit` -> `Copy Formatted`.
3. Paste into a Bibdesk window 