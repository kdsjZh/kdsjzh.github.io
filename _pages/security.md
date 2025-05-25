---
layout: page
title: security
permalink: /security/
nav: true

---

<div class="security-advisories">

{% assign advisories = site.data.security_advisories | sort: 'date' | reverse %}
{% for advisory in advisories %}
  <div class="advisory-card">
    <div class="advisory-header">
      <div class="cve-id">{{ advisory.cve_id }}</div>
      <div class="vendor">{{ advisory.vendor }}</div>
    </div>

    <div class="advisory-tags">
      <span class="tag category">{{ advisory.category }}</span>
      {% if advisory.severity %}
        <span class="tag severity">🔥 {{ advisory.severity }}</span>
      {% endif %}
      {% if advisory.bounty %}
        <span class="tag bounty">💰 {{ advisory.bounty }}</span>
      {% endif %}
    </div>

    {% if advisory.citation %}
      <div class="advisory-citation">
        <a href="{{ advisory.citation }}" target="_blank">🔗 Advisory </a>
      </div>
    {% endif %}
  </div>
{% endfor %}

</div>

<style>
.security-advisories {
  display: flex;
  flex-direction: column;
  gap: 1.2rem;
  padding-top: 1rem;
  max-width: 900px;
  margin: auto;
}

.advisory-card {
  padding: 1.2rem 1.5rem;
  border: 1px solid var(--global-border-color);
  border-radius: 12px;
  background-color: var(--global-bg-color);
  box-shadow: 0 4px 8px rgba(0,0,0,0.06);
  transition: box-shadow 0.3s ease;
}

.advisory-card:hover {
  box-shadow: 0 6px 12px rgba(0,0,0,0.12);
}

.advisory-header {
  display: flex;
  justify-content: space-between;
  font-size: 1.1rem;
  font-weight: 600;
  color: var(--global-text-color);
  margin-bottom: 0.5rem;
}

.cve-id {
  font-family: monospace;
  background: var(--global-accent-color);
  color: var(--global-text-color-light); /* updated */
  padding: 0.2rem 0.5rem;
  border-radius: 4px;
}

.vendor {
  font-style: italic;
  color: var(--global-font-secondary-color);
}

.advisory-tags {
  display: flex;
  gap: 0.6rem;
  flex-wrap: wrap;
  margin: 0.6rem 0;
}

.tag {
  padding: 0.25rem 0.6rem;
  border-radius: 4px;
  font-size: 0.9rem;
  font-weight: 500;
  background-color: var(--global-accent-color);
  color: var(--global-text-color-light); /* updated */
}

.advisory-citation {
  margin-top: 0.5rem;
  font-size: 0.9rem;
}

.advisory-citation a {
  color: var(--global-link-color);
  text-decoration: underline dotted;
}
</style>
