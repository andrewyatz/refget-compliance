---
layout: default
title: Refget Compliance Report
---
## Notice

The following site tested the compliance of refget v1 implementations. This site is no longer maintained. To find out more about refget consult our [public GA4GH product page](https://www.ga4gh.org/product/refget/), [refget Sequences specification](https://ga4gh.github.io/refget/sequences/) and new product [refget sequence collections](https://ga4gh.github.io/refget/seqcols/).

## Results
<table class="primary">
  <thead>
  <tr>
    <th>Server</th>
    {% for description in site.data.descriptions %}
      <th>{{ description[1].title }}</th>
    {% endfor %}
  </tr>
  </thead>
  <tbody>
    {% for server in site.data.servers %}
    {% assign server_key=server[0] %}
    {% assign results=site.data[server_key][0] %}
    {% assign report_link="/reports/" | append: server_key | append: '.html' %}
    <tr>
      <td><a href='{{ site.baseurl }}{{report_link}}'>{{ results.server }}</a></td>
        {% for description in site.data.descriptions %}
          {% assign testname = description[0] %}
          {% assign summary=results.high_level_summary[testname] %}
          {% assign lookup=site.data.result[summary.result] %}
          {% assign href= "#" | append: description[1].id %}
          <td><span class='label {{lookup.class}}'><a href='{{ site.baseurl | append: report_link | append: href  }}'>{{lookup.text}}</a></span></td>
        {% endfor %}
    </tr>
    {% endfor %}
  </tbody>
</table>

## Useful Links
- [Refget specification](https://samtools.github.io/hts-specs/refget.html)
- [Compliance document](https://compliancedoc.readthedocs.io/)
- [Compliance tool](https://github.com/ga4gh/refget-compliance-suite)
