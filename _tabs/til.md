---
layout: default
title: "TIL"
icon: fas fa-calendar-day
order: 1
---

{% include lang.html %}

{% assign all_pinned = site.til | where: 'pin', 'true' %}
{% assign all_normal = site.til | where_exp: 'item', 'item.pin != true and item.hidden != true' %}
{% assign posts = site.til %}

<!-- Get pinned posts on current page -->

{% assign visible_start = paginator.page | minus: 1 | times: paginator.per_page %}
{% assign visible_end = visible_start | plus: paginator.per_page %}

{% if all_pinned.size > visible_start %}
  {% if all_pinned.size > visible_end %}
    {% assign pinned_size = paginator.per_page %}
  {% else %}
    {% assign pinned_size = all_pinned.size | minus: visible_start %}
  {% endif %}

  {% for i in (visible_start..all_pinned.size) limit: pinned_size %}
    {% assign posts = posts | push: all_pinned[i] %}
  {% endfor %}
{% else %}
  {% assign pinned_size = 0 %}
{% endif %}

<!-- Get normal posts on current page -->
{% assign normal_size = paginator.posts | size | minus: pinned_size %}

{% if normal_size > 0 %}
  {% if pinned_size > 0 %}
    {% assign normal_start = 0 %}
  {% else %}
    {% assign normal_start = visible_start | minus: all_pinned.size %}
  {% endif %}

  {% assign normal_end = normal_start | plus: normal_size | minus: 1 %}
  {{ normal_start }} - {{ normal_end }}

  {% for i in (normal_start..normal_end) %}
    {% assign posts = posts | push: all_normal[i] %}
  {% endfor %}
{% endif %}

## Today I Learned (TIL)

**TIL** stands for **Today I Learned**. This is a collection of small, practical things I come across day-to-day, which I thought were worth remembering and sharing with other people. Content and code examples might not be completely accurate.

<div id="post-list" class="flex-grow-1 px-xl-1">
  {% for post in posts %}
    <article class="card-wrapper card">
      <a href="{{ post.url | relative_url }}" class="post-preview row g-0 flex-md-row-reverse">
        {% assign card_body_col = '12' %}

        {% if post.image %}
          {% assign src = post.image.path | default: post.image %}
          {% unless src contains '//' %}
            {% assign src = post.media_subpath | append: '/' | append: src | replace: '//', '/' %}
          {% endunless %}

          {% assign alt = post.image.alt | xml_escape | default: 'Preview Image' %}

          {% assign lqip = null %}

          {% if post.image.lqip %}
            {% capture lqip %}lqip="{{ post.image.lqip }}"{% endcapture %}
          {% endif %}

          <div class="col-md-5">
            <img src="{{ src }}" alt="{{ alt }}" {{ lqip }}>
          </div>

          {% assign card_body_col = '7' %}
        {% endif %}

        <div class="col-md-{{ card_body_col }}">
          <div class="card-body">
            <h1 class="card-title my-2 mt-md-0">{{ post.title }}</h1>

            <div class="card-text content mt-0 mb-3">
              <div class="content">
                {% include til-description.html %}
              </div>
            </div>

            <div class="post-meta flex-grow-1 d-flex align-items-end">
              <div class="me-auto">
                <!-- posted date -->
                <i class="far fa-calendar fa-fw me-1"></i>
                {% include datetime.html date=post.date lang=lang %}

              </div>

              {% if post.pin %}
                <div class="pin ms-1">
                  <i class="fas fa-thumbtack fa-fw"></i>
                  <span>{{ site.data.locales[lang].post.pin_prompt }}</span>
                </div>
              {% endif %}
            </div>
            <!-- .post-meta -->
          </div>
          <!-- .card-body -->
        </div>
      </a>
    </article>
  {% endfor %}
</div>
<!-- #post-list -->

{% if paginator.total_pages > 1 %}
  {% include post-paginator.html %}
{% endif %}
