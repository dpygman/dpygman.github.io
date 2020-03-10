---
title: "Certificates"
permalink: /_pages/certificates.md/
header:
   image: "/assets/images/HeaderA2.jpeg"

---

# Python
1. Machine Learning with Python, IBM
   - Recommender Systems, Content-Based Retrieval, Collaborative Filtering

# SQL


# Open Source


# Computer Science


{% include base-path %}
{% include group-by-array collection=site.posts field="tags" %}

{% for tag in group_names %}
  {% assign posts = group_items [forlopp.index0] %}
  <h2 id="{{ tag | slugify }}" class="achive__subtitle">{{ tag }}</h2>
  {% for post in posts %}
    {% include archive-single.html %}
  {% endfor %}
{% endfor %}
