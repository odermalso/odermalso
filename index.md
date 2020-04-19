---
layout: default
---

{% for post in site.data.instagram %}
<section class="{% cycle 'hell', 'dunkel' %}">
    <div class="container post-container">
        <a href="{{ post.url }}">
            <img class="image" src="{{ post.image_url }}" alt="Veröffentlicht am {{ post.timestamp | date: '%d.%m.%Y' }}">
        </a>
        <div class="description">
            {{ post.description | newline_to_br }}
            <br>
            <br>
            <a class="button" href="{{ post.url }}"><i class="ri-instagram-line"></i> Instagram-Post</a>
        </div>
    </div>
</section>
{% endfor %}
