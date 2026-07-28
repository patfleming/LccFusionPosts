---
title: "Fusion Hardware Architecture Overview"
excerpt: "A high-level walkthrough of Fusion’s tiered hardware architecture, open-source philosophy, and the modular design that makes expansion easy."

content_type: podcast
series: "LCC Fusion Podcast"

date: 2025-11-22

categories: Podcasts
tags: [architecture, node-card, system-design]

gallery:
  - url: /assets/podcasts/images/posters/LCC_Fusion_Hardware_.jpg
    image_path: /assets/podcasts/images/posters/LCC_Fusion_Hardware_.jpg
    alt: "Breakout Boards"
    title: "Breakout Boards"
---

{% include gallery layout="third" caption="LCC Fusion Hardware Architecture Overview" %}

In this LCC Fusion podcast episode, Nelson and Harrison step back from individual cards and devices and look at the **big picture**:  
how Fusion’s open-source design, tiered hardware architecture, and modular bus system come together to form a flexible, educational, and expandable platform for layout control.  
:contentReference[oaicite:1]{index=1}

This episode explains **why Fusion was created**, **how the architecture works**, and **why the system grows cleanly without rewiring or redesign**.

---

## Watch the Podcast

- [Fusion Hardware Architecture Overview (video, 10 min)](https://youtu.be/N_5GHJlMC6Q){:target="_blank" rel="noopener"}

{% include ai_notice.html %}

---

## Why Fusion Was Created

The episode opens with a key question from Nelson:  
*“Why make all of this open-source? Why not just build a commercial product?”*

Harrison explains that Fusion was built for:

- **education**  
- **DIY electronics**  
- **STEM-style learning inside the model railroad hobby**  
- and for hobbyists who want to **understand** the electronics running their layout

All schematics, PCB files, and firmware are public.  
Anyone can study it, build it, or even design new cards.  
Fusion’s open-design philosophy is fundamental — not optional.

---

## The Fusion Architecture: A Three-Tier Model

The podcast breaks the system into three clear tiers:

### 🧠 **Tier 1 — The Node Card**  
The processor.  
Runs logic, talks CAN, and defines the *type* of node.  
Fusion already has **three different Node boards**, each based on a different ESP32 family.

### ⚙️ **Tier 2 — The I/O Cards**  
Function-specific cards that do the actual work:  
Turnouts, Signals, Detection, Audio, Sensors, PWM, etc.  
More than **10 different I/O cards** already exist.

### 🔌 **Tier 3 — Breakout Boards + Devices**  
The bridge to the real world.  
Breakouts adapt the I/O card signals to motors, LEDs, coils, servos, and sensors.  
A single card often supports **multiple breakout boards** — for example, the Turnout Card works with stall motors, servos, twin-coil machines, and relay-driven systems.

Nelson summarizes it perfectly:  
**“Brains → Function → Devices.”**

---

## Fusion Busses: Simple and Purpose-Built

The podcast also takes time to explain the three busses that make Fusion clean and scalable:

- **CAN Bus** — connects nodes across the layout  
- **Node Bus** — the backplane that connects a Node to all cards in its cluster  
- **COMM Bus (I²C)** — short-range communication used inside the cluster  

Harrison explains how these three busses each have one job, keeping the architecture clean and avoiding interference between layers.

---

## Modeled After Desktop Computer Architecture

Fusion’s hardware design draws directly from 30+ years of PC architecture:

- standard card form factors  
- a consistent backplane (like ATX)  
- plug-in I/O cards (like PCI/PCIe)  
- breakouts acting like purpose-specific adapters  

This keeps the system:

- predictable  
- expandable  
- easy to extend with new hardware

Just like building a computer.

---

## Why Tiers Matter

Nelson asks a key question:  
*“Why bother with separate tiers? Why not one big board?”*

The answer:  
**tiers keep Fusion expandable**.

You can create:

- a new Node Card  
- a new I/O Card  
- a new breakout board  

…and **everything still works** without changing the Node, Hub, or wiring model.

Fusion grows **horizontally** — not in complexity.

---

## Work in Progress (Pre-GA)

While the architecture is complete, the project is still in active development:

- new revisions of Node Cards  
- new I/O cards and breakout boards  
- firmware improvements  
- documentation being expanded  
- not yet GA — early-access for builders and contributors

The open-source model means the community shapes the system as it grows.

---

## Summary

This episode provides a wide-angle view of how Fusion fits together:

- Open-source at every level  
- A clean, three-tier architecture  
- A simple and intentional bus structure  
- Standardized card form factors  
- Breakout boards that simplify wiring  
- A platform designed for **learning**, **building**, and **future expansion**  

Fusion’s architecture is built to last — and built to grow.

---

## Downloads and Documentation

- **Full LCC Fusion Documentation:**  https://patfleming.github.io/LccFusionProject/
  
- **GitHub Repository:**  https://github.com/patfleming/LccFusionProject
  
- **LCC Fusion Podcasts Playlist:** https://www.youtube.com/playlist?list=PLg49NFDgDCLRS7j30iTitaWUlfIdiw0Wx
  
- [Download presentation with speaker notes (PPT)](https://raw.githubusercontent.com/patfleming/LccFusionPosts/main/podcasts/getting-started-series/hardware-architecture/src/LCC_Fusion_Hardware_Architecture_Overview.pptx) 
