---
layout: post
title: Tree Recursion
---
**Combinations**

We can use recursion using a tree data structure to come up with all combinations for a given dataset. Here we are going to log all possible combinations of starters, entrees, and desserts at a restaurant.  The data is arranged as an array of arrays.

In our combos function we taken in one parameter, arrayOfArrays.  We then create an empty results array to store each combo.

When creating a recursive function, you need a base case and a recursive case.  Our base case will push the current combo to the results array when we have incremented thru all interior arrays.  Our recursive case will go thru the current array, add each element to combo and (for each element) call the recursion again while incrementing arrIndex.

Finally, we return the results array that holds all our combos.


{% highlight js %}
var recursiveMeal = [
  ['salad','chips','bloomin\' onion'],
  ['steak','shrimp & grits','tofu','hamburger'],
  ['ice cream', 'apple pie', 'peach cobbler', 'rootbeer float']
];


var combos = function(arrayOfArrays) {
  var results = [];
  var recurse = function(combo, arrIndex) {
    // BASE CASE
    if (arrIndex >= arrayOfArrays.length) {
      results.push(combo);
    }
    // RECURSIVE CASE
    else {
      arrayOfArrays[arrIndex].forEach(function(element){
        recurse(combo.concat(element), arrIndex+1);
      });
    }
  };
  
  recurse([], 0);
  return results;
};

console.log(combos(recursiveMeal));
{% endhighlight %}

