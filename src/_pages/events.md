---
title: events
description: Upcoming events from the tabete community.
permalink: /events/
layout: default
---

{% assign upcoming = site.events | sort: "date" %}
{% if upcoming.size > 0 %}

  <ul class="events-list">
    {% for event in upcoming %}
      <li class="event-card">
        {% if event.header_image %}
          <a class="event-card-thumb" href="{{ event.url | relative_url }}">
            <img
              src="{{ event.header_image | relative_url }}"
              alt="{{ event.title }} banner"
            />
          </a>
        {% endif %}
        <div class="event-card-body">
          <h3><a href="{{ event.url | relative_url }}">{{ event.title }}</a></h3>
          <p class="event-meta">
            {% if event.date %}
            <time datetime="{{ event.date | date_to_xmlschema }}">
              {{ event.date | date: "%-d %B %Y" }}
            </time>
            {% endif %}
            {% if event.venue %}
            &nbsp;◈&nbsp; {{ event.venue }}
            {% endif %}
            {% if event.speaker %}
            &nbsp;◈&nbsp; {{ event.speaker }}
            {% endif %}
          </p>
          {% if event.description %}
            <p class="event-description">{{ event.description }}</p>
          {% endif %}
          {% if event.signup_link %}
            <a
              href="{{ event.signup_link }}"
              class="event-signup-link"
              target="_blank"
              rel="noopener noreferrer"
              >Sign up &rarr;</a
            >
          {% endif %}
        </div>
      </li>
    {% endfor %}
  </ul>
{% else %}
  <p>No upcoming events. Check back soon!</p>
{% endif %}
