---
layout: page
title: Log
permalink: /log/
---

{% assign recent = site.notes | sort: "revised" | reverse %}
| Revised | Note | Topic | Status |
|---|---|---|---|
{% for n in recent -%}
| {{ n.revised | date: "%Y-%m-%d" }} | [{{ n.title }}]({{ n.url | relative_url }}) | {{ site.topics[n.topic].title }} | {{ n.status }} |
{% endfor %}
