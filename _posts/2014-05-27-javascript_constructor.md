---
layout: post
title: Javascript Constructor
tags: javascript constructor
comments: true
---

**构造函数实例都拥有指向其构造函数的Construct属性，无论实例是通过new操作符创建还是通过字面量创建；**

例如：
{% highlight javascript %}
var obj = []; obj.constructor === Array // true
var obj = new Array(); obj.constructor === Array // true
{% endhighlight %}  


**特殊说明：**
{% highlight javascript %}
var num = 10; num.constructor === Number // true
var str = "string"; str.constructor === String // true
var boo = true; boo.constructor === Boolean // true
{% endhighlight %}

自己的理解：
调用原始值的construct属性时，其实是先创建了一个临时的包装对象（new Number(10), new String("string"), new Boolean(true)), 然后取的是包装对象的construct的值。