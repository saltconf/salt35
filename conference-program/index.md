---
title: Program
layout: default
---

<script type="text/javascript">
   function lightning(cls, arr) {
       var rows = document.getElementsByClassName(cls);
       for (var i = 0; i < rows.length; i++) {
	         rows[i].classList.toggle("hidden");
       }
       document.getElementById(arr).classList.toggle("collapsed");
   }
</script>

All talks and posters at SALT34 will take place on the University of Rochester's [River Campus](https://www.google.com/maps/place/Wegmans+Hall/@43.1260797,-77.6326735,17z/). 

Talk sessions and on-site registration will take place on the first floor of [Wegmans Hall](https://www.rochester.edu/college/ecm/locations/wegmans.html) (Room 1400; <a href="https://maps.app.goo.gl/erMSWCyUjNKpYigv7">map</a>), and coffee breaks will take place on the first floor of [Goergen Hall](https://www.rochester.edu/college/ecm/locations/goergen.html) (Munnerlyn Atrium; <a href="https://maps.app.goo.gl/PvRXJY6xbWBgUyxR8">map</a>). On Wednesday evening (May 29), there will be a reception concurrent with the poster session, both in <a href="https://www.rochester.edu/college/rettnerhall/facilities/atrium.html">Rettner Hall</a> (Rettner Atrium; <a href="https://maps.app.goo.gl/koZ8dDNAnxJNfjjdA">map</a>).

<p>
  <b>NB:</b> This schedule is preliminary and subject to change. Abstracts will be made available in the near future.
</p>

{% assign lightning_bin = 0 %}
{% assign lightning_bin_str = "One" %}

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
          {% if author.website != null %}
          <a class="authorwebsite" href="{{ author.website }}">{{ author.name }}</a>
          {% else %}
          {{ author.name }}
          {% endif %}
          {% unless forloop.last %}<br/>{% endunless %}
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
          {% if author.website != null %}
          <a class="authorwebsite" href="{{ author.website }}">{{ author.name }}</a>
          {% else %}
          {{ author.name }}
          {% endif %}
          {% unless forloop.last %}<br/>{% endunless %}
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
        <span id="light{{ lightning_bin_str }}PosterArr" class="collapsed"></span>
        <a id="light{{ lightning_bin_str }}PosterSwitch" href="javascript:void(0)" onclick="lightning('posterInfoLight{{ lightning_bin_str }}', 'light{{ lightning_bin_str }}PosterArr')">{{ event.name }}</a>
      </td>
    </tr>
    {% for posterinfo in site.data.presentations.posters %}
      {% if lightning_bin == posterinfo[1].lightning_bin %}
      <tr class="posterInfoLight{{ lightning_bin_str }} hidden">
        <td class="time">&nbsp;</td>
        <td class="title">{{ posterinfo[1].title }}</td>
        <td class="authors">
        {% for authorid in posterinfo[1].authors %}
          {% assign author = site.data.people[authorid] %}
          {% if author.website != null %}
          <a class="authorwebsite" href="{{ author.website }}">{{ author.name }}</a>
          {% else %}
          {{ author.name }}
          {% endif %}
          {% unless forloop.last %}<br/>{% endunless %}
        {% endfor %}
        </td>
      </tr>
      {% endif %}
    {% endfor %}
    {% assign lightning_bin = 1 %}
    {% assign lightning_bin_str = "Two" %}
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