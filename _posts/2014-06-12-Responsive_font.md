---
layout: post
title: Responsive Font
tags: responsive css font
---

## Responsive Font

考虑font的RWD时，有3个要素要考虑：
**font size**, **line height** 和 **line length**

###font size
对于font size, 我更倾向于使用rem和px结合的方式
rem只兼容IE9+，为了向下兼容，要提供px的fallback,
例如：
h1 {
  font-size: 18px;
  font-size: 1.2rem;
}
当然，em方式也可以，但em的计算有些麻烦，如果嵌套层级很多，就复杂了

###line height
对于line height, 最好使用不带单位的值，如 line-height: 1.4 
如果带单位，如1.4em, 那么子代继承下去的值是计算后的值，而非1.4em; 而如果不带单位，继承后的值还是1.4。(http://meyerweb.com/eric/thoughts/2006/02/08/unitless-line-heights/)
ps: line-height的值是相对于font-size计算的，不是高度

###line length
对于line length, 有文章给出过建议，最好在50-60字/行，当然是针对英文；中文记得有篇博文专门讲解，日后找到再做补充

###**关于Font的补充：

### Text Importance
---
> Text can be transformed into sound through the voice synthesizers in screen readers. Text can also be enlarged by screen enlargement or magnification software, without any loss of quality. These are the two main reasons why having content in text format is so important for accessibility. Although it is possible to provide alternative text for graphics, it is not possible to enlarge text in most graphics without some loss of quality (unless the graphic is vector-based, such as Scaleable Vector Graphics [SVG] or Flash, but this introduces a different set of potential accessibility problems).— [Web Accessibility In Mind](http://webaim.org/techniques/fonts/)