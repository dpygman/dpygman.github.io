# David Pygman's Portfolio Page Readme

Hello and welcome to my under construction Portfolio page.

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

##### Mathjax
{% if page.mathjax %}
<script type="text/javascript" async
        src="https://cdn.mathjax.org/mathjax/latest/MathJax.js?config+TeX-MML-AM_CHTML">
</script>
{% endif %}
