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

<div style="text-align: justify;">

{% assign postsByYear = site.publications | group_by_exp: "post", "post.date | date: '%Y'" %}

{% for year in postsByYear reversed %}
  <div class="list__item">
    {% comment %} 연도 크기를 키우고 스타일을 강조했습니다 {% endcomment %}
    <h1 id="{{ year.name }}" style="margin-top: 60px; margin-bottom: 20px; font-size: 2em; border-bottom: 2px solid #333; padding-bottom: 10px;">
      {{ year.name }}
    </h1>
    
    {% for post in year.items reversed %}
      <div style="margin-bottom: 15px;">
        {% include archive-single.html %}
      </div>
    {% endfor %}
  </div>
{% endfor %}

</div>

<p style="font-size: 0.8em; margin-top: 50px;"><sup>*</sup> Equal authorship</p>
