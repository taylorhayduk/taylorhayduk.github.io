---
layout: post
title: Easy Cheat Sheet for Decorators and Classes in JavaScript
---

In JavaScript it can be easy to confuse Decorators and the four types of Classes.  Just remember that Decorators 'decorate' pre-made objects, and Classes create newInstances.

A Decorator is a function that takes in an object, adds functionality to that object, and returns a newly 'decorated' object.

There Four Classes: Functional, Functional Shared, Prototypal, and Pseudoclassical

Functional Class: The functional class creates a newInstance with optional inputs - usually using object literal notation ** var obj == {} **.  It can then 'decorate' the newInstance with additional methods.  It then returns the newInstance.

Functional Shared Class: This is just like the functional class except you have a methodsObject that is shared by all instances.  This can be done by passing the newInstance to extend along with a methodsObject.  

Protypal Class: Instead of using object literal notation to create a newInstance, we create the newInstance with **Object.create(ClassName.prototype)**.  This .prototype is an ordinary object except that it is pre-built in JavaScript.  You can add new functionality to the Class like so: ClassName.prototype.newMethod = function(){};

Pseudoclassical Classes:  This is very similar to the Protypal Class, but we use the keyword 'new' to create a new instance.  Using 'new' we don't have to type out Object.create() or return the object.
