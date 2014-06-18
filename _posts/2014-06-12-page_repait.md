---
layout: post
title: 触发页面重绘的一种方式 
tags: repait css
---

## 触发页面重绘的一种方式  

One thing to note here is that when the browser window is resized, the font doesn’t adjust itself according to the new viewport size, which is probably a bug. The font size changes to fit the size of its container if you refresh the page. To fix this issue (allow resizing without page refresh) you need to cause a “repaint” on the element.You can do that by following Chris Coyier’s example and using jQuery to cause a repaint. For the sake of getting the demo above to work, I used Chris’s snippet which changes the headline’s z-index on window resize, causing a repaint, and therefore you can see the headline adjust its size when you resize your browser as you view the demo.
（http://codepen.io/SaraSoueidan/pen/ae3d1f2ba1a4b821212477396b5d4096）

从上面的解决方案可以获取的灵感：
当某些操作需要让浏览器重绘某些区域才能生效时，可以通过改变某些css的属性来触发重绘(repait)
