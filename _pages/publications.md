---
layout: archive
title: "Publications"
permalink: /publications/
author_profile: true
---

{% if author.googlescholar %}
  <p style="margin-bottom: 2em; font-size: 1.1em;">You can also find my articles on <u><a href="{{author.googlescholar}}">my Google Scholar profile</a>.</u></p>
{% endif %}

{% include base_path %}

<style>
  /* 1. 불필요한 여백 강제 제거 */
  .pub-text-content .archive__item,
  .pub-text-content .archive__item-title,
  .pub-text-content h1,
  .pub-text-content h2, 
  .pub-text-content h3 {
    margin-top: 0 !important;
    padding-top: 0 !important;
  }
  
  /* 2. 리스트 레이아웃 최적화 */
  .pub-list-item {
    display: flex;
    align-items: flex-start;
    margin-bottom: 40px;
    gap: 30px; /* 이미지와 텍스트 사이의 숨통(여백) 확보 */
  }
  
  /* 3. 썸네일 영역 크기 확대 */
  .pub-thumbnail {
    flex: 0 0 220px; /* 기존 150px는 너무 좁습니다. 220px로 확대합니다. */
    max-width: 220px;
  }

  .pub-thumbnail img {
    width: 100%;
    border-radius: 4px;
    border: 1px solid #e0e0e0;
    box-shadow: 0 2px 4px rgba(0,0,0,0.05); /* 시각적 깊이감 추가 */
  }

  /* 4. 텍스트 영역 글꼴 복구 */
  .pub-text-content {
    flex: 1;
    font-size: 1em; /* 강제로 줄였던 폰트 크기를 원래대로 복구합니다. */
    line-height: 1.5;
  }

  /* 5. 모바일 반응형 처리 (핵심) */
  @media (max-width: 768px) {
    .pub-list-item {
      flex-direction: column; /* 화면이 좁아지면 위아래로 분리 */
    }
    .pub-thumbnail {
      flex: 0 0 auto;
      max-width: 100%;
      margin-bottom: 15px;
    }
  }
</style>

{% assign postsByYear = site.publications | group_by_exp: "post", "post.date | date: '%Y'" %}

<div class="publications-wrapper">

{% for year in postsByYear reversed %}
  <section class="year-section">
    <h1 id="{{ year.name }}" style="margin-top: 40px; margin-bottom: 20px; font-size: 1.8em; font-weight: bold; border-bottom: 2px solid #333; padding-bottom: 5px;">
      {{ year.name }}
    </h1>
    
    {% for post in year.items reversed %}
      <div class="pub-list-item">
        
        {% comment %} 좌측 이미지 영역 {% endcomment %}
        <div class="pub-thumbnail">
          {% if post.teaser %}
            <img src="{{ post.teaser | relative_url }}" alt="{{ post.title }} thumbnail">
          {% else %}
            <div style="width: 100%; padding-bottom: 75%; background: #f4f4f4; border: 1px solid #ddd; border-radius: 4px; position: relative;">
              <span style="position: absolute; top: 50%; left: 50%; transform: translate(-50%, -50%); color: #aaa; font-size: 0.9em;">No Image</span>
            </div>
          {% endif %}
        </div>

        {% comment %} 우측 텍스트 영역 {% endcomment %}
        <div class="pub-text-content">
          {% include archive-single.html %}
        </div>

      </div>
    {% endfor %}
  </section>
{% endfor %}

</div>

<p style="font-size: 0.85em; margin-top: 60px; color: #666; border-top: 1px solid #eee; padding-top: 20px;">
  <sup>*</sup> Equal authorship
</p>
