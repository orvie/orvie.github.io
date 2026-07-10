---
layout: default
title: Home
---

<div class="home">
  <h1 class="page-heading">Welcome to Orvie's Knowledge Base</h1>
  
  <p>This is a personal knowledge base for project notes, configuration tips, and learning resources.</p>

  <h2>📑 Main Sections</h2>
  
  <ul>
    <li><a href="/web-deployment/">🚀 Web Deployment</a> - AWS S3, CloudFront, React deployment</li>
    <li><a href="/social-networks/">🔗 Social Networks</a> - OAuth, API integration, authentication</li>
    <li><a href="/ai-study/">🤖 AI & Self-Study</a> - Machine Learning, LLMs, Deep Learning</li>
    <li><a href="/devops/">⚙️ DevOps</a> - Docker, CI/CD, infrastructure tooling</li>
    <li><a href="/quick-reference/">💡 Quick Reference</a> - Commands, links, and resources</li>
  </ul>

  <h2>Latest Posts</h2>

  <ul class="post-list">
    {% for post in site.posts %}
      <li>
        <span class="post-meta">{{ post.date | date: "%b %-d, %Y" }}</span>
        <h3>
          <a class="post-link" href="{{ post.url | relative_url }}">
            {{ post.title | escape }}
          </a>
        </h3>
      </li>
    {% endfor %}
  </ul>

  <h2>Recent Posts from Collections</h2>

  <h3>Web Deployment</h3>
  <ul>
    {% for post in site.web_deployment limit:5 %}
      <li><a href="{{ post.url | relative_url }}">{{ post.title }}</a></li>
    {% endfor %}
  </ul>

  <h3>Social Networks</h3>
  <ul>
    {% for post in site.social_networks limit:5 %}
      <li><a href="{{ post.url | relative_url }}">{{ post.title }}</a></li>
    {% endfor %}
  </ul>

  <h3>AI & Self-Study</h3>
  <ul>
    {% for post in site.ai_study limit:5 %}
      <li><a href="{{ post.url | relative_url }}">{{ post.title }}</a></li>
    {% endfor %}
  </ul>

  <h3>DevOps</h3>
  <ul>
    {% for post in site.devops limit:5 %}
      <li><a href="{{ post.url | relative_url }}">{{ post.title }}</a></li>
    {% endfor %}
  </ul>
</div>
