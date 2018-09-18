---
layout: post
title: "Using MathJax on Github:Pages"
categories:
- Research
tags:
- Github
- MathJax
- Latex
- Webpage
---

## Thanks

A very useful post by [Christopher Poole](http://christopherpoole.github.io/using-mathjax-on-github-pages/) regarding how to use **Latex** in Github:Pages 

However, the font of th latex is smaller than my content. To solve this problem, I add the code below to the <head> part of the **default.html** in the **_layouts** filefolder. It works! I can choose the scale number to scale up or down.

```html
<script type="text/javascript">          
	 MathJax.Hub.Config({       
	 extensions: ["tex2jax.js"],         
	 "HTML-CSS": { scale: 150}        
	 });          
</script>   
``` 
 

## Usage

Here is an example MathJax inline rendering \\( 1/x^{2}  \\), and here is a block rendering: 

\\[  \frac{1}{n^{2}}  \\]

one more equation:

\\[   \frac{E_{t}}{(1+r)^{s}} = ((t+s)^a) \beta \\]   

another one: 

\\[   \beta_{t+s}^{a} + \beta = \sum  \\] 




