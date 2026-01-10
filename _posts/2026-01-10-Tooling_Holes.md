---
layout: posts
classes: wide
toc: false
author_profile: true
permalink: /:slug/

date: 2026-01-10

title: "Tooling Holes: Designing DIY SMD Reflow for Accuracy, Cost, and Repeatability"
excerpt: "How tooling holes and push-pin registration make stencil alignment fast, accurate, and affordable—enabling repeatable DIY SMD reflow without frames or full-size stencils."
categories: [Documentation]
tags: [tools]
---

## Introduction

From the very beginning of this project, I set a non-negotiable constraint:

If this hardware was going to be used by *other people*, then **DIY SMD reflow and stencil alignment had to be accurate, repeatable, and affordable**.
 If that could not be solved cleanly, the project would not move forward.

That requirement came *before* board layouts, firmware, or documentation. It was foundational.

This is **Part 1** of a two-part series.  
**Part 2:** [Lessons Learned: Making DIY SMD Reflow Predictable and Repeatable]({{ "/diy-reflow/" | relative_url }}) — lessons learned that make the workflow predictable and repeatable.

## Why stencil alignment mattered more than reflow itself

DIY reflow is no longer exotic. With the right solder paste and a modest countertop oven, it’s approachable and reliable.

Stencil alignment, however, is where most DIY workflows quietly break down.

The typical solutions involve:

- Full-size stencils
- Professional stencil frames
- Dedicated fixtures
- Higher fabrication and shipping costs

Those approaches work—but they fail the “others can do this” test. They are expensive, bulky, and fragile assumptions to impose on people building a board at home.

If stencil alignment *required* professional framing, then open hardware built around SMD would always be exclusionary.

## Early attempts (and why they weren’t good enough)

Like many builders, I tried the usual techniques:

- Large default-sized stencils
- Magnets
- Blocks
- Visual alignment and tape

They worked *sometimes*. But they were slow, fiddly, and highly dependent on individual technique.

More importantly, they were not something I could responsibly document and hand off to others with confidence.

## Borrowing the right idea from industry

The breakthrough came not from hobby forums, but from paying attention to how PCB assembly is done professionally.

Assembly houses don’t eyeball stencil alignment.
 They don’t rely on frames for precision.

They use **tooling holes**.

Once that clicked, the problem reframed itself:

> Alignment is a geometry problem, not a fixture problem.

If the PCB and the stencil could mechanically register to the same reference points, then everything else became simpler.

## The real challenge: making this work in a DIY toolchain

Understanding tooling holes conceptually was easy.

Making them work reliably in a hobbyist toolchain—specifically using Fritzing for PCB design and stencil generation—was not.

The requirements were subtle but strict:

- The PCB needed a drill hole
- The stencil needed a matching cutout
- The feature had to survive Gerber export and stencil generation
- It could not interfere electrically with the board
- It had to be repeatable for others

There is no first-class “tooling hole” concept in Fritzing. Getting all of this to work took significant trial and error.

Eventually, I arrived at a dedicated **tooling hole part** that reliably produced:

- A drill hole in the PCB
- A matching cutout in the stencil

Once that existed, everything else fell into place.

## The resulting workflow

With tooling holes designed directly into the PCB:

- Small stencils became practical
- No professional frames were required
- Alignment became deterministic instead of visual

The physical setup is deliberately simple:

- Two push pins through the stencil and PCB
- A foam board underneath for compliance

That’s it.

Stencil alignment is now:

- Fast
- Accurate
- Repeatable
- Cheap

And critically: **easy to explain and document for others**.

## Why this unlocked the larger project

This wasn’t an optimization discovered late—it was a gate.

Only after stencil alignment could be made:

- Affordable
- Reliable
- Builder-friendly

…did it make sense to proceed with a larger open hardware ecosystem built around fine-pitch SMD parts.

Tooling holes turned out to be the missing link between “I can build this” and “others can build this.”

## Using the Tooling Hole Part in Fritzing

To support stencil alignment without frames, this approach relies on a dedicated **tooling hole part** designed to produce **both a PCB drill hole and a matching stencil cutout**. The stencil cutout enables mechanical registration; the hole exists purely for alignment, not electrical connectivity.

### Download

- **Tooling Hole (Fritzing Part):**
   [Tooling-Hole.fzpz]({{ site.baseurl }}/assets/other/Tooling-Hole.fzpz)

### How it is used

- Import the part into Fritzing using **File → Open** (or by dragging it into the Parts panel).
- Place the tooling hole part on the **PCB view** only.
- Add **two tooling holes**, positioned at **diagonal corners of the PCB**.
- The holes are not connected to any net and function solely as **mechanical registration features**.

### Assembly setup

During stencil application:

- Two push pins are inserted through the stencil and PCB tooling holes.
- A foam board beneath the PCB provides compliance.
- This mechanically registers the stencil and board without frames or fixtures.

The result is **fast, accurate, and repeatable stencil alignment**, enabling the use of **small, low-cost stencils** suitable for DIY reflow workflows.

### Sharing the solution

This tooling hole part is shared as a **known-good artifact, reusable artifact**. It is provided as-is because it reliably produces the required PCB drill holes and stencil cutouts in the Fritzing toolchain.

If you are using Fritzing and want to avoid full-size stencils, professional frames, or alignment guesswork, this removes a major barrier to low-cost, repeatable DIY SMD reflow.

### Tooling Holes in Other PCB CAD Tools (e.g., KiCad)

Many PCB CAD tools treat tooling holes and stencil apertures as first-class fabrication features. In those environments, creating the same alignment mechanism does not require a custom part.

The typical approach is:

- Place a **non-plated through hole (NPTH)** on the PCB for mechanical registration.
- Add a **non-electrical pad or footprint element** at the same location.
- Configure that element to:
  - Have no copper connectivity
  - Be excluded from solder mask
  - Be included in the **paste layer only**

This produces a **drill hole in the PCB** and a **matching cutout in the stencil**, achieving the same push-pin registration used here.

In tools like KiCad, paste apertures are not implicitly tied to electrical pads, which makes this straightforward once the need for stencil alignment is understood.

Fritzing does not expose this capability directly, which is why a dedicated tooling hole part was created for that workflow.

> This difference is why tooling holes are commonplace in professional assembly workflows, but require explicit support in hobbyist tools like Fritzing.

## Final takeaway

The most important lesson here wasn’t about reflow temperatures or solder paste.

It was this:

> If you expect others to build your hardware, you must design for *their* assembly reality—not just your own bench.

Tooling holes made that possible.