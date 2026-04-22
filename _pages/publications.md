---
layout: archive
title: "Publications"
permalink: /publications/
author_profile: true
---

{% if author.googlescholar %}
  <p style="margin-bottom: 20px;">You can also find my articles on <u><a href="{{author.googlescholar}}">my Google Scholar profile</a>.</u></p>
{% endif %}

{% include base_path %}

<style>
  /* 텍스트 사이의 불필요한 여백을 제거하여 리스트의 밀도를 높입니다 */
  .pub-text-content .archive__item,
  .pub-text-content .archive__item-title,
  .pub-text-content h1,
  .pub-text-content h2, 
  .pub-text-content h3 {
    margin-top: 0 !important;
    padding-top: 0 !important;
    margin-bottom: 5px !important;
  }
</style>

{% assign postsByYear = site.publications | group_by_exp: "post", "post.date | date: '%Y'" %}

<div style="text-align: justify; font-size: 0.95em;">

{% for year in postsByYear reversed %}
  <section class="list__item">
    <h1 id="{{ year.name }}" style="margin-top: 40px; margin-bottom: 25px; font-size: 1.7em; border-bottom: 1px solid #ccc; padding-bottom: 5px; color: #333;">
      {{ year.name }}
    </h1>
    
    {% for post in year.items reversed %}
      {% comment %} 이미지를 제거하고 텍스트만 깔끔하게 나열합니다 {% endcomment %}
      <div class="pub-text-content" style="margin-bottom: 30px; padding-left: 5px;">
        {% include archive-single.html %}
      </div>
    {% endfor %}
  </section>
{% endfor %}

</div>

<p style="font-size: 0.8em; margin-top: 60px; color: #777; border-top: 1px inset #eee; padding-top: 20px;">
  <sup>*</sup> Equal authorship
</p>
