---
layout: page
title: Topics
permalink: /topics/
---

{% for t in site.topics %}
{%- assign key = t[0] -%}{%- assign meta = t[1] -%}
{%- assign notes = site.notes | where: "topic", key | sort: "title" %}
## [{{ meta.title }}]({{ '/topics/' | append: key | append: '/' | relative_url }})

{{ meta.description }}

{% for n in notes -%}
- [{{ n.title }}]({{ n.url | relative_url }}) <small class="status">{{ n.status }}</small>
{% endfor %}
{% endfor %}
