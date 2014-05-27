---
layout: post
tags: javascript prototype
comments: true
---

prototype属性时Javascript为每个Function()实例创建的一个对象。prototype属性来自Function()构造函数。Javascript会为每一个函数创建原型对象，不管你是否打算将这个函数作为构造函数使用。  

例如：
{% highlight javascript %}
var Person = function(name) {this.name = name;}; Person.prototype ==> Object {}
var test = function() {console.log("test");} test.prototype ==> Object {}
{% endhighlight %}

***
虽然原型只是一个对象，但它是特殊的，因为原型链将每个实例都链接到其构造函数的prototype属性。这意味着任何时候使用new关键字由构造函数创建对象时，它都会在创建的对象实例和创建对象的构造函数的prototype属性之间添加一个隐藏的链接。该链接在实例中被称为``__proto__``。正是这个链接使得原型链成为一个链。

例如：
{% highlight javascript %}
var Person = function(name) {this.name = name;} 
var p = new Person();
p.__proto__ === Person.prototype;
{% endhighlight %}

***
与作用域链一样，原型链在链查找时将使用它找到的第一个值。即一旦在链中找到属性，查找即结束，即使链中其他地方页使用了相同的属性名称。  
原型链查找的最后一站是Object.prototype; 如果在Object.prototype也未找到相应的属性，那么就会返回undefined。

***
在上述例子中, p.constructor === Person.prototype    
constructor属性时预制在Person的原型对象中的。  
执行 var Person = function(name) {this.name = name;} 时，constructor就已经有值了，Person.prototype.constructor === constructor属性时预制在Person的原型对象中的。  
如果用新值替换prototype属性的属性值，constructor属性的值就会发生变化，具体是什么值要根据新值来确认。

例如：
{% highlight javascript %}
var Animal = function(type) {this.type = type;} // Animal.prototype.constructor === Animal
var Person = function(name) {this.name = name;}
Person.prototype = new Animal();
var p = new Person();
p.constructor === Animal // true
p.constructor === Person // false
{% endhighlight %}
（解释：理解原型链的查找原理就不难理解constructor值了。首先在p的实例属性中查找constructor，没找到；然后去p.``__proto__``中查找，即Person.prototype, 即new Animal(); new Animal()中也没找到；接着会去new Animal().``__proto__``中查找，即Animal.prototype，然后就找到了，Animal.prototype.constructor === Animal。查找结束。）

如果要保持constructor不变，就要手动去更改constructor的值：
{% highlight javascript %}
Person.prototype = new Animal();
Person.prototype.constructor = Person;
p.constructor === Person; // true
{% endhighlight %}

***
用新对象替换prototype属性不会更新以前的实例。  
创建一个实例时，该实例将在实例化时被绑定到当时的原型。提供一个新对象赋值给prototype不会更新已创建对象和实例之间的连接。

例如：
{% highlight javascript %}
var Person = function() {};
Person.prototype.age = 20;
p = new Person(); p.age // 20
Person.prototype.age = 25;
p.age // 25
Person.prototype = {age: 30}
p1 = new Person();
p.age // 25
p1.age // 30
{% endhighlight %}