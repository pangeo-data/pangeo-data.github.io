---
layout: page
title: Design Documents
description: Brainstorming needs for geoscience software
---

These design documents are rough drafts that summarize the brainstorming that
took place at the inaugural
[pangeo workshop]({% post_url 2016-11-06-pangeo_data %}).

{% assign ddocs = site.collections | where:"label","design_docs" | first %}
{% for page in ddocs.docs %}
- [{{page.title}}]({{ page.url | prepend: site.baseurl }})
{% endfor %}

{{ ddocs | json }}

Note that these documents are not updated; many of the ideas have been
superceded by more mature projects lists in the
[packages] directory.
