hello my name is alexanny and this my my blog so feel welcome tp read as much as you want to your hearts content 

<ul>
  {% for post in site.posts %}
    <li>
      <a href="{{ post.url | relative_url }}">{{ post.title }}</a>
    </li>
  {% endfor %}
</ul>