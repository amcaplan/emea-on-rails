---
layout: home
---

<div class="content" markdown=1>

# What is EMEA on Rails?
{: .title}
The conference experience, minus the jetlag! Join us online on June 9, 2021
{: .subtitle .has-text-weight-normal}

There are so many Rubyists in Europe, the Middle East, and Africa, but we haven't managed to gather much in the past year, and we could definitely learn a lot from each other. Let's get together (virtually for now) and experience some of the excitement of an international conference (remember those?), without jetlag or timezone challenges!

Our first event will be a meetup-of-meetups featuring EMEA speakers from this past RailsConf and recent EMEA conferences. Keep scrolling to find out [which meetups are participating](#participating-meetups) and [who our speakers are](#speakers).

You can also:

* [Register your meetup](https://forms.gle/s44Z78KySXYurX27A)
* [Follow us on Twitter](https://twitter.com/emeaonrails) for updates
* <a href="https://lu.ma/event/evt-zcbXUT9G4Y1sVBd" data-luma-action="checkout" data-luma-event-id="evt-zcbXUT9G4Y1sVBd">Sign up for the event!</a> <a href="https://lu.ma/event/evt-zcbXUT9G4Y1sVBd">(accessible link)</a>

## The Technical Details

We'll meet on the evening of June 9, at 15:00 UTC<span class="is-hidden is-parenthesized has-pre-space has-zone local-time" data-time="2021-06-09T15:00:00Z"></span>, via SignalWire (link to be provided). You can view the [schedule](#schedule) below.

We will also have exciting contests and prizes for all our participants across the region!

</div>

{% render "signup_button" %}

----
{: .my-6}

# Participating Meetups
{: .mb-5 .title .has-text-centered #participating-meetups}

<div class="columns is-mobile is-multiline is-justify-content-center">
{% assign alphabetized-meetups = site.data.meetups | sort: "name" %}
{% for meetup in alphabetized-meetups %}
  <div class="column is-half-mobile is-one-third-tablet is-one-quarter-desktop">
    <a href="{{meetup.homepage}}" target="_blank">
      <figure class="image is-2by1">
        <img src="https://res.cloudinary.com/caplan/image/upload/w_400,h_200,c_pad,f_auto,q_auto/v1/emea-on-rails-2021/meetups/{{meetup.logo}}-logo.jpg" alt="{{meetup.name}}" />
      </figure>
    </a>
  </div>
{% endfor %}
</div>

----
{: .my-6}

# Speakers
{: .mb-5 .title .has-text-centered #speakers}

<div class="columns is-multiline is-justify-content-center">
{% assign alphabetized-speakers = site.data.speakers | sort: "name" %}
{% for speaker in alphabetized-speakers %}
  {% assign abstract-paragraphs = speaker.abstract | newline_to_br | split: '<br />' %}
  <div class="column is-one-third-tablet" id="speaker-{{ speaker.name | downcase | replace: ' ', '-' }}-card">
    <div class="card">
      <div class="card-image">
        <figure class="image is-1by1">
          <img src="https://res.cloudinary.com/caplan/image/{% if speaker.avatar %}upload{% else %}twitter_name{% endif %}/w_400,h_400,c_fill,f_auto,q_auto/{% if speaker.avatar %}emea-on-rails-2021/speakers/{{speaker.avatar}}{% else %}{{speaker.twitter}}{% endif %}.jpg" alt="Profile of {{speaker.name}}" />
        </figure>
      </div>
      <div class="card-content">
        <div class="media">
          <div class="media-content">
            <a href="https://twitter.com/{{ speaker.twitter }}" target="_blank">
              <h4 class="title is-4">{{ speaker.name }}</h4>
            </a>
            <p class="subtitle is-6 is-italic min-2-line-height-mobile">{{ speaker.title }}</p>
          </div>
        </div>

        <div class="content clamp-6-lines">
          {% for paragraph in abstract-paragraphs %}{{ paragraph }}<br/><br/>{% endfor %}
        </div>
      </div>
      <div class="card-footer">
        {% capture modal-id %}speaker-modal-{{ forloop.index }}{% endcapture %}
        <a href="#{{ modal-id }}" class="card-footer-item speaker-read-more" data-modal-id="{{ modal-id }}">Read More</a>
        <div class="modal" id="{{ modal-id }}">
          <div class="modal-background" onclick="javascript:document.getElementById('{{ modal-id }}').classList.remove('is-active');"></div>
          <div class="modal-card">
            <header class="modal-card-head">
              <h3 class="modal-card-title">{{ speaker.name }}</h3>
              <button class="delete" aria-label="close" onclick="javascript:document.getElementById('{{ modal-id }}').classList.remove('is-active');"></button>
            </header>
            <section class="modal-card-body">
              <div class="content">
                <h2>{{ speaker.title }}</h2>
                {% for paragraph in abstract-paragraphs %}<p>{{ paragraph }}</p>{% endfor %}
              </div>
              <article class="message">
                <div class="message-header">
                  <p>Bio</p>
                </div>
                <div class="message-body content">
                  {{ speaker.bio | markdownify }}
                </div>
              </article>
            </section>
          </div>
        </div>
      </div>
    </div>
  </div>
{% endfor %}
</div>

----
{: .my-6}

# Schedule
{: .mb-5 .title .has-text-centered #schedule}

<div id="time-display-toggle" class="tabs is-toggle is-toggle-rounded">
  <ul>
    <li class="is-active" data-time="utc">
      <a class="button">
        <span>UTC</span>
      </a>
    </li>
    <li data-time="local">
      <a class="button">
        <span>Local Time<span class="is-hidden is-parenthesized has-pre-space only-zone local-time" data-time="2021-06-09T15:00:00Z"></span></span>
      </a>
    </li>
  </ul>
</div>

<div class="table-container">
  <table id="schedule-table" class="table is-striped is-fullwidth">
    <thead>
      <th>Time</th>
      {% for track in site.data.tracks %}
        <th>{{ track.name }}</th>
      {% endfor %}
    </thead>
    <tbody>
      {% render "joint_session", time: "14:00", title: "Pre-Event Hangout Hour" %}
      {% render "joint_session", time: "15:00", title: "Welcome and Opening Remarks" %}
      {% render "speakers_slot", speakers: site.data.speakers, tracks: site.data.tracks, time: "15:05" %}
      {% render "joint_session", time: "15:55", title: "Break" %}
      {% render "joint_session", time: "16:00", title: "🏆 Ruby Trivia Quiz 1 🏆", joinLink: true %}
      {% render "speakers_slot", speakers: site.data.speakers, tracks: site.data.tracks, time: "16:10" %}
      {% render "joint_session", time: "16:40", title: "Break" %}
      {% render "joint_session", time: "16:45", title: "Meetup Breakout Sessions" %}
      {% render "joint_session", time: "17:10", title: "Break" %}
      {% render "joint_session", time: "17:15", title: "🏆 Ruby Trivia Quiz 2 🏆", joinLink: true %}
      {% render "speakers_slot", speakers: site.data.speakers, tracks: site.data.tracks, time: "17:25" %}
      {% render "joint_session", time: "18:10", title: "Closing Remarks and Post-Event Hangout Hour" %}
    </tbody>
  </table>
</div>
{% render "signup_button" %}

----
{: .my-6}

# Thanks to our Supporters!
{: .mb-5 .title .has-text-centered #supporters}

<div class="columns is-mobile is-multiline is-justify-content-center">
{% assign alphabetized-supporters = site.data.supporters | sort: "name" %}
{% for supporter in alphabetized-supporters %}
  <div class="column is-half-mobile is-one-third-tablet is-one-quarter-desktop">
    <a href="{{supporter.homepage}}" target="_blank">
      <figure class="image is-2by1">
        <img src="https://res.cloudinary.com/caplan/image/upload/w_400,h_200,c_pad,f_auto,q_auto/v1/emea-on-rails-2021/supporters/{{supporter.logo}}-logo.jpg" alt="{{supporter.name}}" />
      </figure>
    </a>
  </div>
{% endfor %}
</div>

----
{: .my-6}

# Organized By:
{: .mb-5 .title .has-text-centered #organizers}

<div class="columns is-mobile is-multiline is-justify-content-center">
{% assign alphabetized-organizers = site.data.organizers | sort: "name" %}
{% for organizer in alphabetized-organizers %}
  <div class="column is-2-desktop is-3-tablet is-6-mobile is-flex" style="justify-content: center;">
     <a href="{% if speaker.link %}{{ speaker.link }}{% else %}https://twitter.com/{{ speaker.twitter }}{% endif %}" target="_blank">
      <figure class="image is-128x128">
          <img src="https://res.cloudinary.com/caplan/image/{% if organizer.avatar %}upload{% else %}twitter_name{% endif %}/w_256,h_256,c_fill,r_max,f_auto,q_auto/{% if organizer.avatar %}emea-on-rails-2021/organizers/{{organizer.avatar}}{% else %}{{organizer.twitter}}{% endif %}.jpg" alt="Profile of {{organizer.name}}" />
      </figure>
      <div class="has-text-centered has-text-weight-semibold is-size-5">
        {{ organizer.name }}
      </div>
    </a>
  </div>
{% endfor %}
</div>

<script id="luma-checkout" src="https://embed.lu.ma/checkout-button.js"></script>
<script type="text/javascript">
  var forEach = Array.prototype.forEach;

  document.body.addEventListener("keyup", function(e) {
    if (e.keyCode !== 27) return;
    var modal = document.getElementsByClassName("modal is-active")[0];
    if (modal) modal.classList.remove('is-active');
  });

  forEach.call(document.querySelectorAll(".speaker-schedule-listing a.talk-modal-link"), function(el) {
    el.addEventListener("click", function(e) {
      if (!el.dataset.speakerSlug) return;
      e.preventDefault();
      var modalId = document.querySelector("#speaker-" + el.dataset.speakerSlug + "-card .card-footer a.speaker-read-more").dataset.modalId;
      document.getElementById(modalId).classList.add('is-active');
    });
  });

  forEach.call(document.getElementsByClassName("speaker-read-more"), function(el) {
    el.addEventListener("click", function(e) {
      e.preventDefault();
      document.getElementById(el.dataset.modalId).classList.add('is-active');
    });
  });

  forEach.call(document.getElementsByClassName('local-time'), function(el) {
    var time = (new Date(Date.parse(el.dataset.time))).toLocaleTimeString('en-us',{timeZoneName:'short', hour12: false}).replace(/:\d\d /, ' ');
    if (el.classList.contains("only-zone")) {
      time = time.split(' ')[1];
    } else if (!el.classList.contains("has-zone")) {
      time = time.split(' ')[0];
    }
    if (el.classList.contains("is-parenthesized")) time = "(" + time + ")";
    if (el.classList.contains("has-pre-space")) time = " " + time;
    el.innerHTML = time;
    el.classList.remove('is-hidden');
  });

  var timeToggles = document.body.querySelectorAll("#time-display-toggle li");
  forEach.call(timeToggles, function(el) {
    el.addEventListener("click", function(e) {
      forEach.call(timeToggles, function(el) { el.classList.remove('is-active'); });
      el.classList.add('is-active');
      if (el.dataset.time == "utc") {
        forEach.call(document.body.querySelectorAll("#schedule-table .utc-time"), function(el) {
          el.classList.remove("is-hidden");
        });
        forEach.call(document.body.querySelectorAll("#schedule-table .local-time"), function(el) {
          el.classList.add("is-hidden");
        });
      } else {
        forEach.call(document.body.querySelectorAll("#schedule-table .local-time"), function(el) {
          el.classList.remove("is-hidden");
        });
        forEach.call(document.body.querySelectorAll("#schedule-table .utc-time"), function(el) {
          el.classList.add("is-hidden");
        });
      }
    });
  });
  document.body.querySelector("#time-display-toggle li[data-time=local]").click()

  var showCurrentLinks = function() {
    document.querySelectorAll('.outlink.is-hidden').forEach(function(link) {
      if (new Date() > Date.parse(link.dataset.hideUntil)) link.classList.remove('is-hidden');
    });
  }
  setInterval(showCurrentLinks, 3000);
  showCurrentLinks();
</script>
