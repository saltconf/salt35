---
title: Home
layout: default
---

The 35th meeting of Semantics and Linguistic Theory (SALT 35) will be hosted by the Linguistics Department at Harvard University, Cambridge, MA on May 20 – 22, 2025. Presentations at SALT35 will take place in person. In participating, you agree to abide by the [Code of Conduct](code-of-conduct/).

For questions or comments, please contact <span style="font-family: monospace">[salt35.harvard@gmail.com](mailto:salt35.harvard@gmail.com)</span>. 

For more general information on the goals and history of the conference, visit the permanent website for the [SALT conference.](http://saltconf.github.io)

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

{%raw%}
<!--- 
## Sponsors

{%endraw%}
--->
## Organizing Committee

Gennaro Chierchia, Kathryn Davidson, Tanya Bondarenko, Vincent Rouillard, Ankana Saha, Natasha Thalluri, Nayantara Das, Yiqian Wang

## Sponsors

SALT35 is supported by the [Mind, Brain and Behaviour Interfaculty Initiative](https://mbb.harvard.edu), and the [Institute for Quantitative Social Science](https://www.iq.harvard.edu/about) at Harvard University. The [Linguistics Society of America](https://www.lsadc.org)  handles the registration and publishes the conference proceedings.

 <img src=" assets/images/harvard-logo.svg" alt="Harvard logo" width="150" /> <img src=" assets/images/lsa-logo.svg" alt="LSA logo" width="150" /> 

###### This website has been adapted by Natasha Thalluri (graduate student at Harvard Linguistics), from the SALT34 and SALT33 websites following the websites for SALT30 (Sarah Murray), SALT31 (Roman Feiman), and SALT32 (Rafael Herrera Jiménez), in collaboration with SALT’s steering committee. The logo for SALT35 has been designed by Yvette Yi-Chi Wu (graduate student at Harvard Linguistics).
