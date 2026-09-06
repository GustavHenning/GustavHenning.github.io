---
layout: page
title: Log
permalink: /log/
---

Notes ordered by when they were last revised. This is the closest thing the site has to a blog feed.

{% assign recent = site.notes | sort: "revised" | reverse %}
| Revised | Note | Topic | Status |
|---|---|---|---|
{% for n in recent -%}
| {{ n.revised | date: "%Y-%m-%d" }} | [{{ n.title }}]({{ n.url | relative_url }}) | {{ site.topics[n.topic].title }} | {{ n.status }} |
{% endfor %}
