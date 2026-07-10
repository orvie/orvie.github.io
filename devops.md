---
layout: page
title: DevOps
permalink: /devops/
---

# ⚙️ DevOps

Notes on containers, CI/CD, and infrastructure tooling.

## Topics

{% for post in site.devops %}
- [{{ post.title }}]({{ post.url }})
{% endfor %}

## Quick Overview

This section covers:
- **Docker** - Building and running containers
- **CI/CD** - Automated build, test, and deploy pipelines
- **Infrastructure** - Provisioning and configuration tooling

---

### Getting Started

1. Read through the Docker basics guide
2. Set up a CI/CD pipeline for your project
3. Check troubleshooting for common issues
