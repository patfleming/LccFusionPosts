---

background: ukulele-1 0.5 fade-in fade-out

voice: Jack

voice-speed: 1.10

size: 720p

transition: crossfade 0.1

target: online



subtitles:

&nbsp; mode: overlay

&nbsp; position: bottom

&nbsp; break: 100

&nbsp; scale: 0.8

---



<!-- ========================================================= -->

<!-- Scene — Purpose and Scope                                 -->

<!-- ========================================================= -->



(font-size: 20)



!\[contain](Soldering\_Techniques.png)



```md

\# Soldering Techniques

\* Reusable across all PCB builds

\* Focused on problem-solving, not assembly steps

```



> Soldering techniques used throughout LCC Fusion



This video focuses on soldering techniques that apply across

multiple LCC Fusion PCB builds.



(pause: 0.6)



These techniques are referenced by the Node Card, PWM Card,

and other build videos,

so they are covered once here in detail.



(pause: 0.6)



---



<!-- ========================================================= -->

<!-- Scene — Tools That Matter                               -->

<!-- ========================================================= -->



(font-size: 20)



!\[contain](Soldering\_Techniques.png)



```md

\# Essential Soldering Tools

\* Temperature-controlled soldering station

\* Oblique Horseshoe soldering tip

\* Hot air rework gun

\* Flux (optional)

```



> Use the right tools for predictable results



Good soldering results depend more on the right tools

than on hand skill.



(pause: 0.6)



> Use Oblique Horseshoe soldering tip



A temperature-controlled soldering station

with an Oblique Horseshoe soldering tip

is strongly recommended.



(pause: 0.6)



The Oblique Horseshoe tip holds solder well,

allows precise contact,

and is ideal for both pin soldering

and removing solder bridges.



(pause: 0.6)



A hot air gun is used for SMD correction and reseating,

not for initial placement.



(pause: 0.6)



---



<!-- ========================================================= -->

<!-- Scene — Inspecting After Reflow                              -->

<!-- ========================================================= -->



(font-size: 20)



!\[contain](Soldering\_Techniques.png)



```md

\# Post-Reflow Inspection

\* Check seating

\* Check wetting

\* Look for bridges

```



> Inspect before touching the soldering iron



After reflow, always inspect the board

before soldering any pins.



(pause: 0.6)



Confirm that all SMD parts are seated flat,

pads are properly wetted,

and there are no obvious solder bridges.



(pause: 0.6)



Reflow solves placement,

but inspection confirms quality.



(pause: 0.6)



---



<!-- ========================================================= -->

<!-- Scene — Reseating Raised or Misaligned SMD Pins                             -->

<!-- ========================================================= -->



(font-size: 20)



!\[contain](Soldering\_Techniques.png)



```md

\# Reseating SMD Pins

\* Use soldering tip or hot air

\* Press straight down

```



> Fix raised pins immediately



Occasionally, an SMD pin may not fully contact the pad

after reflow.



(pause: 0.6)



> Heat and press pin down into solder



To fix this, place a hot soldering tip

directly on the pin and pad,

allow the solder to melt,

and press straight down on the pin.



(pause: 0.6)



The pin will settle into the solder

and form a proper joint.



(pause: 0.6)



---



<!-- ========================================================= -->

<!-- Scene — Removing Solder Bridges on ICs                            -->

<!-- ========================================================= -->



(font-size: 20)



!\[contain](Soldering\_Techniques.png)



```md

\# Removing Solder Bridges

\* Oblique Horseshoe tip required

\* Clean tip frequently

```



> Solder bridges are common—and fixable



Solder bridges are most common

on fine-pitch ICs.



(pause: 0.6)



The preferred method for removal

is using a hot Oblique Horseshoe soldering tip.



(pause: 0.6)



> Pull solder away from IC



Place the tip against the bridge,

allow the solder to melt,

then pull the solder away from the IC

onto the tip.



(pause: 0.6)



> Clean tip each time



