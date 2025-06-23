---
layout: page
title: 📘 Содержание
permalink: /
---

Добро пожаловать в блог **Budget Helper** — пошаговый дневник создания Telegram Mini App  
на стекe React, NestJS, PostgreSQL, Docker, GitHub Actions и Telegram SDK.

---

{% assign grouped = site.posts | group_by_exp: "post", "post.categories[0]" %}

{% for category in grouped %}
### 🔹 {{ category.name | capitalize }}

<ul>
  {% assign posts = category.items | sort: "order" %}
  {% for post in posts %}
    <li>
      <a href="{{ post.url | relative_url }}">{{ post.title }}</a>
      <small> — {{ post.date | date: "%d.%m.%Y" }}</small>
    </li>
  {% endfor %}
</ul>
{% endfor %}
