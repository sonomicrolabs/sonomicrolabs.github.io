---
layout: home
permalink: /
permalink_en: /
title: "SonoMicro"
description: "Connect your factory to accurate, real-time water flow data with our non-invasive flow measurement service."
header_transparent: true
meta_title: SonoMicro
lang: en

hero:
  enabled: true
  heading: "We Empower Your Water Sustainability Journey"
  # NOTE: this string is a match key, not displayed text — see _includes/framework/blocks/sections/hero.html.
  # The real heading is _i18n/en.yml and _i18n/is.yml's home.hero.heading.
  sub_heading: "Unlock Data-Driven Water Management with Our Non-Invasive Flow Metering Solutions."
  # NOTE: match key too — real text is home.hero.sub_heading in _i18n/en.yml / _i18n/is.yml.
  text_color: "#FFFFFF"
  background_color: "#1d2830"
  background_gradient: true
  background_image: "/assets/images/gen/home/home-1-large.webp"
  background_image_blend_mode: overlay # "overlay", "multiply", "screen"
  fullscreen_mobile: true
  fullscreen_desktop: false
  height: "660px"
  buttons:
    enabled: true
    list:
      - text: "Request Quote"
        #text: {% t hodme.hero.button1 %}
        #text: "Request Quote"
        url: "/contact"
        external: false
        fa_icon: false
        size: large # "small", "normal", "large"
        outline: false
        style: "light" # "light", "dark", "primary"
      - text: "Contact Us"
        url: "/contact"
        external: false
        fa_icon: false
        size: large
        outline: false
        style: "light"

services:
  enabled: true
  sub_heading: ""
  heading: "Our Services"
  limit: 3
  sort: "weight" # 'date'
  view_more_button_text: "View All Services"
  view_more_button_link: "/services"
  prevent_click: false

intro:
  enabled: true
  align: left
  image: "/assets/images/gen/content/drop-data.webp"
  heading: "intro"
  sub_heading: "intro sub heading"
  features:
    # NOTE: these `text` values are unused — _includes/framework/blocks/sections/info.html
    # hardcodes this list to home.intro.features.first_feature..fifth_feature in
    # _i18n/en.yml / _i18n/is.yml instead of reading feature.text. Edit those, not here.
    enabled: true
    list:
      - text: "No process interruption nor downtime needed and runs without affecting flow pressure."
        fa_icon: "fas fa-check"  
      - text: "Autonomous, real-time measurements of water flow for efficient water consumption monitoring, helping you meet CSRD regulatory requirements."
        fa_icon: "fas fa-check"
      - text: "Seamless integration and user-friendly interface for easy implementation and data visualization."
        fa_icon: "fas fa-check"
      - text: "Tailored recommendations for optimizing water usage and reducing waste, contributing to a sustainable future."
        fa_icon: "fas fa-check"
      - text: "Cost-effective access to comprehensive hardware and software solutions, meeting budget constraints and enabling organizations of all sizes to embrace sustainable practices."
        fa_icon: "fas fa-check"
  buttons:
    enabled: true
    list:
      - text: "About Us"
        url: "/about"
        external: false
        fa_icon: ""
        size: large
        outline: true
        style: "primary"

partners:
  enabled: false
  limit: 5
  sort: "weight" # 'date'

projects:
  enabled: false
  heading: "Our Projects"
  sub_heading: ""
  limit: 2
  columns: 2
  sort: "weight" # 'date'
  view_more_button_text: "View All Projects"
  view_more_button_link: "/projects"
  prevent_click: false

outro:
  enabled: false
  align: center
  image: false
  heading: Get Started Today
  sub_heading: "Save time and money on your digital yourney."
  features:
    enabled: true
    list:
      - text: "Free Quote"
        fa_icon: "fas fa-envelope-open-text"
  buttons:
    enabled: true
    list:
      - text: "Contact Us"
        url: "/contact"
        external: true
        size: "large"

posts:
  enabled: true
  heading: "Latest Posts"
  sub_heading: ""
  limit: 3
  columns: 3
  sort:  'date' # "weight" # 'date'
  view_more_button_text: "View All Posts"
  view_more_button_link: "/blog"
  prevent_click: false
---
{% tf _home_/home.md %}