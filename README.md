# David Pygman's Portfolio Page Readme

### Code Pen

#### Future Data Analytics _pages file

---
title: "Analytics"
permalink: /Analytics/
header: "/images/Deming.png"
---

{% include base_path%}
{% include group-by-array collection=site.posts field="tags" %}

{% for tag in group_names %}
  {% assign posts = group_items [forloop.index0] %}
  <h2 id="{{ tag | slugify }}" class="archive_subtitle">{{ tag }}</h2>
  {% for post in posts %}
    {% include archive-single.html %}
  {% endfor%}
{% endfor %}
