---
layout: post
tags: javascript prototype
comments: true
---

1. prototype属性时Javascript为每个Function()实例创建的一个对象。prototype属性来自Function()构造函数。Javascript会为每一个函数创建原型对象，不管你是否打算将这个函数作为构造函数使用。
例如：

{% highlight javascript %}
var Person = function(name) {this.name = name;}; Person.prototype ==> Object {}
var test = function() {console.log("test");} test.prototype ==> Object {}
{% endhighlight %}

2. 虽然原型只是一个对象，但它是特殊的，因为原型链将每个实例都链接到其构造函数的prototype属性。这意味着任何时候使用new关键字由构造函数创建对象时，它都会在创建的对象实例和创建对象的构造函数的prototype属性之间添加一个隐藏的链接。该链接在实例中被称为__proto__。正是这个链接使得原型链成为一个链。