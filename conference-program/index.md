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

All talks and posters at SALT35 will take place in the Science Center at 1 Oxford Street, just outside Harvard Yard. The conference dinner on May 21st will be held at the Cambridge Queen's Head Pub right across the road from the Science Center.

ASL interpretation will be available for all presentations. For any questions related to ASL interpreting, please contact our ASL coordinator Stetson Stanger (<span style="font-family: monospace">[stetsonstanger@fas.harvard.edu](mailto:stetsonstanger@fas.harvard.edu)</span>).  

<p>
  <b>NB:</b> This schedule is preliminary and subject to change.
</p>

{% assign lightning_bin = 0 %}
{% assign lightning_bin_str = "One" %}

{% for day in site.data.program %}

<h2 id="{{ day.day }}">{{ day.date }}</h2>

<table class="program">
  <tbody>
    {% for event in day.events %}
    {% if event.type == "talk_session" %}
      {% assign chair = site.data.people[event.chairid] %}
      <tr class="talkChairinfo">
        <td colspan="3">
          {{ event.name }} // chair: <a href="{{ chair.website }}" class="chairName">{{ chair.name }}</a>
        </td>
      </tr>
      {% for talk in event.subevents %}
        {% assign talkinfo = site.data.presentations.talks[talk.talkid] %}
        <tr class="talk">
          <td class="time">{{ talk.time }}</td>
          <td class="title">
            {% if talkinfo.abstract_formats contains "md" %}
              <a href="/salt34/abstracts/{{ talk.talkid }}.html">{{ talkinfo.title }}</a>
            {% elsif talkinfo.abstract_formats contains "pdf" %}
              <a href="/salt34/abstracts/{{ talk.talkid }}.pdf">{{ talkinfo.title }}</a>
            {% else %}
              {{ talkinfo.title }}
            {% endif %}
            {% if talkinfo.materials_format != null %}
              [<a href="{{ site.baseurl }}/presentation-materials/{{ talk.talkid }}.{{ talkinfo.materials_format }}">{{ talkinfo.materials_type }}</a>]
            {% endif %}
          </td>
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
    {% elsif event.type == "welcome" %}
    {% assign chair = site.data.people[event.chairid] %}
    <tr>
      <td class="time">{{ event.time }}</td>
      <td class="title" colspan="2">{{ event.name }} by <a href="{{ chair.website }}">{{ chair.name }}</a></td>
    </tr>
    {% elsif event.type == "keynote" %}
    {% assign talkinfo = site.data.presentations.keynotes[event.talkid] %}
    {% assign chair = site.data.people[event.chairid] %}
    <tr class="invitedChairinfo"><td colspan="3">Invited Talk // chair: <a href="{{ chair.website }}" class="chairName">{{ chair.name }}</a></td></tr>
    <tr class="invited">
      <td class="time">{{ event.time }}</td>
      <td class="title">
      {% if talkinfo.abstract_formats contains "md" %}
      <a href="/salt34/abstracts/{{ event.talkid }}.html">{{ talkinfo.title }}</a>
      {% elsif talkinfo.abstract_formats contains "pdf" %}
      <a href="/salt34/abstracts/{{ event.talkid }}.pdf">{{ talkinfo.title }}</a>
      {% else %}
      {{ talkinfo.title }}
      {% endif %}
      {% if talkinfo.materials_format != null %}
        [<a href="{{ site.baseurl }}/presentation-materials/{{ event.talkid }}.{{ talkinfo.materials_format }}">{{ talkinfo.materials_type }}</a>]
      {% endif %}
      </td>
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
    {% assign chair = site.data.people[event.chairid] %}
    <tr class="posterChairinfo"><td colspan="3">SALTED Workshop // chair: <a href="{{ chair.website }}" class="chairName">{{ chair.name }}</a></td></tr>
    <tr class="poster">
      <td class="time">{{ event.time }}</td>
      <td class="title" colspan="2"><a href="{{ site.baseurl }}/salted/">{{ event.name }}</a></td>
    </tr>
    {% elsif event.type == "lightning" %}
    {% assign chair = site.data.people[event.chairid] %}
    <tr class="posterChairinfo"><td colspan="3">Lightning Talk Session // chair: <a href="{{ chair.website }}" class="chairName">{{ chair.name }}</a></td></tr>
    <tr class="postertalk">
      <td class="time">{{ event.time }}</td>
      <td class="title" colspan="2">
        <span id="light{{ lightning_bin_str }}PosterArr" class="collapsed"></span>
        <a id="light{{ lightning_bin_str }}PosterSwitch" href="javascript:void(0)" onclick="lightning('posterInfoLight{{ lightning_bin_str }}', 'light{{ lightning_bin_str }}PosterArr')">{{ event.name }}</a>
      </td>
    </tr>
    {% for posterinfo in site.data.presentations.posters %}
      {% if lightning_bin == posterinfo[1].lightning_bin %}
      <tr class="posterInfoLight{{ lightning_bin_str }}">
        <td class="time">&nbsp;</td>
        <td class="title">
        {% if posterinfo[1].abstract_formats contains "md" %}
        <a href="/salt34/abstracts/{{ posterinfo[0] }}.html">{{ posterinfo[1].title }}</a>
        {% elsif posterinfo[1].abstract_formats contains "pdf" %}
        <a href="/salt34/abstracts/{{ posterinfo[0] }}.pdf">{{ posterinfo[1].title }}</a>
        {% else %}
        {{ posterinfo[1].title }}
        {% endif %}
        {% if posterinfo[1].materials_format != null %}
          [<a href="{{ site.baseurl }}/presentation-materials/{{ posterinfo[0] }}.{{ posterinfo[1].materials_format }}">poster</a>]
        {% endif %}
        </td>
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
      <td class="title" colspan="2">{{ event.name }}</td>
      <td></td>
    </tr>
    {% endif %}
    {% endfor %}
  </tbody>
</table>

{% endfor %}


<!---
<embed src="https://saltconf.github.io/salt35/assets/schedule.pdf" width="500" height="700" type="application/pdf" />

 --->
