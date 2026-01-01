---
background: ukulele-1 0.5 fade-in fade-out
voice: Jack
voice-speed: 1.10
size: 720p
transition: crossfade 0.1
target: online

subtitles:
  mode: overlay
  position: bottom
  break: 100
  scale: 0.8
---

<!-- ===================================================== -->
<!-- Scene 1: Reflow — Concept & Benefits                  -->
<!-- ===================================================== -->

(font-size: 20)

![contain](Reflow.png)

```md
# Reflow — Concept
* Reflow secures components using solder paste and heat
* All **SMD** parts are soldered in a single step
* Reflow can also **tack PTH parts** for later pin soldering
* Uses **low-melt 138 degree Celsisus  T4 solder paste**

# Terminology
* **SMD** – Surface Mount Device
* **PTH** – Pin / Through-Hole component
* **PCB** – Printed Circuit Board
```
> Reflow = solder paste + oven (not hand soldering)

Before we touch solder paste, I want to define what “reflow” means,
and how we use it to build LCC Fusion project PCBs.

(pause: 0.6)

Reflow is simply melting solder paste to secure components to the PCB,
all at once—so you’re not hand-soldering every tiny pad individually.

(pause: 0.8)

> Low-melt paste protects the PCB

For LCC Fusion, we recommend a low-melt temperature T4 solder paste,
commonly sold in syringes.
Specifically, a paste with a 138 degree Celsius—280 degree Fahrenheit—melting point,
which helps prevent PCB discoloration during the process.

(pause: 0.8)

> Reflow also tacks PTH parts in place

A key benefit shown throughout this video series is that reflow is normally used for SMD parts,
but it can also be used to lightly tack PTH parts in place.
This tacking step holds those parts during the final pin-soldering process,
which we’ll demonstrate later in the build.

That’s the core idea behind reflow.

(pause: 0.6)

---

<!-- ===================================================== --> 
<!-- Scene 2: Reflow — Execution & Constraints --> 
<!-- ===================================================== -->

(font-size: 20)

![contain](Reflow.png)
 
```md
# Reflow — Execution
* Small digital countertop oven
* Oven set to **BROIL** (top heat)
* Control by **oven temperature**
* Stop at **280 °F (138 °C)**, then slow cool
* PCB must be **suspended**
```

(font-size: 20)

Now let’s talk about how we actually perform the reflow step.

(pause: 0.6)

> Control by oven temperature — not by watching solder melt
> Turn oven off at 280 °F, then open door

For heating, we use a small digital countertop oven.
We run the oven in BROIL mode so heat is applied from the top of the PCB.

(pause: 0.8)

Here’s the critical control rule:
we don’t time this by watching the solder melt.
We heat until the oven display reaches 280 degrees Fahrenheit,
then turn the oven off and open the door for a slow cool-down.

(pause: 0.8)

That’s it—consistent, repeatable reflow every time.
Multiple PCBs can be reflowed at once.

(pause: 0.8)

> PCB must be suspended — PTH leads extend below the board

One more critical detail:
the PCB must be suspended during reflow,
because PTH leads extend below the board.
 
> Use all-metal CLAMPREX Helping Hands on a steel plate

We use an all-metal PCB holder mounted to a steel plate.
This setup is used throughout the PCB build and reflow process.

The magnetic base keeps the holder firmly attached to the plate,
so the board remains stable inside the oven.

(pause: 0.6)

---

<!-- ===================================================== -->
<!-- Scene: Preparing Parts for Assembly -->
<!-- ===================================================== -->

(font-size: 20)

![contain](PCB_to_Layout.png)

```md
# Preparing Parts for Assembly
* Separate and label parts before starting
* Use organizers for small components
* Transfer parts to a tray during assembly
* Use a **Rhinestone** wax tipped picker placing small parts
```

> Prepare parts before placing anything on the PCB

Before we start placing components on the board, I want to cover how I prepare parts for assembly.

(pause: 0.6)

> Organization prevents placement mistakes
> Separate parts into labeled containers

This step isn’t about soldering — it’s about setting yourself up for a smooth, mistake-free build.

(pause: 0.6)

As parts arrive, I never build directly from the shipping bags.  
I separate everything into labeled containers for storage, organized by component type and value.

(pause: 0.6)

> Small parts go into organizers
> Use a parts tray during the build

For small components like resistors, capacitors, diodes, and LEDs, I use small compartment organizers.  
Many of these parts look identical, and mixing them is a common source of errors.

(pause: 0.6)

During the build itself, I only bring out the parts needed for the current step.  
These go into a parts tray placed next to the PCB for easy access with the picker.

(pause: 0.6)

> Fewer mistakes, less rework

This keeps the workspace clean, helps maintain orientation awareness, and reduces the chance of placing the wrong part.

(pause: 0.6)

With the parts prepared and organized, you're ready to build a PCB

(pause: 0.6)

---

<!-- ===================================================== -->
<!-- Scene: Sourcing -->
<!-- ===================================================== -->

(font-size: 20)

![contain](PCB_to_Layout.png)

```md
# Sourcing Parts, Tools, and Supplies
* **Tools** — Amazon
* **Organizers & trays** — Hobby Lobby
* **Electronic components** — AliExpress
* Full component lists and search links - https://patfleming.github.io/LccFusionProject/pcb-components/
```

Buy tools locally, buy parts globally

Most of the tools used in this video series are easiest to source from Amazon.
This includes things like PCB holders, pickers, and soldering tools.


(pause: 0.6)

For small parts organizers and storage trays, craft stores like Hobby Lobby are a good option.
They’re inexpensive, easy to find locally, and work well for sorting components during assembly.
Look for **Bead & Jewelry Storage** or **Rhinestone** organizers.

(pause: 0.6)

For electronic components — resistors, capacitors, ICs, connectors, and LEDs — we primarily use AliExpress.
It offers the best pricing for hobby-scale builds and is well-suited for non-urgent projects.
To save on shipping cost, select **Choice** items for free shipping on orders over 10 dollars.

(pause: 0.6)

To remove guesswork, the LCC Fusion documentation includes a complete component list with direct AliExpress search links for each part.

(pause: 0.6)



