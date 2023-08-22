---
title: Home
layout: default
---

Semantics and Linguistic Theory (SALT) 34 will be hosted by the Linguistics Department at the University of Rochester on May 28 &ndash; 30, 2024.

For questions or comments, please contact <span style="font-family: monospace">[salt34.ur@gmail.com](mailto:salt34.ur@gmail.com)</span>. By attending, you agree to abide by the [Code of Conduct](code-of-conduct/).

<hr/>

## Invited speakers

<ul id="speakers">
  {% for speaker in site.data.program.keynotes %}
  <li>
    <a href="{{ speaker.website }}">{{ speaker.name }}</a> ({{ speaker.institution }})
  </li>
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

<div class="row">
  <div class="three columns" style="text-align: center;">
    <img id="lsa-logo" alt="LSA" src="images/lsa-logo.svg"/>
  </div>
  <div class="nine columns">
    <br/>
    The Linguistic Society of America (LSA) is proud to sponsor SALT and to publish its <a href="https://journals.linguisticsociety.org/proceedings/index.php/SALT">proceedings</a>. Find out more about membership <a href="https://www.linguisticsociety.org/join">here</a>.
  </div>
</div>