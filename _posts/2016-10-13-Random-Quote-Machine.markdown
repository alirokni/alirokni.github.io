---
layout: post
title:  "Random Quote Machine"
date:   2016-10-13 23:00:00 -0700
categories: Code Snippet
---

Created Random Quote generator using mashape.com api. Style is uisng CSS Flexible Box Layout, bootstrp v.3 and font-awesome. JS is using jquery v.3.

[view in codepen] [codepen]{:target="_blank"},

[code in gist.github][gist]{:target="_blank"}


{% highlight ruby %}

 $(function() {
    $(".btn-quote button").on('click', function(){
      getQuote();
    });
    $(".btn-tweet a").on('click', function(){
      tweetIt();
    });    
    function getQuote() {
        $(".content").removeClass("quote-text-shadow");
        $.ajax({
          url: 'https://andruxnet-random-famous-quotes.p.mashape.com/', #=> // The URL to the API. You can get this in the API page of the API you intend to consume
          type: 'GET', #=>// The HTTP Method, can be GET POST PUT DELETE etc
          data: {
            "cat": ""
          },
          dataType: 'json',
          success: function(data) { #=>// It needs to move it out and get called
            $(".content").addClass("quote-text-shadow");
            $("#quoteText").text(data.quote);
            $("#quoteAuthor").text("- " + data.author);
          },
          error: function(err) { #=>// It needs to move it out and get called
            alert(err.responseText);
          },
          beforeSend: function(xhr) {
            xhr.setRequestHeader("X-Mashape-Authorization", "I6mNOeP0L0mshcX7ZsR6Epc3ISpFp1s4rgZjsnbjAjxbDChxTK"); #=> // Testing key, enter here your production Mashape key
          }
        });
    };
    function tweetIt() {
      var textToTweet = $("#quote > i > span").text() + "\n" + $(".content .text-right em").text() + " #quote";
       if (textToTweet.length > 140) {
        alert('Tweet should be less than 140 Chars'); #=> // It needs to display error message more appropriately
        event.preventDefault();
       } else {
        var twtLink = 'http://twitter.com/home?status=' +encodeURIComponent(textToTweet);
        $(".btn-tweet a").attr({
          "href": twtLink,
          "target":'_blank'
        });
       }
    }
    getQuote(); #=> // calling the first time
  });

{% endhighlight %}

[gist]: https://gist.github.com/alirokni/5cb2d061980b2666a5d6c884a03bbfce
[codepen]: https://s.codepen.io/rokni/debug/zKjbdo
