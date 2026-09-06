---
layout: page
title: Home
permalink: /
---

## Topics

{% for t in site.topics %}
{%- assign key = t[0] -%}{%- assign meta = t[1] -%}
{%- assign notes = site.notes | where: "topic", key -%}
- **[{{ meta.title }}]({{ '/topics/' | append: key | append: '/' | relative_url }})**: {{ meta.description }} <small>({{ notes.size }} note{% if notes.size != 1 %}s{% endif %})</small>
{% endfor %}

{%- assign recent = site.notes | sort: "revised" | reverse -%}
{%- if recent.size > 0 %}
## Recently revised

{% for n in recent limit: 5 -%}
- [{{ n.title }}]({{ n.url | relative_url }}) <small>{{ n.revised | date: "%Y-%m-%d" }}</small>
{% endfor %}
{%- endif %}
