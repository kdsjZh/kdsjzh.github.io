---
layout: page
permalink: /milestones/
title: milestones
nav: false
---

<div class="achievements-container">

{% assign badges = site.data.milestones | sort: 'date' | reverse %}
{% assign current_year = "" %}
{% for badge in badges %}
{% assign year = badge.date | date: "%Y" %}
{% if year != current_year %}
{% unless forloop.first %}

</div>
{% endunless %}
<h3 class="achievement-year">{{ year }}</h3>
<div class="achievement-grid">
{% assign current_year = year %}
{% endif %}

{% assign cat_lower = badge.category | downcase %}
{% assign icon_class = badge.icon | default: "fa-award" %}

{% if icon_class contains "fa-solid" or icon_class contains "fa-brands" or icon_class contains "fa-regular" %}
{% assign icon_full = icon_class %}
{% else %}
{% assign icon_full = "fa-solid " | append: icon_class %}
{% endif %}

  <div class="achievement-card cat-{{ cat_lower }}">
    <div class="achievement-icon"><i class="{{ icon_full }}"></i></div>
    <div class="achievement-body">
      <div class="achievement-name">{{ badge.name }}</div>
      <div class="achievement-desc">{{ badge.description }}</div>
      <div class="achievement-meta">
        <span class="achievement-date">{{ badge.date | date: "%b %Y" }}</span>
        {% if badge.category %}
          <span class="achievement-cat">{{ badge.category }}</span>
        {% endif %}
      </div>
    </div>
  </div>

{% if forloop.last %}

</div>
{% endif %}
{% endfor %}

</div>

<style>
.post-header {
  display: none;
}

.achievements-container {
  padding-top: 1rem;
  max-width: 1000px;
  margin: auto;
}

.achievement-year {
  font-size: 0.85rem;
  font-weight: 600;
  color: var(--global-font-secondary-color);
  text-transform: uppercase;
  letter-spacing: 0.15em;
  border-bottom: 1px solid var(--global-divider-color);
  padding-bottom: 0.4rem;
  margin: 1.8rem 0 1rem 0;
}

.achievement-grid {
  display: grid;
  grid-template-columns: repeat(auto-fill, 320px);
  gap: 0.8rem;
}

.achievement-card {
  display: flex;
  gap: 0.8rem;
  align-items: flex-start;
  padding: 0.7rem 0.9rem;
  border: 1px solid var(--global-divider-color);
  border-left: 3px solid var(--global-divider-color);
  border-radius: 6px;
  background-color: var(--global-bg-color);
  transition: transform 0.2s ease, box-shadow 0.2s ease;
}

.achievement-card:hover {
  box-shadow: 0 2px 8px rgba(0, 0, 0, 0.06);
  transform: translateY(-1px);
}

.achievement-card.cat-academia { border-left-color: #3a5a8a; }
.achievement-card.cat-hacking  { border-left-color: #b91c1c; }

.achievement-icon {
  flex-shrink: 0;
  width: 42px;
  height: 42px;
  border-radius: 50%;
  display: flex;
  align-items: center;
  justify-content: center;
  font-size: 1.05rem;
  background-color: rgba(0, 0, 0, 0.04);
  color: var(--global-font-secondary-color);
}

.cat-academia .achievement-icon {
  background-color: rgba(58, 90, 138, 0.12);
  color: #3a5a8a;
}

.cat-hacking .achievement-icon {
  background-color: rgba(185, 28, 28, 0.1);
  color: #b91c1c;
}

.achievement-body {
  flex: 1;
  min-width: 0;
}

.achievement-name {
  font-weight: 600;
  font-size: 0.95rem;
  color: var(--global-text-color);
  margin-bottom: 0.2rem;
  line-height: 1.3;
}

.achievement-desc {
  font-size: 0.78rem;
  color: var(--global-font-secondary-color);
  line-height: 1.4;
  margin-bottom: 0.45rem;
}

.achievement-meta {
  display: flex;
  gap: 0.6rem;
  align-items: center;
  font-size: 0.7rem;
}

.achievement-date {
  color: var(--global-font-secondary-color);
}

.achievement-cat {
  text-transform: uppercase;
  letter-spacing: 0.1em;
  font-weight: 600;
  font-size: 0.65rem;
}

.cat-academia .achievement-cat { color: #3a5a8a; }
.cat-hacking  .achievement-cat { color: #b91c1c; }

@media (max-width: 600px) {
  .achievement-grid {
    grid-template-columns: 1fr;
  }
}
</style>
