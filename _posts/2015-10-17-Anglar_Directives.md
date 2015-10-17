---
layout: post
title: Intro to Angular Directives
---

Directives allow HTML to express behavior of a web application.

Say you have a webpage where you're listing out a bunch all players in a team.  Your homepage might look something like the following.

{% highlight html %}
<html lang="en" ng-app="myApp">
  <head>
  </head>
  <body layout="column" ng-controller="AppCtrl">
    <h1>Georgia Bulldogs</h1>
    <h2>Athens, Georgia</h2>
    <h4>Georgia Bulldogs Starting Lineup:</h4>
    <ul>
      <li ng-repeat="player in team.player">
        <p>{{player.name}}</p>
        <p>{{player.number}}</p>
        <p>{{player.position}}</p>
        <p>{{player.hometown}}</p>
        <p>{{player.weight}}</p>
        <p>{{player.height}}</p>
      </li>
    </ul>
    ...
  </body>
</html>
{% endhighlight %}

You are likely to have a lot more html than what is written above.  Instead of putting all that Starting Lineup information in the homepage, we can separate it into a directive.

In you app.js, create a directive for the Lineup.  In the directive, we return an object with two important values: restrict and templateUrl.

The restrict value can be set to 'E', 'A', or 'C'.  This is to choose if you want to replace the Lineup with an element or attribute.

Element:
<player-lineup></player-lineup>

Attribute:
<div player-lineup="expression"></div>

