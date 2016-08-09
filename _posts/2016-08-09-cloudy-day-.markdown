---
layout: post
title:  "Cloudy Day in Style"
date:   2016-08-09 12:00:00 -0700
categories: Code Snippet
---

An implementations of Cloudy Day in CSS with animation.

<iframe width="100%" height="300" src="//jsfiddle.net/alirokni/re455sdm/embedded/result/" allowfullscreen="allowfullscreen" frameborder="0"></iframe>


{% highlight ruby %}

<!-- HTML -->
<div id="clouds">
  <div class="cloud x1"></div>
  <div class="cloud x2"></div>
  <div class="cloud x3"></div>
  <div class="cloud x4"></div>
  <div class="cloud x5"></div>
</div>

<!-- CSS -->
* {
  margin: 0;
  padding: 0;
}

body {
  overflow: hidden;
}

#clouds {
  padding: 10px 0px;
  background: #c9dbe9;
  background-image: radial-gradient(circle at top left, #FFFF80 10%, #c9dbe9 30%, #eaeaea 60%); // for showing the sun
  height: 300px;
}

.cloud {
  width: 205px;
  height: 66px;
  background: #fff;
  border-radius: 100px;
  position: relative;
}

.cloud:before,
.cloud:after {
  content: "";
  background: #fff;
  width: 100px;
  height: 90px;
  position: absolute;
  left: 10px;
  top: -25px;
  border-radius: 120px;
  transform: rotate(40deg);
}

.cloud:after {
  width: 120px;
  height: 120px;
  top: -50px;
  left: auto;
  right: 15px;
}

.x1 {
  animation: moveclouds 90s linear infinite;
}

.x2 {
  left: 450px;
  top: -10px;
  transform: scale(0.4);
  zoom: 0.4;
  opacity: 1;
  animation: moveclouds 55s linear infinite;
}

.x3 {
  left: 350px;
  top: 130px;
  transform: scale(0.7);
  zoom: 0.7;
  opacity: 0.7;
  animation: moveclouds 45s linear infinite;
}

.x4 {
  left: 50px;
  top: 75px;
  transform: scale(0.66);
  opacity: 0.56;
  animation: moveclouds 50s linear infinite;
}

.x5 {
  left: 590px;
  top: -100px;
  transform: scale(1.4);
  opacity: 0.5;
  animation: moveclouds 60s linear infinite;
}

@keyframes moveclouds {
  from {
    transform: translate3d(500%, 0, 0);
  }
  to {
    transform: translate3d(-200%, 0, 0);
  }
}



{% endhighlight %}


[jsfiddle]: https://jsfiddle.net/alirokni/re455sdm/
