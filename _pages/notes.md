---
title: "Research Notes Archive"
permalink: /notes/
layout: single
author_profile: false
hide_title: true
excerpt: "Archived physics notes and earlier projects by Hyejin Kim."
---

<div class="page-intro">
  <p class="eyebrow">Archive</p>
  <p class="page-deck">Earlier research notes, course projects, and computational physics explorations.</p>
</div>

These posts document work from my undergraduate years. They remain available for reference, while my current research is summarized on the [Research page]({{ '/research/' | relative_url }}). This archive is intentionally kept separate from the primary site navigation.

<div class="notes-list">
{% for post in site.posts %}
  <article>
    <time datetime="{{ post.date | date_to_xmlschema }}">{{ post.date | date: "%B %Y" }}</time>
    <h2><a href="{{ post.url | relative_url }}">{{ post.title }}</a></h2>
    {% if post.excerpt %}<p>{{ post.excerpt | strip_html | truncate: 180 }}</p>{% endif %}
  </article>
{% endfor %}
</div>
