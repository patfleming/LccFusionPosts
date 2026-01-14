---
title: "Built-In Self-Testing: Making Modular Electronics Trustworthy"
excerpt: "  DIY PCBs rarely fail in obvious ways. This post explains how built-in
  self-testing in the LCC Fusion project validates power, communications,
  external boards, and attached ICs—providing fast, practical confidence
  before modular hardware is placed into service."

date: 2026-01-12

categories: Posts
tags:
  - power-distribution
  - layout-power
  - electrical-design
  - board-level-power
  - system-integration
  - protection-and-isolation
---

## Why Self-Test Matters

When you’re building and deploying modular electronics—especially systems that may be assembled, expanded, and rewired over time—*powering on successfully* is not the same as *working correctly*.

In practice, most failures don’t come from exotic bugs. They come from very ordinary issues:

- A cold solder joint  
- A connector that isn’t seated  
- A missing pull-up  
- A swapped cable  
- A board installed in the wrong slot  
- Power that is present, but unstable  

In a layout environment, these problems often surface only after installation, when access is harder and assumptions pile up. That is the motivation behind the LCC Fusion project’s built-in self-testing capability: provide **early, repeatable confidence** that the system is electrically sane before it’s asked to do real work.

This isn’t about laboratory diagnostics. It’s about practical reliability.

---

## Design Goal: Confidence Without Complexity

From the beginning, the self-test capability was designed around a few non-negotiable goals:

- **Easy to enable**  
- **Safe to run on a live layout**  
- **Useful to builders and installers alike**  
- **No external test equipment required**  

Just as importantly, the output of the test must be *unambiguous*. The system should clearly indicate whether something is missing, miswired, or behaving outside expectations—without requiring the user to interpret raw electrical data.

---

## What the Self-Test Actually Does

Rather than running a single monolithic check, the self-test is composed of multiple focused validations. Collectively, they provide coverage across power, logic, and connectivity.

At a high level, the self-test verifies:

- Power rails and brown-out behavior  
- Microcontroller reset reasons and startup health  
- Digital I/O paths and expected idle states  
- Presence of pull-ups or pull-downs where required  
- Whether inputs are floating, driven, or shorted  
- Communication paths such as CAN and I²C (where applicable)  
- Presence or absence of attached cards or breakout boards  
- Timing-dependent behaviors when signals are exercised  
- That feedback mechanisms (LEDs, serial output, audible alerts) are operational  

Importantly, the tests are designed to **distinguish between conditions**. For example, “nothing connected” is treated differently from “connected but behaving incorrectly.”

---

## How the Self-Test Is Triggered

The self-test is intentionally simple to invoke. Depending on the situation, it can be enabled through:

- A defined power-on condition  
- A temporary jumper or button  
- A firmware configuration flag  

The test can be run during bench assembly, during installation, or later during troubleshooting. In normal operation, it can be disabled without reflashing firmware, allowing the system to transition cleanly into service.

This makes the self-test a tool—not a mode you get stuck in.

---

## How It Works (Conceptual Overview)

The self-test does not rely on introspection or hidden magic. Each check is based on a **known electrical expectation**.

Examples include:

- A signal line that should float unless an external device is present  
- A pin that should change state when driven internally  
- A bus that should respond within a defined time window  
- A supply rail that should remain stable under load  

During the test, the firmware stimulates specific lines or conditions and observes the response. Those observations are then compared against expected ranges or states. Deviations are flagged and categorized, allowing the system to report *what kind* of problem it sees—not just that something failed.

No code needs to be exposed for the value to be clear: the system is actively checking its assumptions about the hardware around it.

---

## Concrete Examples of Implemented Self-Tests

The self-test framework is not theoretical. It is built around concrete,
repeatable checks that validate whether the physical hardware behaves the way
the firmware expects.

Below are representative examples of self-tests that are implemented today.


### GPIO Line Sanity Testing

