---
layout: post
title:  "HTML Sanitizer"
date:   2016-08-10 16:00:00 -0700
categories: Code Snippet
---

One of the many implementations of encoding decoding html in JavaScript. For other ways, visit [stackoverflow][stackoverflow]{:target="_blank"}.

[Edit in JSFiddle][jsfiddle]{:target="_blank"}, open console from DevTools and hit the Result/JavaScript.

{% highlight ruby %}

var encapsulateEntityMap = { // mapping html Entities
  "&": "&amp;",
  "<": "&lt;",
  ">": "&gt;",
  "/": "&sol;",
  '"': "&quot;",
  "'": "&apos;",
  "&amp;": "&",
  "&lt;": "<",
  "&gt;": ">",
  "&sol;": "/",
  "&quot;": '"',
  "&apos;": "'"
};

function HTMLsanitizer(string) {
  if (!string) {
    return false;
  }
  if (!!(string.match(/(<|>|\/|\"|\'|&[^a-z])/g))) { // only do encodeing for these entities, in case of & don't decode &amp; only & 
    return String(string).replace(/[&<>"'\/]/g, function(s) { // replace each entity with encoded map representative "&": "&amp;"
      return encapsulateEntityMap[s];
    });
  } else {
    return String(string).replace(/(&amp;|&lt;|&gt;|&sol;|&quot;|&apos;)/g, function(s) { // replace each encoded entity with decoded map equivalent "&amp;": "&"
      return encapsulateEntityMap[s];
    });
  }

}

console.log(HTMLsanitizer("<p>this \"is\" a</p>", "encode")); => &lt;p&gt;this &quot;is&quot; a&lt;&sol;p&gt;
console.log(HTMLsanitizer("&lt;p&gt;this &quot;is&quot; a&lt;&sol;p&gt;")); => <p>this "is" a</p>
console.log(HTMLsanitizer()); => false
console.log(HTMLsanitizer(HTMLsanitizer("<p>this \"is\" a</p>", "encode"))); => <p>this "is" a</p>


{% endhighlight %}


[jsfiddle]: https://jsfiddle.net/alirokni/wd110hop/
[stackoverflow]: http://stackoverflow.com/a/1219983
