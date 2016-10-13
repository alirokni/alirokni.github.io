---
layout: post
title:  "Random Quote Machine"
date:   2016-10-13 23:00:00 -0700
categories: Code Snippet
---

Created Random Quote generator using mashape.com api. 
[view in codepen] [codepen]{:target="_blank"}, [code in gist.github][gist]{:target="_blank"}, 

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
          url: 'https://andruxnet-random-famous-quotes.p.mashape.com/', // The URL to the API. You can get this in the API page of the API you intend to consume
          type: 'GET', // The HTTP Method, can be GET POST PUT DELETE etc
          data: {
            "cat": ""
          },
          dataType: 'json',
          success: function(data) {
            $(".content").addClass("quote-text-shadow");
            $("#quoteText").text(data.quote);
            $("#quoteAuthor").text("- " + data.author);
          },
          error: function(err) {
            alert(err.responseText);
          },
          beforeSend: function(xhr) {
            xhr.setRequestHeader("X-Mashape-Authorization", "I6mNOeP0L0mshcX7ZsR6Epc3ISpFp1s4rgZjsnbjAjxbDChxTK"); // Enter here your Mashape key
          }
        });
    };
    function tweetIt() {
      var textToTweet = $("#quote > i > span").text() + "\n" + $(".content .text-right em").text() + " #quote";
       if (textToTweet.length > 140) {
        alert('Tweet should be less than 140 Chars');
        event.preventDefault();
       } else {
        var twtLink = 'http://twitter.com/home?status=' +encodeURIComponent(textToTweet);
        $(".btn-tweet a").attr({
          "href": twtLink,
          "target":'_blank'
        });
       }
    }
    getQuote(); // calling the first time
  });

{% endhighlight %}

[gist]: https://gist.github.com/alirokni/5cb2d061980b2666a5d6c884a03bbfce
[codepen]: https://s.codepen.io/rokni/debug/zKjbdo
