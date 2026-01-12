---
title: "LCC Fusion Podcast – BSD Card & Block Breakout Board"
excerpt: "Short detection and block protection using the BSD Card and the Block Breakout Board"

date: 2025-11-22

categories: Podcasts
tags: [bsd, detection, breakout-boards]

gallery:
  - url: /assets/podcasts/images/posters/BSD_Card.jpg
    image_path: /assets/podcasts/images/posters/BSD_Card.jpg
    alt: "BSD Card Podcast Presentation"
    title: "BSD Card"

  - url: /assets/podcasts/images/posters/Block_Breakout_Board.jpg
    image_path: /assets/podcasts/images/posters/Block_Breakout_Board.jpg
    alt: "Block Breakout Board Podcast Presentation"
    title: "Block Breakout Board"
---

{% include gallery layout="third" caption="LCC Fusion BSD Card & Block Breakout Board" %}

In this LCC Fusion podcast episode, Nelson and Harrison take a deep dive into **Block Short Detection** using the **BSD Card** and the standard **Block Breakout Board**.  
These two boards work together to provide **per-block short protection**, **accurate occupancy detection**, and **automatic recovery** that keeps the rest of the layout running smoothly.

The BSD Card is Fusion’s electrical “first responder,” and this episode explains exactly how and why it works.

---

## Watch the Podcasts

- [BSD Card Overview (video)](https://youtu.be/TbA53L5_Z4Y){:target="_blank" rel="noopener"}

- [Block Breakout Board Overview (video)](https://youtu.be/APAasm0nT_o){:target="_blank" rel="noopener"}

---

## What these episodes cover

### 🔥 **What Block Short Detection Really Means**

- Why certain blocks—mainlines, yard throats, and crossovers—need **local, immediate protection**
- How the BSD Card protects **four blocks** independently
- Why short recovery happens *on the card itself*, not at the booster
- How BSD Cards prevent wide-area shutdowns and keep trains moving

### 🔌 **How the BSD Card Works**

- Reading digital current levels to determine **clear**, **occupied**, or **shorted**
- How the BSD uses its on-board ESP32 to debounce, filter, and interpret block current
- Automatic short recovery:  
  **power off → wait → retry → report**
- When and why the BSD reports states to the Node Card instead of publishing events directly
- LED indicators for each block to simplify testing and troubleshooting

### 🧱 **The Block Breakout Board**

- The wiring layer for four blocks  
- Simplifies feeder wiring and reduces clutter under the layout  
- Works identically for the BOD, BSD, and BRD Cards  
- Uses standard network cables for clean, reliable connections  
- Helps isolate wiring issues before connecting to electronics

### 🤖 **Integrating the BSD into a Fusion Layout**

- How the BSD Card sends clean state updates to the Node Card via I2C  
- How the Node Card publishes LCC events for automation  
- Signals, routes, and logic reacting instantly to short or occupancy events  
- Short events triggering **operator alerts**, **voice messages**, or **safety interlocks**

### ⚙️ **Configuring the BSD Card**

- Setting the **occupancy current range** for your locomotives
- Using defaults for turnout cards
- Configuring signals:  
  choose the PWM card, assign lamp lines, set up aspects
- Event values auto-populate, reducing setup effort
- Logic statements defined by simple **conditions and actions**  
  (e.g., *If Block 3 is shorted → Set Signal to Stop*)

### 🔧 **Best Practices**

- Test using the Node Card’s **self-test** to confirm I2C connection and EEPROM identity
- Use a small load to verify occupancy thresholds
- Momentary short to confirm short detection and auto-reset
- Use the Node Card’s serial monitor to verify I2C messages  
- Keep BSD Cards close to the blocks they protect  
- Treat each BSD as a **4-block protected district**

---

## Why LCC Fusion’s Protection System Stands Out

Fusion builds on the NMRA LCC model but enhances it with a strong **edge-computing architecture**:

- BSD Cards interpret and protect blocks **locally**, without loading the Node Card  
- Block state decisions are made *before* they reach layout logic, improving reliability  
- Modular design allows layouts to scale without adding more LCC Nodes  
- Breakout Boards keep wiring simple and reduce troubleshooting time  
- Self-testing and automatic card identification help installers get it right the first time

The BSD Card and Block Breakout Board together form a **robust**, **scalable**, and **operator-friendly** solution for short detection and block automation.

---

## Downloads and Documentation

- **Full LCC Fusion Documentation:**  https://patfleming.github.io/LccFusionProject/
  
- **GitHub Repository:**  https://github.com/patfleming/LccFusionProject
  
- **LCC Fusion Podcasts Playlist:** https://www.youtube.com/playlist?list=PLg49NFDgDCLRS7j30iTitaWUlfIdiw0Wx
  
- [Download BSD Card presentation with speaker notes (PPT)]({{ site.baseurl }}/assets/podcasts/presentations/BSD_Card.pptx)

- [Download Block Breakout Board presentation with speaker notes (PPT)]({{ site.baseurl }}/assets/podcasts/presentations/Block_Breakout_Board.ppt)

---

