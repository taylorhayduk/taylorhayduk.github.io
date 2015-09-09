---
layout: post
title: Tree Permutations
---


{% highlight ruby linenos %}

var phoneDigitsToLetters = {
  0: '0',
  1: '1',
  2: 'ABC',
  3: 'DEF',
  4: 'GHI',
  5: 'JKL',
  6: 'MNO',
  7: 'PQRS',
  8: 'TUV',
  9: 'WXYZ'
};


var telephoneWords = function(digitString) {
  digitArr = digitString.split('');
  var results = [];

  var recurse = function(string, digitArr) {
    if (digitArr.length === 0) {
      results.push(string);
    }
    else {
      var letters = phoneDigitsToLetters[digitArr[0]].split('');
      letters.forEach(function(letter){
        recurse(string+letter, digitArr.slice(1));
      });
    }
  };
  
  recurse("", digitArr);
  return results;
};

console.log(telephoneWords('5309'));

{% endhighlight %}
