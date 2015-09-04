---
layout: post
title: Subclass Instantiation Patterns Cheat Sheet
---

**Functional Subclass**


{% highlight ruby linenos %}
var Robot = function(catchPhrase) {
  var obj = {catchPhrase: catchPhrase};
  obj.speak = function(){console.log(obj.catchPhrase);};
  return obj;
}

var Terminator = function(catchPhrase) {
  var obj = Robot(catchPhrase);
  obj.shoot = function(){console.log("Bang Bang");};
  return obj;
}

var arnold = Terminator("I'll be back!");
{% endhighlight %}

**Pseudoclassical Subclass**


{% highlight ruby linenos %}
var Robot = function(catchPhrase) {
  this.catchPhrase = catchPhrase;
};
Robot.prototype.speak = function(){
  console.log(this.catchPhrase);
};

var Terminator = function(catchPhrase) {
  Robot.call(this, catchPhrase);
}
Terminator.prototype = Object.create(Robot.prototype);
Terminator.prototype.constructor = Terminator;
Terminator.prototype.shoot = function(){console.log("Bang Bang");};

var arnold = new Terminator("I'll be back!");
{% endhighlight %}