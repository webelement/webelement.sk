---
title: Rečníci
desc: Ľudia, ktorí boli prednášať na WebElemente
layout: page
permalink: /recnici/
class: speakers
---

<div class="section page speakers">
<div class="container">


<h1>Rečníci</h1>
<p>
Vďaka patrí všetkým, ktorí boli prednášať! Info o rečníkoch je stiahnuté z ich Twitteru.
</p>

{% for speaker in site.data.speakers %}
<div class="speaker">

{% if speaker.image %}
    <img src="{{ speaker.image | prepend: site.baseurl }}" alt="{{ speaker.name }}" class="img-circle">
{% endif %}

<h2 id="{{ speaker._id }}">{{ speaker.name }}</h2>

{% if speaker.twitter %}
    <p>
        <a href="https://twitter.com/{{ speaker.twitter }}"
           title="{{ speaker.name }} - Twitter"
           target="_blank">@{{ speaker.twitter }}</a>
    </p>
{% endif %}

{% if speaker.about and speaker.about != '' %}
    <blockquote>{{ speaker.about }}</blockquote>
{% endif %}

<ul class="posts">
{% for event in speaker.events %}
    {% assign postUrl = event | split: 'webelement' | last | prepend: "/event/webelement" | append: "/" %}
    {% for post in site.posts %}
        {% if post.url == postUrl %}
            {% include event-list-item.html post=post %}
        {% endif %}
    {% endfor %}
{% endfor %}
</ul>

</div>
{% endfor %}

</div>
</div>