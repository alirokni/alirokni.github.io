---
layout: post
title:  "Fibonacci Number"
date:   2016-08-08 23:00:00 -0700
categories: Code Snippet
---

One of the implementation of [Fibonacci number][fibonacci-wiki]{:target="_blank"} in JavaScript. For toher ways, visit [stackoverflow][stackoverflow]{:target="_blank"}.

First code is the initial step to reconstruct the formula, second code is using loop within function and last one is using recursion to list Fibonacci number.

[Edit in JSFiddle][jsfiddle]{:target="_blank"}, open console from DevTools and hit the Result/JavaScript.

{% highlight ruby %}

var a = 0, // 1st nu.
    b = 1, // 2nd nu.
    res = [0, 1];
//  1st nu. + 2nd nu.
a = a + b; // 0 + 1;
res.push(a); // 1

a = a + b; // 1 + 1
res.push(a); // 2

a = a + b; // 2 + 1
res.push(a); // 3

// 2nd nu. = 1st nu. - 2nd nu.
// 1st nu. = 1st nu. + 2nd nu.
b = a - b; // 3 - 1
a = a + b; // 3 + 2; 
res.push(a); // 5

b = a - b; // 5 - 2
a = a + b; // 5 + 3; 
res.push(a); // 8

b = a - b;
a = a + b; //   8 + 5; 
res.push(a); // 13

b = a - b;
a = a + b; //   13 + 8; 
res.push(a); // 21

b = a - b;
a = a + b; //   21 + 13; 
res.push(a); // 34

console.log(res);
#=> prints [0, 1, 1, 2, 3, 5, 8, 13, 21, 34]


var fibonacci = console.log((function(n) {
  var a = 0,
    b = 1,
    res = [a, b];

  for (var i = 0; i < n; i++) {
    if (i > 2) { // for numbers larger than 2
      b = a - b; // 2nd nu. =  1st nu. - 2nd nu.  
    }
    a = a + b; // all numbers calclulated usign 1st nu. = 1st nu. + 2nd nu.
    res.push(a);
  }
  return res;
})(11));
#=> prints [0, 1, 1, 2, 3, 5, 8, 13, 21, 34, 55, 89, 144]

function fibonacciRecursion(n) {
  console.log(calcFibonacci(n));
}

function calcFibonacci(n) {
  var a = 0,
    b = 1,
    res = [a, b];

  for (var i = 0; i < n; i++) {
    if (i > 2) {
      b = a - b;
    }
    a = a + b;
    res.push(a);
  }

  return res;
}

fibonacciRecursion(11);
#=> prints [0, 1, 1, 2, 3, 5, 8, 13, 21, 34, 55, 89, 144]
{% endhighlight %}


[jsfiddle]: https://jsfiddle.net/alirokni/jemjw47k/
[fibonacci-wiki]: https://en.wikipedia.org/wiki/Fibonacci_number
[stackoverflow]: http://stackoverflow.com/questions/7944239/generating-fibonacci-sequence
