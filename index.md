### 🔹 Введение

<ul>
  {% assign posts = site.categories["введение"] | sort: "order" %}
  {% for post in posts %}
    <li>
      <a href="{{ post.url | relative_url }}">{{ post.title }}</a>
      <small> — {{ post.date | date: "%d.%m.%Y" }}</small>
    </li>
  {% endfor %}
</ul>

### 🔹 Backend

<ul>
  {% assign posts = site.categories["backend"] | sort: "order" %}
  {% for post in posts %}
    <li>
      <a href="{{ post.url | relative_url }}">{{ post.title }}</a>
      <small> — {{ post.date | date: "%d.%m.%Y" }}</small>
    </li>
  {% endfor %}
</ul>
