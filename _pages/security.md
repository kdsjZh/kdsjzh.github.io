---
layout: page
title: security
permalink: /security/
nav: true
---

<div class="security-advisories">

{% assign advisories = site.data.security_advisories | sort: 'date' | reverse %}
{% assign current_year = "" %}
{% for advisory in advisories %}
  {% assign year = advisory.date | date: "%Y" %}
  {% if year != current_year %}
    {% unless forloop.first %}
      </div>
    {% endunless %}
    <h3 class="advisory-year">{{ year }}</h3>
    <div class="advisory-grid">
    {% assign current_year = year %}
  {% endif %}

  {% assign sev_class = advisory.severity | downcase %}
  <div class="advisory-card{% if advisory.severity %} sev-card-{{ sev_class }}{% endif %}">
    <a class="cve-id" href="{{ advisory.citation }}" target="_blank" rel="noopener">{{ advisory.cve_id }}</a>
    <div class="vendor">{{ advisory.vendor }}</div>
    <div class="advisory-tags">
      <span class="tag category">{{ advisory.category }}</span>
      {% if advisory.severity %}
        <span class="tag severity sev-{{ sev_class }}">{{ advisory.severity }}</span>
      {% endif %}
      {% if advisory.bounty %}
        <span class="tag bounty">{{ advisory.bounty }}</span>
      {% endif %}
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

.security-advisories {
  padding-top: 1rem;
  max-width: 1000px;
  margin: auto;
}

.advisory-year {
  font-size: 0.85rem;
  font-weight: 600;
  color: var(--global-font-secondary-color);
  text-transform: uppercase;
  letter-spacing: 0.15em;
  border-bottom: 1px solid var(--global-divider-color);
  padding-bottom: 0.4rem;
  margin: 1.8rem 0 1rem 0;
}

.advisory-grid {
  display: grid;
  grid-template-columns: repeat(auto-fill, 280px);
  gap: 0.8rem;
}

.advisory-card {
  padding: 0.7rem 0.9rem;
  border: 1px solid var(--global-divider-color);
  border-left: 3px solid var(--global-divider-color);
  border-radius: 6px;
  background-color: var(--global-bg-color);
  transition: border-color 0.2s ease, transform 0.2s ease, box-shadow 0.2s ease;
}

.advisory-card.sev-card-high   { border-left-color: #b91c1c; }
.advisory-card.sev-card-medium { border-left-color: #c2783c; }
.advisory-card.sev-card-low    { border-left-color: #94a3b8; }

.advisory-card:hover {
  box-shadow: 0 2px 8px rgba(0, 0, 0, 0.06);
  transform: translateY(-1px);
}

.cve-id {
  display: inline-block;
  font-family: var(--global-code-font-family, monospace);
  font-size: 0.95rem;
  font-weight: 600;
  color: var(--global-theme-color) !important;
  text-decoration: none;
  margin-bottom: 0.2rem;
}

.cve-id:hover {
  text-decoration: underline;
}

.vendor {
  font-size: 0.85rem;
  font-style: italic;
  color: var(--global-font-secondary-color);
  margin-bottom: 0.45rem;
}

.advisory-tags {
  display: flex;
  flex-wrap: wrap;
  gap: 0.35rem;
}

.tag {
  padding: 0.15rem 0.5rem;
  border-radius: 999px;
  font-size: 0.72rem;
  font-weight: 500;
  line-height: 1.4;
  white-space: nowrap;
}

.tag.category {
  background-color: var(--global-bg-color);
  border: 1px solid var(--global-divider-color);
  color: var(--global-text-color);
}

.tag.severity {
  background: none;
  border: none;
  padding: 0.15rem 0;
  font-size: 0.68rem;
  font-weight: 600;
  letter-spacing: 0.1em;
  text-transform: uppercase;
}

.tag.sev-high   { color: #b91c1c; }
.tag.sev-medium { color: #c2783c; }
.tag.sev-low    { color: #94a3b8; }

.tag.bounty {
  background-color: rgba(180, 140, 40, 0.1);
  color: #8a6d1f;
  border: 1px solid rgba(180, 140, 40, 0.3);
}

@media (max-width: 600px) {
  .advisory-grid {
    grid-template-columns: 1fr;
  }
}
</style>
