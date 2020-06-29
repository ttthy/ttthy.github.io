---
layout: photolist
title: Publications
menu: yes
order: 2
---
{% assign hashes = site.data.papers %}
{% capture years %}
{% for hash in hashes %}
{{ hash[0] }}
{% endfor %}
{% endcapture %}
{% assign sortedyears = years | split:' ' | sort | reverse %}

<div class="row">
<h1>Publications
    <a class="button" target="_blank" href="https://scholar.google.com/citations?user={{site.scholar_id}}">
        <i class="ai ai-google-scholar"></i>
    </a>
</h1>
</div>

<div class="row">
<h3>Conferences/Workshops </h3>
</div>
<div class="row">
{% for year in sortedyears %}
    <h4> {{year}} </h4>
    {% for paper in hashes[year] %}
        {% case paper.paper-type %}
            {% when "inproceedings" %}
                {% include paper.html paper=paper %}
        {% endcase %}
    {% endfor %}
{% endfor %}
</div>

<br/>

<div class="row">
<h3> Journals </h3>
</div>
<div class="row">
{% for year in sortedyears %}
    <h4> {{year}} </h4>
    {% for paper in hashes[year] %}
        {% case paper.paper-type %}
            {% when "article" %}
                {% include paper.html paper=paper %}
        {% endcase %}
    {% endfor %}
{% endfor %}
</div>
