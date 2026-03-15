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
    {% for page in site.pages %}
        {% if page.path contains '/articles/' %}
            {% assign ext = page.path | split: '.' | last %}
            {% if ext == 'html' %}
                {% assign html_count = html_count | plus: 1 %}
            {% endif %}
        {% endif %}
    {% endfor %}

    {% if html_count > 0 %}
    <h2>Typora Articles</h2>
    <ul class="post-list">
        {% for page in site.pages %}
            {% if page.path contains '/articles/' %}
                {% assign ext = page.path | split: '.' | last %}
                {% if ext == 'html' %}
                <li>
                    <a href="{{ page.url | relative_url }}">{{ page.title }}</a>
                </li>
                {% endif %}
            {% endif %}
        {% endfor %}
    </ul>
    {% endif %}
</div>
