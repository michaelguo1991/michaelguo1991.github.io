---
layout: post
title: setTimeout & setInterval
tags: javascript setTimeout setInterval
---

**HTML规范定义，setTimeout和setInterval的最小间隔是4ms.**

举例说明：
{% highlight javascript %}
var count = 0;
var start = new Date();
var timer = setInterval(function() {
  if (new Date() - start > 1000) {
    clearInterval(timer);
    console.log(count);
    return;
  }
  count++;
}, 0);
{% endhighlight %}
**chrome 35.0 运行结果：250**

{% highlight javascript %}
var count = 0;
var start = new Date();
while(new Date() - start < 1000) {
  count++;
}
console.log(count);
{% endhighlight %}
**chrome 35.0 运行结果：725926**