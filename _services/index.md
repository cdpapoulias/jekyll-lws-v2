---
layout: page
title: Services
permalink: /services
section: services
intro_paragraph: >
   Leading Web Studio builds & maintains great websites for great companies.

---
{% for service in site.services %}
  <h3>{{ service.name }}</h3>
  {{ service.short-intro }}
  <a href="{{service.url}}">Learn More</a>
{% endfor %}
