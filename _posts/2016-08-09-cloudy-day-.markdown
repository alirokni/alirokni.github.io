---
layout: post
title:  "Cloudy Day in Style"
date:   2016-08-09 12:00:00 -0700
categories: Code Snippet
---

One of the implementations of Cloudy Day in CSS with animation.

<div>
<script async src="//jsfiddle.net/alirokni/re455sdm/embed/result/"></script>
</div>

[Edit in JSFiddle][jsfiddle]{:target="_blank"}

{% highlight ruby %}
<!-- HTML -->
<div id="clouds">
  <div class="sun"></div>
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
  /*background: linear-gradient(120deg, #c9dbe9, #eaeaea);*/
  background-image: radial-gradient(circle at top left, #FFFF80 10%, #c9dbe9 30%, #eaeaea 60%);
  height: 300px;
}

.sun {
  /*width: 120px;
  height: 120px;
  background: #FFD800;
  border-radius: 150px;
  margin-left: 50px;
  background-image: radial-gradient(circle at top left, #FFFF80 20%, rgba(204, 153, 153, 0.4) 30%, #E6E6FF 60%);*/
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
  top: -400px;
  transform: scale(0.4);
  zoom: 0.4;
  opacity: 1;
  animation: moveclouds 55s linear infinite;
}

.x3 {
  left: 350px;
  top: -170px;
  transform: scale(0.7);
  zoom: 0.7;
  opacity: 0.7;
  animation: moveclouds 45s linear infinite;
}

.x4 {
  left: 50px;
  top: -75px;
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
    /* margin-left: 150%; */
    transform: translate3d(800%, 0, 0);
  }
  to {
    /* margin-left: -50%; */
    transform: translate3d(-100%, 0, 0);
  }
}


{% endhighlight %}


[jsfiddle]: https://jsfiddle.net/alirokni/re455sdm/
