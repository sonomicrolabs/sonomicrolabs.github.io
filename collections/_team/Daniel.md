---
title: "Daniel Bergmann Sigtryggsson"
layout: team-member
header_transparent: true
date: 2023-06-19T13:44:30+10:00
weight: 2
meet: "placeholder"
description: "daniel description"
thumbnail: "/assets/images/team/daniel-thumbnail.jpg"
image: "/assets/images/team/daniel.jpg"
jobtitle: "daniel jobtitle"
links:
  - url: "https://www.linkedin.com/in/danielbergmann1/"
    label: LinkedIn
    icon: "fab fa-linkedin"
  - #url: "https://www.linkedin.com/in/danielbergmann1/"
    #label: Github
    #icon: "fab fa-github"
lang: en
hero:
  enabled: true
  heading: "Meet the Team"
  sub_heading: ""
  text_color: "#FFFFFF"
  background_color: ""
  background_gradient: true
  background_image: false
  background_image_blend_mode: overlay # "overlay", "multiply", "screen"
  fullscreen_mobile: false
  fullscreen_desktop: false
  height: "330px"
  buttons:
    enabled: true
    list:
      - text: "Contact Us"
        url: "/contact"
        external: false
        fa_icon: false
        size: large
        outline: true
        style: "light"

grid:
  collection: "team"
  sort_by: "weight" # "date", "weight"
  columns: 3
  prevent_click: false

---
{% tf _collections/team/Daniel.md %}