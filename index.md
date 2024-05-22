---
title: Home
layout: default
---

Semantics and Linguistic Theory (SALT) 34 will be hosted by the Linguistics Department at the University of Rochester on May 28 &ndash; 30, 2024. The conference will be held solely in-person, and there will be no remote presentation or attendance option.

As part of SALT34, the SALT Equity and Diversity Committee (SALTED) and the SALT34 organizing committee will hold a workshop: *Spotlighting sign languages in semantics*.

For questions or comments, please contact <span style="font-family: monospace">[salt34.ur@gmail.com](mailto:salt34.ur@gmail.com)</span>. By attending, you agree to abide by the [Code of Conduct](code-of-conduct/).

<hr/>

## Invited speakers

<ul id="speakers">
  {% for presentation in site.data.presentations.keynotes %}
    {% if presentation[0] != "name" %}
      {% assign speakerid = presentation[1].authors[0] %}
      {% assign speaker = site.data.people[speakerid] %}
      <li>
        {% if speaker.website != null %}<a href="{{ speaker.website }}">{{ speaker.name }}</a>{% else %}{{ speaker.name }}{% endif %} ({{ speaker.institutions | join: ", " }})
      </li>
    {% endif %}
  {% endfor %}
</ul>

<hr/>

## Announcements

<table class="announce">
  <tbody>
    {% for announcement in site.data.announcements %}
    <tr>
      <td class="time">
        [{{ announcement.date }}]
      </td>
      <td>
        {{ announcement.text }}
      </td>
    </tr>
    {% endfor %}
  </tbody>
</table>
<!-- <hr style="border-style: dashed; border-color: #eae9e6"> -->

<hr/>

## Important dates

<table class="announce">
  <tbody>
    {% for milestone in site.data.important_dates %}
    <tr>
      <td class="time">
        [{{ milestone.date }}]
      </td>
      <td>
        {{ milestone.text }}
      </td>
    </tr>
    {% endfor %}
  </tbody>
</table>

<hr/>

## Sponsors

SALT34 is sponsored by the [University of Rochester Department of Linguistics](https://www.sas.rochester.edu/lin/) and the [Center for Language Sciences at the University of Rochester](https://www.sas.rochester.edu/cls/). The [Linguistic Society of America](https://www.lsadc.org/) publishes [the conference proceedings](https://journals.linguisticsociety.org/proceedings/index.php/SALT).