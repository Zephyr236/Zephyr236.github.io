---
layout: default
title: Home
---

<div class="home">
    <h1>Welcome to Zephyr's Blog</h1>

    <h2>Recent Posts</h2>
    <ul class="post-list">
        {% for post in site.posts %}
        <li>
            <span class="post-date">{{ post.date | date: "%B %d, %Y" }}</span>
            <a href="{{ post.url | relative_url }}">{{ post.title }}</a>
        </li>
        {% endfor %}
    </ul>

    {% assign html_count = 0 %}
    {% for file in site.static_files %}
        {% if file.path contains '.html' %}
            {% unless file.path contains 'index.html' or file.path contains '_layouts' %}
                {% assign html_count = html_count | plus: 1 %}
            {% endunless %}
        {% endif %}
    {% endfor %}

    {% if html_count > 0 %}
    <h2>Articles</h2>
    <ul class="post-list">
        {% for file in site.static_files %}
            {% if file.path contains '.html' %}
            {% unless file.path contains 'index.html' or file.path contains '_layouts' %}
            <li>
                <span class="post-date">{{ file.name | slice: 0, 10 }}</span>
                <a href="{{ file.url | relative_url }}">{{ file.name | remove: '.html' | replace: '-', ' ' }}</a>
            </li>
            {% endunless %}
            {% endif %}
        {% endfor %}
    </ul>
    {% endif %}
</div>
