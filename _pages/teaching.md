---
layout: page
permalink: /academics/
title: teaching
description: A 
years: [2019]
nav: true
---

<div class="publications">

{% for y in page.years %}
  <h2 class="year">{{y}}</h2>
  {% bibliography -f papers -q @*[year={{y}}]* %}
{% endfor %}

</div>


<div class="teaching">

  <h2 class="year">2019</h2>
 <a href=https://www.coursicle.com/cmu/courses/STU/98357/> 98357: Introduction to Pakistan and its Culture </a>
</div>
