---
layout: archive
title: "Publications"
permalink: /publications/
author_profile: true
---

{% if site.author.googlescholar %}
  <div class="wordwrap">You can also find my articles on <a href="{{site.author.googlescholar}}">my Google Scholar profile</a>.</div>
{% endif %}

{% include base_path %}

<!-- {% for post in site.publications reversed %}
  {% include archive-single.html %}
{% endfor %} -->


<!-- Add preprints and ongoing work on top -->
{% assign ongoing = site.publications | where: "pub_type", "ongoing" %}


<h2>Submitted and Ongoing Work</h2>
{% if ongoing.size > 0 %}

  <ul>
    {% for post in ongoing reversed %}
      {% include archive-single.html %}
    {% endfor %}
  </ul>
  
{% else %}
  <p>No ongoing work or preprints available at the moment. Please refer to the year-wise list below for my publications.</p>
{% endif %}


<!-- group by publication year -->
<h2>Publications by Year</h2>

{% assign publications_by_year = site.publications | group_by_exp:"post", "post.date | date: '%Y'" %}
{% for year in publications_by_year reversed %}
  {% assign year_items = year.items | where_exp: "item", "item.pub_type != 'ongoing'" %}
  {% if year_items.size == 0 %}
    {% continue %}
  {% endif %}
  <h3>{{ year.name }}</h3>
  <ul>
    {% for post in year.items %}
    {% unless post.pub_type == "ongoing" %}
      {% include archive-single.html %}
    {% endunless %}
    {% endfor %}
  </ul>
{% endfor %}