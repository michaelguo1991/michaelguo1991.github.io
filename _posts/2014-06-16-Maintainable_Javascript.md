---
layout: post
title: Maintainable Javascript
tags: maintainable coding_style
---

####**Use logical names for your functions and variables**

* Don’t worry about length, you can compress it during build process.
* Variable names should be nouns (i.e. var book).
* Function names should begin with a verb (i.e. getName()).
* Avoid names that have no meaning (i.e. var a; function foo()).
* Use camel casing since camelCasingIsTheJavascriptWay.
* For Constant-like variables use – UPPER_CASE_WITH_UNDERSCORE.



####**Event Handlers should only handle events**
* Bad Example

{% highlight javascript %}
//The wrong way!!!
function handleClick(event){
    var popup = document.getElementById("popup");
    popup.style.left = event.clientX + "px";
    popup.style.top = event.clientY + "px";
    popup.className = "reveal";
}
{% endhighlight %}

* Better Example – factor out function so it can be passed around and tested

{% highlight javascript %}
//Better, but still wrong
function handleClick(event){
    showPopup(event);
}

function showPopup(event){
    var popup = document.getElementById("popup");
    popup.style.left = event.clientX + "px";
    popup.style.top = event.clientY + "px";
    popup.className = "reveal";
}
{% endhighlight %}

* Even better, don’t pass --event-- object. Extract data that you need and pass that on to the function.

{% highlight javascript %}
//Good
function handleClick(event){
    showPopup(event.clientX, event.clientY);
}

function showPopup(x, y){
    var popup = document.getElementById("popup");
    popup.style.left = x + "px";
    popup.style.top = y + "px";
    popup.className = "reveal";
}
{% endhighlight %}