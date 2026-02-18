---
permalink: /
title: "About Me"
author_profile: true
redirect_from:
  - /about/
  - /about.html
---

Hello! I am a PhD student in Operations Research at [Columbia University’s IEOR Department](https://ieor.columbia.edu/). I am fortunate to be advised by [Christian Kroer](https://www.columbia.edu/~ck2945/). My research focuses on problems at the intersection of game theory and mechanism design. Previously, I graduated with a bachelor of engineering in industrial engineering from the American University of Beirut with high distinction.

# News

{% assign sorted_news = site.data.news | sort: "date" | reverse %}

<ul style="list-style-type: none; padding-left: 0;">
{% for item in sorted_news %}
<li class="news__item">
<small>{{ item.date | date: "%B %Y" }}</small>
<p>{{ item.content }}</p>
</li>
{% endfor %}
</ul>
