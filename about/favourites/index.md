---
layout: page
title: Favourites
---

# Articles

{% for favourite in site.data.favourites %}* [{% if favourite.starred %}★{% endif %} {{ favourite.title }}]({{ favourite.link }})
{% endfor %}

# Blogs

{% for blog in site.data.blogs %} * [{{ blog.title }}]({{ blog.link }})
{% endfor %}