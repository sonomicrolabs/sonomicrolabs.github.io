---
layout: list
title: Services
description: "A selection of our digital services"
permalink: /services/
permalink_en: /services/
header_transparent: true
lang: en

hero:
  enabled: true
  heading: "Services"
  sub_heading: "We offer comprehensive, connected flow measurement solutions for factories."
  text_color: "#FFFFFF"
  background_color: false
  background_gradient: true
  background_image: "/assets/images/gen/home/home-8-large.webp"
  background_image_blend_mode: overlay # "overlay", "multiply", "screen"
  fullscreen_mobile: false
  fullscreen_desktop: false
  height: "500px"
  buttons:
    enabled: false
    list:
      - text: "Contact Us"
        url: "/contact"
        external: false
        fa_icon: false
        size: large
        outline: true
        style: "light"

grid:
  collection: "services"
  sort_by: "weight" # "date", "weight"
  columns: 3
  prevent_click: false

intro:
  enabled: true
  align: left
  image: false
  heading: "Advanced Flow Measurement for Connected Factories."
  sub_heading: "Our hardware and digital platform provide actionable data to optimize water use and identify loss, and our team provides consultations to help your facility get the most out of its flow data while adhering to budget constraints."
  buttons:
    enabled: false
    list:
      - text: "About Us"
        url: "/about/"
        external: false
        fa_icon: false
        size: normal

outro:
  enabled: true
  align: left
  image: false
  heading: "Ready to get started?"
  sub_heading: "Contact us today for a free quote!"
  buttons:
    enabled: true
    list:
      - text: "Get In Touch."
        url: "/contact"
        external: false
        fa_icon: false
        size: normal
---
{% tf _services_/services.md %}