One of the most common DIY PCB failure modes is incorrect GPIO behavior:
a line that floats, a pin that is shorted, or a signal that never reaches a
valid logic level.

The self-test explicitly validates GPIO line behavior by exercising each pin
and observing how it responds.

The firmware can determine whether a pin is:

- Floating (no pull-up or pull-down present)
- Stuck low (shorted to ground)
- Stuck high (shorted to VCC)
- Responding normally when driven and released

This allows the system to report *why* a pin is failing, not just that it failed.

### Detecting Floating Inputs

Many signal lines are expected to settle into a known idle state when released.
A floating input typically indicates:

- a missing resistor
- an unconnected cable
- a breakout board that is not present

During self-test, the firmware briefly drives the pin, releases it, and then
checks whether it settles to a stable logic level. If the pin does not settle,
the condition is flagged as a floating input.

This single test catches a large percentage of wiring and assembly errors.

### Detecting Shorts to Ground or Power

A pin that is permanently asserted is just as problematic as one that floats.

By configuring and sampling the pin under controlled conditions, the self-test
can detect when a line is:

- hard-shorted to ground
- hard-shorted to a supply rail

Rather than producing a generic failure, the test output indicates the *type*
of fault detected, allowing troubleshooting to focus on soldering or wiring
instead of firmware.

### I²C Line Validation (SDA and SCL)

I²C buses are particularly sensitive to missing pull-ups and wiring faults.

The self-test treats SDA and SCL as special cases and validates that:

- the line rises when released
- pull-ups are present
- the line is not shorted low

This allows the firmware to distinguish between:

- an I²C device that is not responding
- an I²C bus that is electrically misconfigured

In practice, this frequently surfaces missing pull-ups or miswired breakout
boards before higher-level communication tests even begin.

### Pin-Role–Aware Testing

Not all pins are tested the same way.

Each self-test invocation includes the *expected role* of the pin
(generic GPIO, I²C SDA, I²C SCL, etc.). The test logic adapts accordingly.

This prevents false positives and ensures the results reflect design intent,
not just raw electrical behavior.

### Human-Readable Diagnostic Output

A deliberate design decision is that self-test results are reported using
clear, human-readable messages.

The output is intended to be understandable by builders and installers without
schematics or source code open. Each message points toward a likely physical
cause: wiring, soldering, missing components, or incorrect configuration.

This turns self-testing into a practical workflow tool, not a developer-only aid.

---

## Knowing What’s Connected

Reliable self-testing depends on more than electrical measurements—it also depends on knowing what hardware is expected to be present. In LCC Fusion, plug-in boards can identify themselves electronically, allowing the system to adjust its tests based on the actual cards and ICs installed. This avoids false errors and enables true plug-and-play behavior without manual configuration.

---

## Why This Matters in Modular Systems

Modular systems amplify both flexibility *and* risk.

Cards and breakout boards are often assembled separately. Wiring is added incrementally. Configurations change over time. In that environment, wiring errors are not a possibility—they are a certainty.

Self-testing shifts troubleshooting away from guesswork and toward evidence. Instead of asking “Is this board bad?”, the system can say “This input is floating” or “This device isn’t responding.”

That reduces build time, shortens installation cycles, and lowers the ongoing support burden.

---

## What This Says About the Project

Including self-test as a first-class feature reflects an architectural mindset:

- Users will make mistakes  
- Hardware will be reconfigured  
- Systems will evolve  

Rather than pretending otherwise, the design embraces those realities. The self-test capability is not a debugging trick bolted on at the end—it is part of how the system communicates its state to the person building or installing it.

---

## Practical Sophistication

You don’t need to study firmware internals to appreciate the value of self-testing.

- Builders gain confidence before moving on  
- Installers get fast validation on-site  
- The system tells you what it sees—before trains start moving  

That combination of transparency and practicality is what turns a collection of boards into a dependable system.
