---
layout: archive
title: "Publications"
permalink: /publications/
author_profile: true
---

{% if author.googlescholar %}
  You can also find my articles on <u><a href="{{author.googlescholar}}">my Google Scholar profile</a>.</u>
{% endif %}

{% include base_path %}

<div style="text-align: justify; font-size: 0.95em;">

{% assign postsByYear = site.publications | group_by_exp: "post", "post.date | date: '%Y'" %}

{% for year in postsByYear reversed %}
  <div class="list__item">
    {% comment %} 상단 여백을 줄이고 연도 크기를 조정했습니다 {% endcomment %}
    <h1 id="{{ year.name }}" style="margin-top: 30px; margin-bottom: 15px; font-size: 1.8em; border-bottom: 2px solid #333; padding-bottom: 8px;">
      {{ year.name }}
    </h1>
    
    <div style="line-height: 1.5;">
      {% for post in year.items reversed %}
        <div style="margin-bottom: 20px;">
          {% include archive-single.html %}
        </div>
      {% endfor %}
    </div>
  </div>
{% endfor %}

</div>

<p style="font-size: 0.8em; margin-top: 50px;"><sup>*</sup> Equal authorship</p>
