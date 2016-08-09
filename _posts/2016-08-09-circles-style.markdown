---
layout: post
title:  "Circles in Style"
date:   2016-08-09 15:20:00 -0700
categories: Code Snippet
---

5 ways to create circles in CSS.

<iframe width="100%" height="300" src="//jsfiddle.net/alirokni/qmk6ba7c/embedded/result/" allowfullscreen="allowfullscreen" frameborder="0"></iframe>


{% highlight ruby %}

<!-- HTML -->
<div id="circles01"></div>
<div id="circles02"></div>
<div id="circles03"></div>
<div id="circles04"></div>
<div id="circles05"></div>

<!-- CSS -->
#circles01 {
  width: 20px;
  height: 20px;
  background: red;
  border-radius: 50%;
  position: relative;
  margin: 100px auto;
}
#circles01:before,
#circles01:after {
  content: '';
  display: block;
  position: absolute;
  height: inherit;
  width: inherit;
  border-radius: inherit;
  background: blue;
}
#circles01:before {
  left: -40px;
}
#circles01:after {
  right: -40px;
}

#circles02 {
  width: 20px;
  height: 20px;
  background: red;
  border-radius: 50%;
  position: relative;
  margin: 100px auto;
  box-shadow: -40px 0 0 0 blue, 40px 0 0 0 green, -40px 40px 0 0 brown, 40px -40px 0 0 pink, 1px 40px 0 0 yellow;
}

#circles03 {
  width: 20px;
  height: 20px;
  background: red;
  border-radius: 50%;
  position: relative;
  margin: 100px auto;
}
#circles03:before,
#circles03:after {
  content: '';
  display: block;
  position: absolute;
  height: inherit;
  width: inherit;
  background: blue;
  -webkit-clip-path: circle(10px at 10px 10px);
  clip-path: circle(10px at 10px 10px);
}
#circles03:before {
  left: -40px;
}
#circles03:after {
  right: -40px;
}

#circles04 {
  width: 20px;
  height: 20px;
  background: red;
  border-radius: 50%;
  position: relative;
  margin: 100px auto;
}
#circles04:before,
#circles04:after {
  content: '';
  display: block;
  position: absolute;
  height: inherit;
  width: inherit;
  background: -webkit-radial-gradient(center ellipse, #0000ff 70%, rgba(0, 0, 0, 0) 5%);
  background: radial-gradient(ellipse at center, #0000ff 70%, rgba(0, 0, 0, 0) 5%);
}
#circles04:before {
  left: -40px;
}
#circles04:after {
  right: -40px;
}

#circles05 {
  width: 20px;
  height: 20px;
  background: red;
  border-radius: 50%;
  position: relative;
  margin: 100px auto;
}
#circles05:before,
#circles05:after {
  content: '';
  display: block;
  position: absolute;
  height: inherit;
  width: inherit;
  background: url(data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIGhlaWdodD0iMTAwIiB3aWR0aD0iMTAwIj48Y2lyY2xlIGN4PSIxMCIgY3k9IjEwIiByPSIxMCIgc3Ryb2tlPSJub25lIiBzdHJva2Utd2lkdGg9IjMiIGZpbGw9ImJsdWUiLz48L3N2Zz4=);
}
#circles05:before {
  left: -40px;
}
#circles05:after {
  right: -40px;
}

{% endhighlight %}

