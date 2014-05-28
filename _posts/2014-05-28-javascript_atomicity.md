---
layout: post
title: Javascript 线程执行的原子性
tags: javascript thread 事件处理
date: 2014-05-28-11:00
comments: true
---

**Javascript事件处理器在线程空闲之前不会运行**

{% highlight javascript %}
function innerFn() {
  var start = new Date();
  console.log("inner function start");

  while(new Date() - start < 1000) {}
  console.log("use time ", new Date() - start, "ms");
  console.log("inner function finished");
}

function test() {
  var start = new Date();
  console.log("test function start");

  setTimeout(function() {
    console.log("setTimeout callback function execute, time: ", new Date() - start, "ms");
  }, 500);

  while(new Date() - start < 1000) {}
  console.log("first while loop finished");

  innerFn();

  var newStart = new Date();
  while(new Date() - newStart < 1000) {}
  console.log("second while loop finished");

  console.log("test function finished");
}
{% endhighlight %}

setTimeout函数会注册一个延时事件，按理说当500ms过后，延时事件就会被触发，callback执行；但事实上，当函数test执行完成之后，setTimeout callback才执行。此时的test是一个执行整体，不会被其他事件干扰打断。（可能理解有误，有待验证）