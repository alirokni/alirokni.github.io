---
layout: post
title:  "Phone Numbers"
date:   2016-08-09 08:00:00 -0700
categories: Code Snippet
---

One of the implementation of phone number formatting in JavaScript.

[Edit in JSFiddle][jsfiddle]{:target="_blank"}, open console from DevTools and hit the Result/JavaScript.

{% highlight ruby %}

function solution(S) {
  var str = S,
    res = '',
    phone = [],
    phoneNo = '';

  res = str.replace(/[\ -]+/g, ''); // allow numbers as string

  for (i = 0; i < res.length; i++) {
    if (i % 3 === 0 && i !== 0 && i < 8) { // add - before each 3 digits
      phone.push("-" + res[i]);
    } else if (i % 2 === 0 && i !== 0 && i > 8) { // add - before each 2 digits
      phone.push("-" + res[i]);
    } else {
      phone.push(res[i]);
    }
  }
  return phone.toString().split(',').join(phoneNo);
}

console.log(solution('555372654011234556')); #=> // 555-372-6540-11-23-45-56
console.log(solution('00-44-48 5555 8361')); #=> // "004-448-5555-83-61"
console.log(solution('00')); #=> //"00"
console.log(solution('0-44 --00 --55 ')); #=>  //"044-005-5"
console.log(solution('044 0-0 -- 0')); #=>  //"044-000"
console.log(solution('0')); #=>  //"0"
console.log(solution('555372654')); #=> //"555-372-654"


{% endhighlight %}


[jsfiddle]: https://jsfiddle.net/alirokni/bqmwhuzk/embed/

