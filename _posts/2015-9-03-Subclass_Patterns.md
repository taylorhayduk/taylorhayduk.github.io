---
layout: post
title: Subclass Instantiation Patterns
---
Subclasses, like Classes, are like factories that create similar objects.  Subclasses themselves have a parent object from which they gain functionality.  In the following examples we have a Robot class and a Terminator subclass.  The Terminator subclass will have all the functionality of robot with an additional speak method.


**Functional Subclass**

In the functional subclass instantiation pattern, we have a function that first creates a new instance of it's parent by calling the parent and passing in any necessary parameters.  The subclass function then adds additional functionality to the parent object and returns it.

{% highlight javascript %}
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

In the Pseudoclassical Subclass Instantiaton pattern, we call the parent passing in a 'this' reference and any additional parameters.

After calling the parent class and outside of the subclass variable, we must make several changes to the subclass's prototype.

We first set the subclass prototype to the parent class prototype by using Object.create.  We should avoid using the 'new' keyword to create the prototype because the parent's prototype might require input parameters that we do not have at present.

Next we set the subclass's prototype.constructor to be the subclass itself.  This is important if we need to know what created an object at a later time.

Lastly, we add in any functionality that we want in the new subclass.


{% highlight javascript %}
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