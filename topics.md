---
layout: page
title: Topics
permalink: /topics/
---

Every note on this site, grouped by topic.

{% for t in site.topics %}
{%- assign key = t[0] -%}{%- assign meta = t[1] -%}
{%- assign notes = site.notes | where: "topic", key | sort: "title" %}
## [{{ meta.title }}]({{ '/topics/' | append: key | append: '/' | relative_url }})

{{ meta.description }}

{% for n in notes -%}
- [{{ n.title }}]({{ n.url | relative_url }}) <span class="status status-{{ n.status }}">{{ n.status }}</span>
{% endfor %}
{% endfor %}
