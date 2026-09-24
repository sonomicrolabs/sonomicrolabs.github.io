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
  sub_heading: "We offer a comprehensive, sustainable water management solutions."
  # NOTE: match key, not displayed text — see _includes/framework/blocks/sections/hero.html.
  # The real sub_heading is services.hero.sub_heading in _i18n/en.yml / _i18n/is.yml.
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
  # NOTE: heading/sub_heading below are currently NOT rendered on this page — info.html
  # (_includes/framework/blocks/sections/info.html) only has match conditions for a few
  # other pages' literal heading/sub_heading strings, none of which match this page's.
  # Pre-existing gap, not introduced here; left with correct copy in case it's wired up.
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