---
layout: post
title:  "Search wikipedia with underscorejs temlplate"
date:   2016-10-21 12:00:00 -0700
categories: Code Snippet
---

Created Search wikipedia with underscorejs temlplate using wikipedia api. Style is uisng CSS Flexible Box Layout, bootstrp v.3 and font-awesome. JS is using jquery v.3. and underscore templating

[view in codepen] [codepen]{:target="_blank"},

[code in gist.github][gist]{:target="_blank"}


{% highlight ruby %}

#=> Template
<div class="main-container">
  <a class="wiki-text" href="https://en.wikipedia.org/wiki/Special:Random" target="_blank">Wikipedia Random article <i class="fa fa-external-link" aria-hidden="true"></i></a>
  <p class="wiki-text">or</p>
  <div class="input-group search-group">
    <input type="text" class="form-control search" placeholder="Search for...">
    <span class="input-group-btn search-go">
            <button class="btn btn-secondary" type="button">Search Wikipedia!</button>
      </span>
  </div>
  <ul id="tabsContent" class="list-continer">
    <script type="text/html" id="tabs-data">
       #=> // <% _.each(jsonData[0].query.pages, function(wiki,key,list){ %> used array 
       <% _.each(jsonData.query.pages, function(wiki,key,list){ %>   
            <li class="list-items">
              <a href="https://en.wikipedia.org/?curid=<%= key %>" target="_blank">
                <div class="entry-thumbnail">
                  <% typeof(wiki.thumbnail) != 'undefined' ? print('<img src='+ wiki.thumbnail["source"] +'>')  : print('')  %>
                </div>
                <div class="entry-title"><%= wiki.title  %></div>
                <div class="entry-extract">
                  <%= wiki.extract %>
                  <i class="fa fa-external-link hide" aria-hidden="true"></i>
                </div>
              </a> 
            </li>
       <% }); %>
    </script>
  </ul>
</div>

#=> js
$(function() {
  function doSearch() {
    var searchInput = $('.search').val();
    if (searchInput.length < 1 $("ul#tabsContent li").hasClass( "list-items" ) === true) {
      return false;
    }
    var wikiUrl = "https://en.wikipedia.org/w/api.php";
    $.ajax({
      url: wikiUrl,
      data: {
        'format': 'json',
        'action': 'query',
        'generator': 'search',
        'gsrnamespace': '0',
        'gsrlimit': '10',
        'prop': 'pageimages|extracts',
        'pilimit': 'max',
        'exintro': '',
        'explaintext': '',
        'exsentences': '1',
        'exlimit': 'max',
        'gsrsearch': searchInput.toString()
      },
      dataType: 'jsonp',
      jsonp: 'callback',
      jsonpCallback: 'jsonp_callback', #=> // No need to add. To replace success and error callbacks as a seprate function in case of more complicated cases 
      success: function(data, status) {
        showResult(data);
      },
      error: function(jqXHR, textStatus, errorThrown) {
        alert(textStatus + " " + errorThrown);
      }
    });
  }

  function showResult(data) {
   jsonData = data;   #=> // using JavaScript object notation syntax instead of array
  #=>/* used array in template 
  #=>  jsonData = []; 
  #=>  jsonData.push(data);
  #=> */  
    var tabsTemplate = $("#tabs-data").html();
    if (Boolean(tabsTemplate)) {
      $("#tabsContent").html(_.template(tabsTemplate, {
        jsonData: jsonData
      }));
    }

    $(".list-items").hover(
      function() {
        $(this).find(".fa-external-link").removeClass('hide');
      },
      function() {
        $(this).find(".fa-external-link").addClass('hide');
      }
    );
  }

  $(".search-go").on("click", doSearch);

  $(".search").on("keypress", function(e) {
    if (e.which == 13) {
      doSearch();
    }
  });
});

{% endhighlight %}

[gist]: https://gist.github.com/alirokni/9f47da813f6e0aba353bcc5b575f899a
[codepen]: https://s.codepen.io/rokni/debug/KgbzLN
