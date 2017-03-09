---
layout: page
title: Articles
---

<ul class="posts">
  {% for post in site.posts %}

    {% unless post.next %}
      <h3>{{ post.date | date: '%Y' }}</h3>
    {% else %}
      {% capture year %}{{ post.date | date: '%Y' }}{% endcapture %}
      {% capture nyear %}{{ post.next.date | date: '%Y' }}{% endcapture %}
      {% if year != nyear %}
        <h3>{{ post.date | date: '%Y' }}</h3>
      {% endif %}
    {% endunless %}

    <li itemscope>
      <a href="{{ site.baseurl }}{{ post.url }}">{{ post.title }}</a>
      <p class="post-date">
        <span>
          <i class="fa fa-calendar" aria-hidden="true"></i>
          {% assign m = post.date | date: "%-m" %}
          {{ post.date | date: "%-d" }}
          {% case m %}
            {% when '1' %}janvier
            {% when '2' %}février
            {% when '3' %}mars
            {% when '4' %}avril
            {% when '5' %}mai
            {% when '6' %}juin
            {% when '7' %}juillet
            {% when '8' %}août
            {% when '9' %}septembre
            {% when '10' %}octobre
            {% when '11' %}novembre
            {% when '12' %}décembre
          {% endcase %} - <i class="fa fa-clock-o" aria-hidden="true"></i>
          {% include read-time.html %}
        </span>
      </p>
    </li>

  {% endfor %}
</ul>
{{ post.date | date: "%-d" }}
