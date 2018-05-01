---
layout: post
title: "Pure CSS Line Numbers"
date: 2016-07-15 13:11:57 +0100
author: "Tristan White"
tags: CSS
---

I was messing around with an easy way of display code on my website, and stumbled upon a neat trick for making incrementing line numbers with CSS.

{% highlight css %}
.codeblock {
  counter-reset: step;
  counter-increment: step 0;  
}
.codeblock .line:before {
  content: counter(step);
  counter-increment: step;
}
{% endhighlight %}

<br>

The final result is awesome! Check it out:

<p data-height="700" data-theme-id="light" data-slug-hash="bZaQYJ" data-default-tab="result" data-user="triss90" data-embed-version="2" data-pen-title="CSS line numbers" class="codepen">See the Pen <a href="https://codepen.io/triss90/pen/bZaQYJ/">CSS line numbers</a> by Tristan  White (<a href="https://codepen.io/triss90">@triss90</a>) on <a href="https://codepen.io">CodePen</a>.</p>
<script async src="https://static.codepen.io/assets/embed/ei.js"></script>
