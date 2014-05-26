---
layout: default
---

{% highlight javascript %}
var Person = function(name) {this.name = name;}; Person.prototype ==> Object {}
var test = function() {console.log("test");} test.prototype ==> Object {}
{% endhighlight %}

{% highlight ruby %}
def show
  @widget = Widget(params[:id])
  respond_to do |format|
    format.html # show.html.erb
    format.json { render json: @widget }
  end
end
{% endhighlight %}