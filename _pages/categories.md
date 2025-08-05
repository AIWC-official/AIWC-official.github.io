---
layout: page
title: 카테고리
description: 주요 주제별로 콘텐츠를 탐색해보세요
permalink: /categories/
---

<div class="categories-page">
  {% assign categories = site.categories | sort %}
  {% for category in categories %}
    <div class="category-card">
      <h2><a href="{{ category.url }}">{{ category.title }}</a></h2>
      <p>{{ category.description }}</p>
      {% assign category_name = category.title %}
      {% assign post_count = site.posts | where_exp: "post", "post.categories contains category_name" | size %}
      <p class="post-count">{{ post_count }}개의 게시물</p>
    </div>
  {% endfor %}
</div>

<style>
  .categories-page {
    display: grid;
    grid-template-columns: repeat(auto-fill, minmax(300px, 1fr));
    gap: 20px;
    margin-top: 30px;
  }
  
  .category-card {
    padding: 20px;
    border-radius: 12px;
    background-color: var(--background-alt-color);
    transition: transform 0.3s ease;
  }
  
  .category-card:hover {
    transform: translateY(-5px);
    background-color: var(--background-alt-color-2);
  }
  
  .category-card h2 {
    margin-bottom: 10px;
  }
  
  .post-count {
    margin-top: 10px;
    font-weight: bold;
    color: var(--heading-font-color);
  }
</style>