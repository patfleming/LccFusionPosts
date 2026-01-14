---
title: "Firmware at Scale: Managing Features, Memory, and Usability on the ESP32"
excerpt: "How real memory limits, multiple node roles, and DIY usability constraints shaped how firmware is built, delivered, and deployed in LCC Fusion."
date: 2026-01-14

categories: Posts
tags:
  - firmware
  - esp32
  - openmrn
  - automation
  - architecture
  - embedded
  - system-design
  - docs-as-ui
---

---

## Where the Real Constraint Appeared

One of the first hard constraints I ran into building LCC Fusion was memory.

The ESP32 is a capable MCU, but once OpenMRN enters the picture, the available headroom drops quickly. OpenMRN provides a complete, standards-compliant implementation of LCC, and it does exactly what it should do—but it also consumes a significant and largely non-negotiable portion of both flash and SRAM.

That left far less space than expected for everything else.

At first, I assumed this was an efficiency problem. I spent a lot of time analyzing code size, trimming logic, and trying to optimize paths. None of that fundamentally worked. Even aggressive optimization only delayed the outcome.

The problem wasn’t inefficient code.

The problem was that the system was growing in capability, and a single firmware image was being asked to do too much.

---

## Usability Made the Problem Worse (and Better)

At the same time, usability improvements were pushing the system in the opposite direction.

As functionality was separated—input devices versus output devices, detection versus actuation, configuration versus operation—the system became easier to understand and easier to use. Builders could reason about what a device did. Installers could match hardware to intent. Users didn’t have to guess how pieces fit together.

That clarity mattered, especially because LCC Fusion is DIY.

But every improvement came at a cost. Separation meant more code paths, more optional features, and more memory usage. Doing the *right* thing architecturally made the memory problem worse, not better.

This wasn’t something that could be solved by trimming features or collapsing responsibilities back together. The system needed to remain flexible, and that flexibility had a real cost.

---

## Firmware Has Different Jobs

Another pressure emerged as the hardware matured: the same firmware family was being used in very different ways.

LCC Fusion firmware runs across multiple node types and I/O devices. A single project might include Node Cards, Quad-Node Cards, and multiple breakout boards. On a Quad-Node Card, four ESP32s may each serve a different role—one focused on logic processing, another bridging CAN to wireless links, another managing a layout district.

A single firmware image cannot serve all of those roles efficiently.

Firmware also has different jobs at different points in the system’s lifecycle.

A builder may want firmware that emphasizes diagnostics and self-testing. An installer may reload firmware to match what the planner specified. An operator may want a stable, feature-focused build once the system is in place.

The hardware may be the same. The needs are not.

This reinforced a key requirement: DIY does not mean programmer. Builders and installers should not be expected to install toolchains, manage build flags, or compile firmware.

---

## The First Solution: Controlled Builds

The turning point came when we stopped trying to make one firmware image do everything.

Instead, build-time controls were introduced to enable or disable major feature groups—Wi-Fi, ESP-NOW, device support, debugging, and optional subsystems. This immediately relieved memory pressure and allowed firmware to better match its intended role.

But it created a new problem: delivery.

Once multiple firmware builds exist, how do they get to the end user without pushing complexity back onto them?

---

## Firmware That Works the Moment It Boots

Installation alone was not enough.

Many embedded devices boot into an unconfigured state, requiring additional steps before they do anything useful. For developers this is acceptable; for builders and installers it is friction.

LCC Fusion firmware needed to be operational out of the box.

That meant configuration data had to be treated as part of the firmware itself. Defaults, identifiers, and initial configuration needed to be bundled alongside the executable code and delivered as a single unit.

Configuration stopped being something applied *after* installation and became part of the firmware deliverable.

---

## Documentation as the User Interface

Once firmware variants and preconfigured data existed, the next challenge was how to present them.

Instead of filenames or download tables, LCC Fusion uses documentation as the interface.

The documentation explains why variants exist, what problems each one solves, and what tradeoffs are involved. From there, users select the firmware that matches their intent directly from the documentation.

