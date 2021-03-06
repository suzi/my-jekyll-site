---
layout: post
title: Better management of IE & Media Query CSS Styles using LESS CSS
categories:
- Technology
tags:
- CSS
- CSS preprocessors
- LESS CSS
- Responsive Web Design
- Web Design
status: publish
type: post
published: true
meta:
  _rawhtml_settings: '0,0,0,0'
  _cws_is_markdown: '1'
  _edit_last: '1'
  dsq_thread_id: '1023936043'
  _wpbitly: http://bit.ly/VIVuH3
  _su_title: ''
---
**Wow!** I just [found out](http://alwaystwisted.com/post.php?s=2012-06-05-another-approach-to-mobile-first-css-whilst-supporting-internet-explorer) that you can do this awesomeness with LESS:

## Inline Media Queries

{% highlight css %}
header {
  background-color: red;
    @media screen only and (min-width: 20em) {
      background-color: blue;
    }
}
{% endhighlight %}

Which when compiled into CSS returns us with this.

{% highlight css %}
header {
  background-color: red;
}

@media screen only and (min-width: 20em) {
  header {
    background-color: blue;
  }
}
{% endhighlight %}


## Using `&` to put a class before instead of after

You can use the  `&`  **after** (normally *before* to combine selector strings) which takes the preceding element and then puts the .ie8 class in front of it. So for example writing this LESS.

{% highlight css %}
header {
  background-color: red;
  .ie8&amp; {
    background-color: blue;
  }
}
{% endhighlight %}

Which gives us this CSS.

{% highlight css %}
header {
  background-color: red;
}
.ie8 header {
  background-color: blue;
}
{% endhighlight %}


## Why this is cool

This really helps prevent fragmentation of styles. Before learning these techniques, I'd often put IE styles in their own `ie.less` sheet and media queries in `media-queries.less`, but with these new techniques, I can keep styles bundled with their other relevant rules.
