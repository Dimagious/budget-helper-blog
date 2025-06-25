---
layout: page          # какой макет вам нужен
title: "📘 Содержание" # заголовок вверху
permalink: /          # оставляем «/», чтобы это была главная
---

### 🔹 Введение
<ul>
  {% assign posts = site.categories["Введение"] | sort: "order" %}
  {% for post in posts %}
    <li>
      <a href="{{ post.url | relative_url }}">{{ post.title }}</a>
      <small> — {{ post.date | date: "%d.%m.%Y" }}</small>
    </li>
  {% endfor %}
</ul>

### 🔹 Backend
<ul>
  {% assign posts = site.categories["Backend"] | sort: "order" %}
  {% for post in posts %}
    <li>
      <a href="{{ post.url | relative_url }}">{{ post.title }}</a>
      <small> — {{ post.date | date: "%d.%m.%Y" }}</small>
    </li>
  {% endfor %}
</ul>
