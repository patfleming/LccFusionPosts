---
title: "LCC Fusion Podcast – BOD Card & Breakout Board"
excerpt: "Train detection with the Block Occupancy Detection (BOD) Card and its Breakout Board"

date: 2025-11-21

categories: [LCC Fusion Project, Podcast]
tags: [podcasts, detection, bod]

gallery:
  - url: /assets/podcasts/images/posters/BOD_Breakout_Board.jpg
    image_path: /assets/podcasts/images/posters/Block_Breakout_Board.jpg
    alt: "Block Breakout Board Podcast Presentation"
    title: "Block Breakout Board"

  - url: /assets/podcasts/images/posters/BOD_Card.jpg
    image_path: /assets/podcasts/images/posters/BOD_Card.jpg
    alt: "BOD Card Podcast Presentation"
    title: "BOD Card"
---

{% include gallery layout="third" caption="LCC Fusion BOD Card & Block Breakout Board" %}

In this LCC Fusion podcast episode, Nelson and Harrison explore **how train detection works** using the **BOD Card** and the **Block Breakout Board**.  
These two boards work together to deliver **accurate**, **modular**, and **layout-friendly** block detection with minimal wiring.

---

## Watch the Podcasts

- [BOD Card Overview (video, 24 min)](https://youtu.be/NZ0R7zkpjbk){:target="_blank" rel="noopener"}
  
- [Block Breakout Board Overview (video, 17 min)](https://youtu.be/APAasm0nT_o){:target="_blank" rel="noopener"}


{% include ai_notice.html %}

---

## What these episodes cover

### 🚦 **Understanding Block Occupancy Detection**

- What “block detection” means in an LCC Fusion layout
- Why Fusion uses *current-sensing* for reliable occupancy reporting  
- How each BOD Card supports **8 detection channels**
- How each Block Breakout Board connects to **4 blocks**, and why a BOD Card supports two breakout boards (total of **8 blocks**)

### 🔌 **How the BOD Card Works**

- Measuring block current to detect train presence  
- Key components used for stable detection  
- LED indicators for each block  
- “No solder jumpers” design—plug in network cables and go  
- How the BOD Card sends LCC Events to the CAN Bus for automations, signals, sound triggers, etc.

### 🧱 **The Block Breakout Board**

- The four input/output connectors for Mainline and Block wiring  
- Using simple network cables to connect Block Breakout Boards to the BOD Card  
- Why Breakout Boards reduce wiring complexity on your layout fascia or under the benchwork  
- How the board helps keep detection reliable even with long runs

### 🧩 **Integrating Detection Into an LCC Layout**

- How multiple BOD Cards can be distributed around the layout  
- How Fusion uses **LCC Events** so signals, logic, and automation respond instantly  
- Pairing BOD Cards with BSD (Short Detection), BRD (Reversing Loop Detection), and BLVD cards  
- Tips on locating cards for best power and cable routing

### 🔧 **Best Practices**

- Choosing where each detected block begins and ends  
- Avoiding false positives by grouping feeders correctly  
- Using the Hub + Node Card to minimize wiring  
- Verifying block detection using the Node Card serial monitor  
- Why testing each block at the Block Breakout Board saves time later

---

## Why LCC Fusion’s Detection System Stands Out

Fusion builds on standard **NMRA LCC** practices with enhancements:

- Clear separation of **BOD Card** (electronics) and **Block Breakout Board** (track wiring)
- Support for two Block Breakout Boards per card
- Network-cable interconnects that eliminate messy point-to-point wiring
- Self-testing via Node Card firmware
- Automatic I²C card identification
- Consistent physical card format for easy stacking and expansion

Together, the BOD Card and Block Breakout Board form a **clean, scalable, and predictable** detection solution for layouts of all sizes.

---

## Downloads and Documentation

- **Full LCC Fusion Documentation:**  https://patfleming.github.io/LccFusionProject/
  
- **GitHub Repository:**  https://github.com/patfleming/LccFusionProject
  
- **LCC Fusion Podcasts Playlist:** https://www.youtube.com/playlist?list=PLg49NFDgDCLRS7j30iTitaWUlfIdiw0Wx
  
- [Download BOD Card presentation with speaker notes (PPT)]({{ site.baseurl }}/assets/podcasts/presentations/BOD_Card.pptx) 

- [Download Block Breakout Board presentation with speaker notes (PPT)]({{ site.baseurl }}/assets/presentations/podcasts/Block_Breakout_Board.ppt) 

---

