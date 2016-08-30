---
layout: post
title:  "Prime number"
date:   2016-08-30 16:00:00 -0700
categories: Code Snippet
---

One of the many implementations of Prime number in JavaScript. For more information, visit [wikipedia][wikipedia]{:target="_blank"}.

[Edit in JSFiddle][jsfiddle]{:target="_blank"}, open console from DevTools and hit the Result/JavaScript.

{% highlight ruby %}

Number.prototype.isPrime = function(number) {
  var start = 3,
    num = this,
    finalNo = 0,
    res = num + " is not Prime",
    result = [];

  while (start <= num) {
    if (start % 2 !== 0 && start % 3 !== 0) {
      finalNo = start;
      result.push(finalNo);
    }
    start++;
    if (finalNo == num) {
      res = num + " is a prime number";
    }
  }
  //console.log(result);
  return res + " and all prime numbers of " + num + " are: " + result;
};
console.log((101).isPrime()); #=> 101 is a prime number and all prime numbers of 101 are: 5,7,11,13,17,19,23,25,29,31,35,37,41,43,47,49,53,55,59,61,65,67,71,73,77,79,83,85,89,91,95,97,101
console.log((12).isPrime());  #=> 12 is not Prime and all prime numbers of 12 are: 5,7,11
console.log((97).isPrime());  #=> 97 is a prime number and all prime numbers of 97 are: 5,7,11,13,17,19,23,25,29,31,35,37,41,43,47,49,53,55,59,61,65,67,71,73,77,79,83,85,89,91,95,97

{% endhighlight %}


[jsfiddle]: https://jsfiddle.net/alirokni/j2dj4nra/
[wikipedia]: https://en.wikipedia.org/wiki/Prime_number
