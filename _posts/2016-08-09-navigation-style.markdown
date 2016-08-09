---
layout: post
title:  "Site Navigation in Style"
date:   2016-08-09 13:00:00 -0700
categories: Code Snippet
---

An implementations of Site Navigation in CSS with linear-gradient background-image transition .

<iframe width="100%" height="300" src="//jsfiddle.net/alirokni/Ljuqw1yp/embedded/result/" allowfullscreen="allowfullscreen" frameborder="0"></iframe>


{% highlight ruby %}

<!-- HTML -->
<nav>
  <ul id="nav">
    <li class="listItem"><a href="#" class="navigation">Updates</a></li>
    <li class="listItem"><a href="#" class="navigation">Features</a></li>
    <li class="listItem"><a href="#" class="navigation">Bookmarks</a></li>
    <li class="listItem"><a href="#" class="navigation">Widgets</a></li>
    <li class="listItem"><a href="#" class="navigation">envelope</a></li>
  </ul>
</nav>

<!-- CSS -->
a.navigation {
  background-image: linear-gradient(45deg, #e15100 50%, #fff 50%);
  background-size: 140% 1200%;
  border: 1px solid #e15100;
  color: #e15100;
  text-align: center;
  background-image: linear-gradient(45deg, #e15100 50%, #fff 50%);
  transition: background-position 1s ease 0s;
  padding: 1rem 2rem;
  text-decoration: none;
}

a.navigation:hover {
  color: #ffffff;
  background-position: 0 +100%;
}

#nav li {
  display: inline-block;
  margin: 1.2rem .2rem
}


{% endhighlight %}


[jsfiddle]: https://jsfiddle.net/alirokni/re455sdm/
