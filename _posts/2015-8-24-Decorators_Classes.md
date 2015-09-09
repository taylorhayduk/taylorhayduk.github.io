---
layout: post
title: Class Instantiation Patterns
---

In JavaScript it can be easy to confuse Decorators and the four types of Classes.  Just remember that Decorators 'decorate' pre-made objects, and Classes create newInstances.

A Decorator is a function that takes in an object, adds functionality to that object, and returns a newly 'decorated' object.

There Four Classes: Functional, Functional Shared, Prototypal, and Pseudoclassical

**Functional Class**

The functional class creates a newInstance with optional inputs - usually using object literal notation.  It can then 'decorate' the new instance with additional methods and returns it.

{% highlight ruby linenos %}
var Robot = function(catchPhrase) {
  var obj = {catchPhrase: catchPhrase};
  obj.speak = function(){console.log(obj.catchPhrase);};
  return obj;
}

var arnold = Robot("I'll be back!");
{% endhighlight %}

**Functional Shared Class**

This is just like the functional class except you have a methods object that is shared by all instances.  This can be done by passing the new instance to extend (available in jQuery) along with the methods object.  

{% highlight ruby linenos %}
var Robot = function(catchPhrase) {
  var obj = {catchPhrase: catchPhrase};
  extend(obj, Robot.methods);
  return obj;
}

Robot.methods = {
  speak: function(){console.log(obj.catchPhrase);}
};

var arnold = Robot("I'll be back!");
{% endhighlight %}

**Protypal Class**

Instead of using object literal notation to create a new instance, we create the new instance with:

Object.create(ClassName.prototype)

This .prototype is just like the methods object above except that it is pre-built in JavaScript.  You can add new functionality to the Class like so:

ClassName.prototype.newMethod = function(){};

{% highlight ruby linenos %}
var Robot = function(catchPhrase) {
  var obj = Object.create(Robot.prototype);
  obj.catchPhrase = catchPhrase;
  return obj;
}

Robot.prototype.speak = function(){console.log(this.catchPhrase);};

var arnold = Robot("I'll be back!");
{% endhighlight %}

**Pseudoclassical Classes**

This is very similar to the Protypal Class, but we use the keyword 'new' to create a new instance.  Using 'new' we don't have to type out Object.create() or return the object.

{% highlight ruby linenos %}
var Robot = function(catchPhrase) {
  this.catchPhrase = catchPhrase;
}

Robot.prototype.speak = function(){console.log(this.catchPhrase);};

var arnold = new Robot("I'll be back!");
{% endhighlight %}