Clean the tip immediately,

then repeat if needed.



(pause: 0.6)



Do not drag solder across pins—

always pull away from the component.



(pause: 0.6)



---



<!-- ========================================================= -->

<!-- Scene — Preparing IC Legs Before Placement                          -->

<!-- ========================================================= -->



(font-size: 20)



!\[contain](Soldering\_Techniques.png)



```md

\# Preparing IC Legs

\* Flatten before placement

\* Align before pasting

``` 



> IC legs often need adjustment



IC legs are often bent during shipping or handling,

especially the corner pins.



(pause: 0.6)



Before placement,

set the IC on a flat, hard surface

and gently press down

to flatten all legs evenly.



(pause: 0.6)



> Use X-Acto knife for alignments



Use a No. 11 X-Acto knife

to align any pins that are out of parallel.



(pause: 0.6)



If this step is skipped,

pins may not seat into the solder paste

and will cause reflow defects.



(pause: 0.6)



---



<!-- ========================================================= -->

<!-- Scene — Hand Soldering PTH Pins (Technique)                        -->

<!-- ========================================================= -->



(font-size: 20)



!\[contain](Soldering\_Techniques.png)



```md

\# PTH Pin Soldering

\* Heat pin and pad together

\* Form solder up the lead

```



> Proper PTH soldering technique



When soldering through-hole pins,

place the Oblique Horseshoe tip at roughly a 45-degree angle

so it contacts both the pin and the plated ring.



(pause: 0.6)



Apply solder to the pin and tip,

then remove the solder wire.



(pause: 0.6)



As the solder melts,

pull the tip slightly upward

to draw solder from the ring

up along the pin.



(pause: 0.6)



This creates a strong,

clean joint with good wetting.



(pause: 0.6)



---



<!-- ========================================================= -->

<!-- Scene — Fixing PTH Issues                        -->

<!-- ========================================================= -->



(font-size: 20)



!\[contain](Soldering\_Techniques.png)



```md

\# PTH Corrections

\* Reseat parts

\* Remove bridges

```



> Fix issues before trimming leads



If a PTH component is not seated flush,

heat one pin and gently press the part down

until it contacts the PCB surface.



(pause: 0.6)



If solder bridges form between pins,

use the Oblique Horseshoe tip to pull excess solder away,

cleaning the tip after each pass over the pins.



(pause: 0.6)



Only trim leads, not pins, 

after all solder joints are complete and verified.



(pause: 0.6)



---



<!-- ========================================================= -->

<!-- Scene — Final Cleanup and Verification                    -->

<!-- ========================================================= -->



(font-size: 20)



!\[contain](Soldering\_Techniques.png)



```md

\# Final Cleanup

\* Inspect every joint

\* Optional electrical cleaner

```



> Finish with inspection, not assumptions



After soldering,

inspect every pin and pad.



(pause: 0.6)



Confirm there are no cold joints,

no missed pins,

and no solder bridges.



(pause: 0.6)



Because LCC Fusion uses no-clean solder paste,

flux residue is minimal.



(pause: 0.6)



> Clean with alcohol or electrical contact cleaner



If desired,

use alcohol or electrical contact cleaner and a soft brush,

then allow the board to air dry.



(pause: 0.6)



Do not wipe with cloths—

they snag components and leave residue.



(pause: 0.6)



---



<!-- ========================================================= -->

<!-- Scene — Closing                   -->

<!-- ========================================================= -->



(font-size: 20)



!\[contain](Soldering\_Techniques.png)



```md

\# Technique Matters

\* Repeatable

\* Fixable

\* Reusable

```



> These techniques apply everywhere



These soldering techniques apply

across all LCC Fusion PCB builds.



(pause: 0.6)



They are referenced by build videos

so those videos can stay focused

on assembly flow—not soldering mechanics.



(pause: 0.6)



With soldering covered,

we can now focus entirely

on building and configuring the system.



(pause: 0.6)

