---
layout: page
title: Home
permalink: /
---

This is where I keep my thoughts about things. It is organised by **topic**, not by date, and pages get revised rather than replaced. Think of it as a personal encyclopaedia that is permanently under construction.

Every note carries a **status**: *seed* means a rough idea, *growing* means I am actively working on it, and *evergreen* means it is reasonably complete. Read the seeds charitably.

## Topics

{% for t in site.topics %}
{%- assign key = t[0] -%}{%- assign meta = t[1] -%}
{%- assign notes = site.notes | where: "topic", key -%}
- **[{{ meta.title }}]({{ '/topics/' | append: key | append: '/' | relative_url }})**: {{ meta.description }} <small>({{ notes.size }} note{% if notes.size != 1 %}s{% endif %})</small>
{% endfor %}

## Recently revised

{% assign recent = site.notes | sort: "revised" | reverse %}
{%- for n in recent limit: 5 %}
- [{{ n.title }}]({{ n.url | relative_url }}) <small>{{ n.revised | date: "%Y-%m-%d" }}</small>
{%- endfor %}

See the full [log]({{ '/log/' | relative_url }}), or read [about this site]({{ '/about/' | relative_url }}).
