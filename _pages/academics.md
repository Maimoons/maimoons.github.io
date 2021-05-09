---
layout: page
permalink: /academics/
title: academics
description: Little undergraduate teaching and academic experiences
years: [2020]
nav: true
---

<hr> 

<div class="publications"> 
  <h2>publication</h2>
    {% for y in page.years %}
      <h2 class="year">{{y}}</h2>
     {% bibliography -f papers -q @*[year={{y}}]* %}
     {% endfor %}
</div>



<div class="teaching">
  <h2>teaching</h2>
      <h2 class="year">2019</h2>
      <a href="https://www.coursicle.com/cmu/courses/STU/98357/"> 98357: Introduction to Pakistan and its Culture </a>
</div>
