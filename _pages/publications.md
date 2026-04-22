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
  /* 우측 텍스트 영역의 제목 상단 여백을 강제로 제거하여 이미지의 상단과 딱 맞춥니다 */
  .pub-text-content h2, 
  .pub-text-content h3 {
    margin-top: 0 !important;
  }
</style>

{% assign postsByYear = site.publications | group_by_exp: "post", "post.date | date: '%Y'" %}

<div style="text-align: justify; font-size: 0.93em;">

{% for year in postsByYear reversed %}
  <section class="list__item">
    <h1 id="{{ year.name }}" style="margin-top: 40px; margin-bottom: 20px; font-size: 1.7em; border-bottom: 1px solid #ccc; padding-bottom: 5px;">
      {{ year.name }}
    </h1>
    
    {% for post in year.items reversed %}
      <div style="display: flex; align-items: flex-start; margin-bottom: 30px; gap: 20px;">
        
        {% comment %} 좌측 이미지 영역 {% endcomment %}
        <div style="flex: 0 0 150px; max-width: 150px;">
          {% if post.teaser %}
            {% comment %} 테두리(border)를 제거했습니다 {% endcomment %}
            <img src="{{ post.teaser | relative_url }}" alt="teaser" style="width: 100%; border-radius: 4px;">
          {% else %}
            {% comment %} 이미지가 없을 때의 박스 테두리도 원치 않으시면 border를 빼시면 됩니다 {% endcomment %}
            <div style="width: 150px; height: 100px; background: #f9f9f9; display: flex; align-items: center; justify-content: center; color: #999; font-size: 0.8em;">No Image</div>
          {% endif %}
        </div>

        {% comment %} 우측 텍스트 영역 {% endcomment %}
        <div class="pub-text-content" style="flex: 1;">
          {% include archive-single.html %}
        </div>

      </div>
    {% endfor %}
  </section>
{% endfor %}

</div>

<p style="font-size: 0.8em; margin-top: 60px; color: #777; border-top: 1px inset #eee; padding-top: 20px;">
  <sup>*</sup> Equal authorship
</p>
