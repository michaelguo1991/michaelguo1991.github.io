---
layout: default
---

prototype属性时Javascript为每个Function()实例创建的一个对象。prototype属性来自Function()构造函数。Javascript会为每一个函数创建原型对象，不管你是否打算将这个函数作为构造函数使用。
例如：
{% highlight Javascript %}
var Person = function(name) {this.name = name;}; Person.prototype ==> Object {}
var test = function() {console.log("test");} test.prototype ==> Object {}
{% endhighlight %}