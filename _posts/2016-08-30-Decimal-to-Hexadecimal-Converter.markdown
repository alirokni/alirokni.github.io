---
layout: post
title:  "Decimal to Hexadecimal Converter"
date:   2016-08-30 23:00:00 -0700
categories: Code Snippet
---

One of the many implementations of Decimal to Hexadecimal Conversion in JavaScript. 

[Edit in JSFiddle][jsfiddle]{:target="_blank"}, -implemented using String Replace(0), Switch(1)- open console from DevTools and hit the Result/JavaScript.

{% highlight ruby %}

//decToHex
var converted = "",
  DecHexMap = { // mapping html Entities
    10: "A",
    11: "B",
    12: "C",
    13: "D",
    14: "E",
    15: "F"
  };

function decToHex(nu, method) {
  var hex = 16,
    nuN = nu,
    remin = nuN % hex,
    quo = parseInt(nuN / hex);

  if (quo >= 0) {
    if (quo > 0) {
      decToHex(quo);
    }
    if (remin >= 10) {
      if (method = 0) {
        remin = String(remin).replace(/(10|11|12|13|14|15)/g, function(s) {
          return DecHexMap[s];
        });
      } else if (method = 1) {
        switch (remin) {
          case (10):
            remin = "A";
            break;
          case (11):
            remin = "B";
            break;
          case (12):
            remin = "C";
            break;
          case (13):
            remin = "D";
            break;
          case (14):
            remin = "E";
            break;
          case (15):
            remin = "F";
            break;
        }
      }
    }
    converted += remin;
  } else {
    converted += remin;
  }
  return converted;
}

console.log(decToHex(12345, 0)); #=> // 3039
console.log(decToHex(123, 1)); #=> // 7B
console.log(decToHex(10, 0)); #=> // A
console.log(decToHex(12345678, 1)); #=> //BC614E

{% endhighlight %}

[jsfiddle]: https://jsfiddle.net/alirokni/rakc3v7h/
