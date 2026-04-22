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
            <img src="{{ post.teaser | relative_url }}" alt="teaser" style="width: 100%; border-radius: 4px; border: 1px solid #eee;">
          {% else %}
            {% comment %} 이미지가 없을 때 보여줄 기본 아이콘이나 빈 칸 {% endcomment %}
            <div style="width: 150px; height: 100px; background: #f9f9f9; border: 1px dashed #ccc; display: flex; align-items: center; justify-content: center; color: #999; font-size: 0.8em;">No Image</div>
          {% endif %}
        </div>

        {% comment %} 우측 텍스트 영역 {% endcomment %}
        <div style="flex: 1;">
          {% include archive-single.html %}
        </div>

      </div>
    {% endfor %}
  </section>
{% endfor %}

</div>
