---
title: Projects - Nishant Iyer
display: Projects
description: List of projects I've made
plum: false
wrapperClass: 'text-center'
projects:
  Current Focus:
    - name: 'Lubera'
      link: 'https://lubera.digital'
      desc: 'Developing thin client for remote digital health delivery'

  Cybersecurity:
    - name: 'AI-based POC of Careless Whisper Exploit'
      link: 'https://nishantiyerml-cw-rtt-analyzer.hf.space'
      desc: 'An AI-powered cybersecurity proof of concept of the Careless Whisper Exploit, this Space analyzes RTT delivery-receipt traces to infer likely device states, user activity patterns, companion session behavior, and platform fingerprints. It combines multiple ML models, behavioral heuristics, and rich visual analytics to turn low-level timing data into interpretable insights for security research'

    - name: 'CVE-2020-15215-Discord-POC'
      link: 'https://github.com/NishantIyer/CVE-2020-15215-Discord-POC'
      desc: 'This project is a proof-of-concept focused on Electron security, based on the 2020 vulnerability chain involving CVE-2020-15215 and CVE-2020-15174. It then applies those conditions in a practical PoC implementation modeled after Discord’s desktop architecture, exploring how renderer–main boundaries, preload bridges, IPC channels, and navigation controls can be misconfigured and abused. The goal is to simulate these edge cases in a controlled environment and better understand how to secure Electron apps against similar issues.'

    - name: 'Vuln Disclosure - Scaler - Critical Credential Exposure'
      link: 'https://disclosurereport-2-2.tiiny.site/'
      desc: 'Identified a critical Firebase authentication misconfiguration on Scaler’s SST platform where an admin custom token was exposed client-side, reproduced impact via signInWithCustomToken, and escalated findings to management and engineering teams. Received acknowledgement and vulnerability was fixed.'

  Cloud:
    - name: 'NoVNC Ubuntu Persistent on GCP'
      link: 'https://github.com/NishantIyer/ubuntu-xfce-web-'
      desc: "Ubuntu on the web"
    - name: 'Aliyun Terraform'
      link: 'https://github.com/NishantIyer/aliyunterraform'
      desc: "Terraform module for creating AnalyticDB for PostgreSQL on Alibaba Cloud."
    - name: 'Alibaba CFC Blockchain Application'
      link: 'https://github.com/NishantIyer/Aliyun-FC-Blockchain'
      desc: "Blockchain Application on Alibaba Cloud Function Compute"
    - name: 'Aliyun ECS Plugin'
      link: 'https://github.com/NishantIyer/aliyun-ecs-plugin'
      desc: "aliyun ecs plugin"
    - name: 'Azure Migrator to Oracle'
      link: 'https://github.com/NishantIyer/AzureMigrater'
      desc: "Migration from Azure to Oracle made hasslefree!"

  Web Apps:
    - name: 'Beatville'
      link: 'https://beatville.vercel.app'
      desc: "A decentralized and blazing fast privacy respecting alternative to Spotify and Youtube"
    - name: 'Multiplayer Chess'
      link: 'https://full-fledged-chess-web-app.nishant2609.repl.co'
      desc: "A full fledged chess app with chat functionality."

  Bots:
    - name: 'Proxima'
      link: 'https://discord.com/api/oauth2/authorize?client_id=947363163081412681&permissions=8&scope=bot'
      desc: "A 1000+ command discord bot, quite advanced and has everything you can imagine. Sadly, it never gained traction but was quite a hit among my friends"
    - name: 'Hymn'
      link: 'https://discord.com/api/oauth2/authorize?client_id=945667542997954590&permissions=8&scope=bot'
      desc: "A music playing bot :)"
    - name: 'Proxie'
      link: 'https://github.com/NishantIyer/proxie'
      desc: "A transformer/nueral model based voice assistant."

  Networking:
    - name: 'ESPFA'
      link: 'https://github.com/NishantIyer/espfa'
      desc: "ESP32 Port Forwarding Accelerator"
    - name: 'Unified Threat Management'
      link: 'https://utm-interface.netlify.app'
      desc: "An aio security management device made out of esp32."
---

<!-- @layout-full-width -->

<ListProjects :projects="frontmatter.projects" />
