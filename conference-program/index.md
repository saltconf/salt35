---
title: Program
layout: default
---

<p>
  <b>NB:</b> This schedule is preliminary and subject to change. Abstracts will be made available in the near future.
</p>

{% for day in site.data.program %}

<h2 id="{{ day.day }}">{{ day.date }}</h2>

<table class="program">
  <tbody>
    {% for event in day.events %}
    {% if event.type == "talk_session" %}
    <tr class="talkChairinfo"><td colspan="3">{{ event.name }}</td></tr>
    {% for talk in event.subevents %}
    {% assign talkinfo = site.data.presentations.talks[talk.talkid] %}
    <tr class="talk">
      <td class="time">{{ talk.time }}</td>
      <td class="title">{{ talkinfo.title }}</td>
      <!-- <a href="abstracts/{{ talk.talkid }}">{{ talkinfo.title }}</a> -->
      <td class="authors">
        {% for authorid in talkinfo.authors %}
          {% assign author = site.data.people[authorid] %}
          {{ author.name }} {% unless forloop.last %}<br/>{% endunless %}
        {% endfor %}
      </td>
    </tr>
    {% endfor %}
    {% elsif event.type == "keynote" %}
    {% assign talkinfo = site.data.presentations.keynotes[event.talkid] %}
    <tr class="invitedChairinfo"><td colspan="3">Invited Talk</td></tr>
    <tr class="invited">
      <td class="time">{{ event.time }}</td>
      <td class="title">{{ talkinfo.title }}</td>
      <!-- <a href="abstracts/{{ talk.talkid }}">{{ talkinfo.title }}</a> -->
      <td class="authors">
        {% for authorid in talkinfo.authors %}
          {% assign author = site.data.people[authorid] %}
          {{ author.name }} {% unless forloop.last %}<br/>{% endunless %}
        {% endfor %}
      </td>
    </tr>
    {% elsif event.type == "workshop" %}
    <tr class="posterChairinfo"><td colspan="3">SALTED Workshop</td></tr>
    <tr class="poster">
      <td class="time">{{ event.time }}</td>
      <td class="title" colspan="2">{{ event.name }}</td>
    </tr>
    {% elsif event.type == "lightning" %}
    <tr class="posterChairinfo"><td colspan="3">Lightning Talk Session</td></tr>
    <tr class="postertalk">
      <td class="time">10:15-11:00</td>
      <td class="title" colspan="2">
        <!-- <span id="lightOnePosterArr" class="collapsed"></span> -->
        {{ event.name }}
        <!-- <a id="lightOnePosterSwitch" href="javascript:void(0)" onclick="lightning('posterInfoLightOne', 'lightOnePosterArr')">{{ event.name }}</a> -->
      </td>
    </tr>
    <!-- <tr class="posterInfoLightOne hidden">
      <td class="time">&nbsp;</td>
      <td class="title"><a href="abstracts/mascarenhas-picat-salt29-abstract.pdf">'Might' as a generator of alternatives: the view from reasoning</a></td>
      <td class="authors">Salvador Mascarenhas and Léo Picat</td>
    </tr> -->
    {% elsif event.type == "poster" %}
    <tr class="posterChairinfo"><td colspan="3">Poster Session</td></tr>
    <tr class="postertalk">
      <td class="time">{{ event.time }}</td>
      <td class="title" colspan="2">{{ event.name }}</td>
    </tr>
    {% else %}
    <tr class="{{ event.type }}">
      <td class="time">{{ event.time }}</td>
      <td class="title">{{ event.name }}</td>
      <td></td>
    </tr>
    {% endif %}
    {% endfor %}
  </tbody>
</table>

{% endfor %}