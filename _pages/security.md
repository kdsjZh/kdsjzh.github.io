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

  <div class="advisory-card">
    <a class="cve-id" href="{{ advisory.citation }}" target="_blank" rel="noopener">{{ advisory.cve_id }}</a>
    <div class="vendor">{{ advisory.vendor }}</div>
    <div class="advisory-tags">
      <span class="tag category">{{ advisory.category }}</span>
      {% if advisory.severity %}
        {% assign sev_class = advisory.severity | downcase %}
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
  font-size: 1.1rem;
  font-weight: 600;
  color: var(--global-font-secondary-color);
  border-bottom: 1px solid var(--global-divider-color);
  padding-bottom: 0.3rem;
  margin: 1.5rem 0 0.8rem 0;
  letter-spacing: 0.05em;
}

.advisory-grid {
  display: grid;
  grid-template-columns: repeat(auto-fill, 280px);
  gap: 0.8rem;
}

.advisory-card {
  padding: 0.75rem 0.9rem;
  border: 1px solid var(--global-divider-color);
  border-radius: 8px;
  background-color: var(--global-bg-color);
  transition: border-color 0.2s ease, transform 0.2s ease;
}

.advisory-card:hover {
  border-color: var(--global-theme-color);
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
  border: 1px solid transparent;
}

.tag.sev-high {
  background-color: rgba(220, 53, 69, 0.12);
  color: #c0392b;
  border-color: rgba(220, 53, 69, 0.3);
}

.tag.sev-medium {
  background-color: rgba(255, 159, 64, 0.15);
  color: #b35900;
  border-color: rgba(255, 159, 64, 0.35);
}

.tag.sev-low {
  background-color: rgba(108, 117, 125, 0.15);
  color: #4d5358;
  border-color: rgba(108, 117, 125, 0.3);
}

.tag.bounty {
  background-color: rgba(40, 167, 69, 0.12);
  color: #1e7e34;
  border: 1px solid rgba(40, 167, 69, 0.3);
}

@media (max-width: 600px) {
  .advisory-grid {
    grid-template-columns: 1fr;
  }
}
</style>
