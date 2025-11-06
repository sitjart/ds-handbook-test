---
title: Maturity model
---

Maturity model description goes here...

## Domains

The RDM Maturity Model is structured into several domains, each representing a key area of research data management.

<div class="accordion accordion-flush" id="domainsAccordion">
 {% for domain in site.data.mm.domains %}
  <div class="accordion-item">
    <h3 class="accordion-header">
      <button class="accordion-button {% unless forloop.first %}collapsed{% endunless %}" 
              type="button"
              data-bs-toggle="collapse" 
              data-bs-target="#collapse{{forloop.index}}" 
              aria-expanded="{% if forloop.first %}true{% else %}false{% endif %}" 
              aria-controls="collapse{{forloop.index}}">
        <strong>{{ domain.name }}</strong>
      </button>
    </h3>
    <div id="collapse{{forloop.index}}" class="accordion-collapse collapse {% if forloop.first %}show{% endif %}" data-bs-parent="#domainsAccordion">
      <div class="accordion-body">
        {{ domain.description }}
      </div>
    </div>
  </div>
  {% endfor %}
</div>

## Indicators
<div class="accordion accordion-flush" id="indicatorsAccordion">
 {% for domain in site.data.mm.domains %}
  <div class="accordion-item">
    <h3 class="accordion-header">
      <button class="accordion-button {% unless forloop.first %}collapsed{% endunless %}" 
              type="button"
              data-bs-toggle="collapse" 
              data-bs-target="#collapse2{{forloop.index}}" 
              aria-expanded="{% if forloop.first %}true{% else %}false{% endif %}" 
              aria-controls="collapse2{{forloop.index}}">
        <strong>{{ domain.name }}</strong>
      </button>
    </h3>
    <div id="collapse2{{forloop.index}}" class="accordion-collapse collapse {% if forloop.first %}show{% endif %}" data-bs-parent="#indicatorsAccordion">
      <div class="accordion-body">
        {% assign domain_indicators = site.data.mm.indicators | where:"Domain", domain.name %}
        {% if domain_indicators != empty %}
        <table class="table table-bordered table-striped">
          <thead>
            <tr>
              <th>Subdomain</th>
              <th>Indicator</th>
              <th>Maturity Levels</th>
            </tr>
          </thead>
          <tbody>
            {% for indicator in domain_indicators %}
            <tr>
              <td>{{ indicator.Subdomain }}</td>
              <td>[{{ indicator["Indicator level"] }}] {{ indicator.Indicator }}</td>
              <td>
                <ol>
                  {% for level in indicator["Maturity levels"] %}
                  <li>{{ level }}</li>
                  {% endfor %}
                </ol>
              </td>
            </tr>
            {% endfor %}
          </tbody>
        </table>
        {% endif %}
      </div>
    </div>
  </div>
  {% endfor %}
</div>


## Version information

- Version: {{ site.data.mm.version["Version number"] }} [{{ site.data.mm.version["Version description"] }}]
- Release date: {{ site.data.mm.version["Timestamp"] }}