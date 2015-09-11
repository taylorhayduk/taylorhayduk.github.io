---
layout: post
title: Tree Recursion
---
**Combinations**

We can use recursion using a tree data structure to come up with all combinations for a given dataset. Here we are going to log all possible combinations of starters, entrees, and desserts at a restaurant.  The data is arranged as an array of arrays.

In our combos function we taken in one parameter, arrayOfArrays.  We then create an empty results array to store each combo.

Next we have our recurse function that takes in an array called 'current' and an array index.  We will use the 'current' array to build each combo and our arrIndex to keep track of which array in the arrayOfArrays we are currently on.

On each recursive pass, we iterate thru the elements in the 'arrIndex' array and each element to the 'current' array.  We then pass this new combo to the recursive function and increment the arrIndex by 1.  Once our arrIndex has passed the length of the arrayOfArrays, we can return the combo.


{% highlight ruby linenos %}
var recursiveMeal = [
  ['salad','chips','popcorn shrimp'], // Starter
  ['steak','shrimp & grits','tofu','hamburger'], // Main Course
  ['ice cream', 'apple pie', 'peach cobbler', 'rootbeer float']  // Dessert
];


var combos = function(arrayOfArrays) {
  var results = [];
  var recurse = function(current, arrIndex) {
    // BASE CASE
    if (arrIndex >= arrayOfArrays.length) {
      results.push(current);
    }
    // RECURSIVE CASE
    else {
      arrayOfArrays[arrIndex].forEach(function(element){
        recurse(current.concat(element), arrIndex+1);
      });
    }
  };
  
  recurse([], 0);
  return results;
};

console.log(combos(recursiveMeal));
{% endhighlight %}

