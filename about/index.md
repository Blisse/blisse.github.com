---
layout: page
title: About
---

<img src="{{ site.data.profile.profile_picture | prepend:site.baseurl }}" width="40%">

## Hello!

{% for line in site.data.profile.about %}
{{ line | markdownify }}
{% endfor %}

## Quotes

{% for quote in site.data.quotes %}
{% for line in quote.lines %}> {{ line | markdownify }}{% endfor %}>
> - {{ quote.cite }}
{% endfor %}