The documentation doesn’t just describe the system—it drives it.

---

## Scaling the Build Process

With multiple firmware variants, manual builds quickly become unsustainable.

Each variant must be built consistently, include the correct configuration data, and appear in the documentation where users expect it. Doing this by hand does not scale.

The solution was to integrate firmware builds directly into the documentation build pipeline. Variants are declared once, built automatically, and placed into the site structure alongside the documentation that explains them.

Documentation and firmware are generated together, ensuring they never drift apart.

---

## Delivering Firmware Directly From the Docs

The final piece is delivery.

Firmware is installed directly from the documentation using browser-based tooling. Users connect a USB cable, select the firmware variant that matches their card and purpose, and load it onto the ESP32.

- No IDE.  

- No command line.  
- No build steps.

The documentation itself becomes the installer.

---

## Example: Firmware Delivery Without Tooling

This approach is easiest to understand with a concrete example.

A typical firmware installation section in the documentation contains a short explanation, an install button, and a small script:

```html
<h2>Install Node Card Firmware</h2>

<p>
Select the firmware that matches your Node Card and intended use.
Connect the ESP32 to your computer using a USB cable, then click Install.
</p>

<esp-web-install-button manifest="manifest.json">
</esp-web-install-button>

<script
  type="module"
  src="https://unpkg.com/esp-web-tools@10/dist/web/install-button.js">
</script>
```

From the user’s perspective, that is the entire process. They click **Install**, select the USB serial port, and the firmware is flashed directly onto the ESP32 from the browser.

Behind the button is a small manifest file that defines what should be written to flash and where:

```{
  "name": "LCC Fusion – Node Card Firmware",
  "version": "1.0.0",
  "builds": [
    {
      "chipFamily": "ESP32",
      "parts": [
        { "path": "bootloader.bin", "offset": 4096 },
        { "path": "partitions.bin", "offset": 32768 },
        { "path": "firmware.bin",   "offset": 65536 },
        { "path": "spiffs.bin",     "offset": 0xD50000 }
      ]
    }
  ]
}
```

This ties together several architectural decisions: a standardized flash layout, multiple firmware deliverables, and preconfigured data delivered alongside the firmware.

### How `spiffs.bin` Is Created

The `spiffs.bin` file is generated at build time from a standard `/data` directory using the `mkspiffs` tool:

```
mkspiffs -c data/ -b 4096 -p 256 -s 0x2B0000 spiffs.bin
```

This packages configuration files and defaults into a filesystem image that is flashed with the firmware. When the ESP32 boots, SPIFFS is mounted automatically and the node starts in a known, operational state.

All of this complexity is hidden from the user. Firmware installs in one step and works immediately.

------

## Why This Still Matters as the Hardware Evolves

Newer MCUs like the ESP32-P4 offer significantly more memory, and larger flash sizes—8 MB being the current standard—have reduced pressure on program size.

But memory alone was never the whole problem.

SRAM limits still matter. OpenMRN still consumes a large, fixed portion of available memory. Attempts to offload meaningful functionality into PSRAM proved ineffective, and the loss of pins outweighed any benefit.

More importantly, the need for multiple firmware builds was never driven solely by memory.

Different hardware roles still exist. Different lifecycle phases still exist. Builders, installers, and operators still need firmware that matches their purpose. A single “everything enabled” image would blur responsibilities and complicate deployment.

Treating firmware as a documented, selectable deliverable—rather than something users must build—keeps the system flexible without pushing complexity onto the user.

------

## Takeaways

Firmware variants are not a sign of failure. They are a sign that a system has grown beyond its initial assumptions.

The real challenge is not avoiding variants, but owning them—making them intentional, understandable, and easy to use.

By treating firmware and configuration data as first-class deliverables, integrating them into documentation, and automating their creation and delivery, LCC Fusion remains flexible without becoming inaccessible.

The real constraint was never flash or RAM.

It was how much complexity users were asked to absorb.

