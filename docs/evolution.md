---
layout: page
title: Evolution
permalink: /Evolution/
custom_js: evolution.js
custom_css: evolution.css
---

<h1 class="page-title">{{ page.title | escape }}</h1>

<div class="section row">
    <div class="col s12" id="apps_evolution">
    </div>
</div>    
<div class="divider"></div>

{% assign current =  site.versions | last %}
{% for version in site.versions reversed%}
    {% if current.label == version.label %}
<h5>{{ version.label }}<span class="new badge" data-badge-caption="Current Version"></span></h5>
<div class="row">
    {% endif %}

    {% if current.label != version.label %}
<h5>{{ version.label }}</h5>
<div class="row">   
        {% endif %}
    <div class="col s12">

           <ul class="version" id="{{ version.label }}">
            <li>Number of applications: <em class="n_apps">{{ version.number_of_apps }}</em></li>
            {% if version.loc %}
                <li>Number of Lines of Code: <em>{{ version.loc }}</em></li>
            {% endif %}
            {% if version.total_pure_kotlin %}
                <li>Number of pure Kotlin apps:<em>{{ version.total_pure_kotlin }}</em></li>
            {% endif %}
            <li>Release date: <em class="release_date">{{ version.date | date: "%b %d,  %Y"}}</em></li>
            <li><a class="right" href="{{ version.url | relative_url }}"> More details</a></li>
           </ul>
         </div>
</div>

<div class="divider"></div>
{% endfor %}

