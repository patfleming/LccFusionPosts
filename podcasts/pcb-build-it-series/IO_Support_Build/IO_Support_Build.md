---
background: ukulele-1 0.5 fade-in fade-out
voice: Bill
size: 720p
transition: crossfade 0.1
target: online

subtitles:
  mode: overlay
  position: bottom
  break: 100
  scale: 0.8
---

<!-- ========================================================= --> 
<!-- Scene: Introduction and Scope --> 
<!-- ========================================================= -->

(font-size: 20)

![contain](IO_Support_Build.png)

```md
# Build I/O Cards
* Prior build videos required
* Same process, different PCBs
```

> Build additional LCC Fusion I/O boards

This video covers the assembly of several LCC Fusion I/O Card PCBs and
the Node Bus Hub that connects them.

(pause: 0.6)

It assumes you have already watched the Reflow Introduction,
Soldering Techniques, and Node Card Build videos.

(pause: 0.6)

The same overall build process is used throughout.

(pause: 0.6)

---

<!-- ========================================================= --> 
<!-- Scene: PCBs Covered --> 
<!-- ========================================================= -->

(font-size: 20)

![contain](IO_Support_Build.png)

```md
# PCBs Covered
* PWM Card
* BOD Card
* Signal Mast Breakout Board
* Block Breakout Board
* Node Bus Hub
```

> One build flow, multiple PCBs

All of these PCBs follow the same basic assembly steps.

(pause: 0.6)

The differences are in component density
and the level of care required during placement.

(pause: 0.6)

---

<!-- ========================================================= --> 
<!-- Scene: Stencil Requirement --> 
<!-- ========================================================= -->

(font-size: 20)

![contain](IO_Support_Build.png)

```md
# Stencil Requirement
* PWM Card: REQUIRED
* BOD Card: REQUIRED
* Breakout Boards: NOT USED
* Node Bus Hub: REQUIRED
```

> Stencils are required for PCBs with fine-pitch ICs

Both the PWM Card and the BOD Card include fine-pitch ICs with small solder pads.

(pause: 0.6)

Using a stencil is required to meter solder volume correctly
and avoid solder bridges.

(pause: 0.6)

The small cost of a stencil is worth avoiding failed PCBs.

(pause: 0.6)

---

<!-- ========================================================= --> 
<!-- Scene: Ordering PCBs and Stencils --> 
<!-- ========================================================= -->

(font-size: 20)

![contain](IO_Support_Build.png)

```md
# Ordering
* Gerbers ready to upload
* Use JLCPCB
* Order stencil with PCBs
```

> Start with the correct PCB and stencil

Gerber files for all LCC Fusion PCBs are ready to upload
directly to JLCPCB.

(pause: 0.6)

When ordering PWM or BOD Cards,
order the stencil at the same time.

(pause: 0.6)

Request a custom 100 × 150 mm stencil
to reduce shipping costs.

(pause: 0.6)

---

<!-- ========================================================= --> 
<!-- Scene: Applying Solder Paste --> 
<!-- ========================================================= -->


(font-size: 20)

![contain](IO_Support_Build.png)

```md
# Applying Solder Paste
* Stencil required for PWM and BOD Cards
* Direct paste for breakout boards
```

> Two paste application paths

For PWM and BOD Cards,
apply solder paste using the stencil, just as with the Node Card.

(pause: 0.6)

For the breakout boards, no stencil is used.

(pause: 0.6)

Apply a small amount of paste directly to the large pads.
These PCBs are intentionally forgiving.

(pause: 0.6)

Some breakout boards offer multiple connector options,
so always follow the step-by-step build documentation.

(pause: 0.6)

---

<!-- ========================================================= --> 
<!-- Scene: Component Placement --> 
<!-- ========================================================= -->

(font-size: 20)

![contain](IO_Support_Build.png)

```md
# Component Placement
* Extra care for fine-pitch ICs
   - Prepare IC pins: flatten and align before placement
   - Verify all pins contact paste
* Normal care on breakout boards
```

> Check and align IC pins carefully

The PCBs with fine-pitch ICs require extra care during
pin preparation and component placement.

(pause: 0.6)

Prepare the IC pins by straightening and flattening them.
Align each IC carefully over the solder paste and take your time.

(pause: 0.6)

Breakout boards use large SMD and PTH parts
and are much more forgiving.

(pause: 0.6)

---

<!-- ========================================================= --> 
<!-- Scene: Reflow --> 
<!-- ========================================================= -->

(font-size: 20)

![contain](IO_Support_Build.png)

```md
# Reflow
* Same reflow process for all boards
* Set oven to BROIL
* Heat until oven reaches 280 °F
* Turn off oven and allow a slow cool-down
* Multiple boards can be reflowed together
```

> Use the same reflow process for all PCBs

Reflow is done exactly as shown
in the Reflow Introduction video.

(pause: 0.6)

Set the oven to BROIL,
heat until the oven reaches 280 °F,
then turn it off and allow a slow cool-down.

(pause: 0.6)

Multiple PCBs can be reflowed at once.

(pause: 0.6)

---

<!-- ========================================================= --> 
<!-- Scene: Inspection and PTH Soldering --> 
<!-- ========================================================= -->

(font-size: 20)

![contain](IO_Support_Build.png)

```md
# Final Steps
* Inspect after reflow
* Hand-solder PTH pins
```

> Inspect first, then solder

Inspect all PCBs after reflow.

(pause: 0.6)

On PWM and BOD Cards,
closely inspect fine-pitch IC pins for bridges or lifted pins.

(pause: 0.6)

The reflow process can tack PTH components in place,
making the final hand soldering easier and cleaner.

(pause: 0.6)

---

<!-- ========================================================= --> 
<!-- Scene: Summary --> 
<!-- ========================================================= -->

(font-size: 20)

![contain](IO_Support_Build.png)

```md
# Summary
* Same process across PCBs
* Stencils required for PCBs with fine-pitch ICs
* Breakout boards are intentionally simple
```

> Build confidence comes from repeatability

All these LCC Fusion I/O boards follow the same build process.

(pause: 0.6)

The key difference is the level of care required,
not the steps themselves.

(pause: 0.6)

With the PCBs built,
the next video covers installation and system integration.

(pause: 0.6)
