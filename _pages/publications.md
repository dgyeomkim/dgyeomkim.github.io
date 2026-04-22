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

{% comment %} 연도별로 그룹화하고 최신 연도순으로 정렬 {% endcomment %}
{% assign postsByYear = site.publications | group_by_exp: "post", "post.date | date: '%Y'" %}

{% for year in postsByYear reversed %}
  <div class="list__item">
    <h2 class="archive__subtitle" style="border-bottom: 1px solid #eee; padding-bottom: 10px; margin-top: 50px;">
      {{ year.name }}
    </h2>
    
    {% comment %} 해당 연도 내의 논문들을 최신 날짜순으로 정렬 {% endcomment %}
    {% for post in year.items reversed %}
      {% include archive-single.html %}
    {% endfor %}
  </div>
{% endfor %}

<p style="font-size: 0.8em; margin-top: 40px;"><sup>*</sup> Equal authorship</p>
