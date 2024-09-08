---
layout: page
title: devlog
---

<section>
  {% if site.logs[0] %}

    {% capture currentyear %}{{ 'now' | date: "%Y" }}{% endcapture %}
    {% capture firstpostyear %}{{ site.logs[0].date | date: '%Y' }}{% endcapture %}
    {% if currentyear == firstpostyear %}
        <h3>This year's logs</h3>
    {% else %}  
        <h3>{{ firstpostyear }}</h3>
    {% endif %}

    {%for post in site.logs %}
      {% unless log.next %}
        <ul>
      {% else %}
        {% capture year %}{{ log.date | date: '%Y' }}{% endcapture %}
        {% capture nyear %}{{ log.next.date | date: '%Y' }}{% endcapture %}
        {% if year != nyear %}
          </ul>
          <h3>{{ log.date | date: '%Y' }}</h3>
          <ul>
        {% endif %}
      {% endunless %}
        <li><time>{{ log.date | date:"%d %b" }} - </time>
          <a href="{{ log.url | prepend: site.baseurl | replace: '//', '/' }}">
            {{ log.title }}
          </a>
        </li>
    {% endfor %}
    </ul>

  {% endif %}
</section>