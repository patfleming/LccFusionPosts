---
title: "Firmware Variants Without Feature Lock-In"
excerpt: "How LCC Fusion avoids cutting features or forcing users to become developers by treating firmware variants and preconfigured data as first-class deliverables."

date: 2026-01-12

categories: Posts
tags: [firmware-variants, build-pipeline, esp32, usability, architecture, docs-as-ui]

---

## The Assumption That Breaks First: “One Firmware Fits All”

Most embedded projects begin with an unspoken assumption: there will be *one* firmware image.

Early on, this works. The feature set is small, the hardware is new, and tradeoffs are manageable. Everything compiles, everything fits, and the project moves forward. Early users are often developers themselves, so rough edges are tolerated.

But this assumption is fragile—and it is usually the **first thing that breaks** as a project matures.

As features accumulate—connectivity options, user interfaces, diagnostics, sensors, storage—the firmware stops being a single coherent thing. It becomes a collection of capabilities competing for limited flash, RAM, and attention. On MCUs like the ESP32, those limits are real and unavoidable. You can optimize, refactor, and tune, but eventually you reach a point where “just turning everything on” is no longer viable.

This is where many projects make an uncomfortable choice.

One path is to **cut features**. Something has to go, so advanced capabilities get removed or postponed indefinitely. The project remains buildable, but only by narrowing its scope and excluding certain use cases.

The other path is to **push complexity onto users**. Features remain available, but only if the user is willing to install an IDE, learn the build system, enable the right flags, and compile their own firmware. The project stays flexible—but only for developers.

Both paths solve the memory problem, but they do so by creating a *human* problem. Either users lose capabilities they care about, or they are asked to become firmware engineers just to use the device.

Neither outcome was acceptable for LCC Fusion.

From the beginning, feature growth was intentional. Support for Bluetooth, Wi-Fi, ESP-NOW, serial interfaces, displays, diagnostics, and multiple classes of devices wasn’t accidental scope creep—it was the point. The firmware was meant to grow with the system, not be frozen at the moment when it still fit comfortably in flash.

That meant the original assumption had to be challenged.

If one firmware image can’t serve all users, the problem isn’t how to force it to—it’s how to abandon the assumption entirely without fragmenting the project.

---

## When Feature Growth Is Intentional, Not Accidental

In many projects, features accumulate reluctantly. Each new capability is weighed against memory usage, complexity, and maintenance cost. Growth is treated as a risk.

In LCC Fusion, growth was a requirement.

The system was designed to scale across different layouts, devices, and operating styles. That meant supporting multiple communication paths, different kinds of sensors and actuators, various user interfaces, and increasingly sophisticated diagnostics. Over time, the firmware became feature-rich by design.

This created a tension. MCU limits were not a surprise, but they were unavoidable. Flash and RAM would eventually become scarce. The question was not *whether* limits would be reached, but *how* the project would respond when they were.

The goal was never to decide in advance which features were “core” and which were “optional.” That would lock the project into a static definition just as users were beginning to explore what was possible.

Instead, the project needed a way to let features grow **without forcing a single definition of the firmware**.

---

## Memory Limits Become Product Decisions

Once memory constraints enter the picture, technical decisions quickly turn into product decisions.

Which features ship?
Which users get left out?
Who is expected to solve the problem?

In many open projects, the implicit answer is “advanced users can build it themselves.” That keeps the codebase flexible, but it quietly shifts responsibility away from the project and onto the user.

LCC Fusion had a different audience in mind. Many end users are not developers. They are builders, installers, and operators. Asking them to set up a toolchain, resolve dependencies, and compile firmware is often a non-starter.

So firmware variants became inevitable—but not as debug builds or hidden configuration options. They needed to be **intentional, user-facing choices**.

---

## Variants as User Intent, Not Debug Artifacts

Most projects treat variants as internal artifacts: debug vs release, small vs large, experimental vs stable.

LCC Fusion treats variants as **solutions**.

Each variant exists to solve a recognizable problem. One build might emphasize connectivity, another diagnostics, another minimal footprint. The important point is that variants are not about enabling or disabling random features—they are about matching firmware capabilities to user intent.

This shifts the question from “Which flags do I enable?” to “Which version fits what I’m trying to do?”

That distinction matters. It keeps the project flexible without asking users to become developers.

---

## The Non-Developer Reality

For many embedded projects, usability ends at the source code. If the code is clean and well-documented, the job is considered done.

But for non-developers, the experience doesn’t begin with code—it begins with installation.

If installing firmware requires an IDE, a build environment, or command-line expertise, many users will never make it past the first step. The project may be open, but it isn’t accessible.

That reality drove a key requirement: **users should be able to select and install firmware without building it themselves**.

---

## Firmware That Works the Moment It Boots

Installation is only half the story. What happens after the firmware is loaded matters just as much.

Many devices boot into an unconfigured state. Users must connect, configure, upload data, or perform additional steps before anything useful happens. For developers, this is acceptable. For others, it’s a barrier.

LCC Fusion needed firmware that was **operational out of the box**.

That meant building firmware images that included not just code, but also preconfigured data. Defaults, identifiers, and initial configuration needed to be stored alongside the firmware and delivered as part of the image.

In other words, configuration data became a first-class artifact, not an afterthought.

---

## Documentation as the User Interface

Once firmware variants and configuration data exist, the next question is how to present them to users.

The obvious answer might be filenames or download pages. But those don’t explain *why* variants exist or *how* to choose between them.

Instead, LCC Fusion uses documentation as the interface.

The documentation explains:
- Why variants exist
- What problems each variant solves
- What tradeoffs are involved

From there, users select the firmware that matches their needs—directly from the documentation.

This turns documentation into an active part of the system, not just a reference.

---

## Scaling the Build Process

Once variants exist, manual builds quickly become unsustainable.

Each variant must be built consistently. Each must include the correct configuration data. Each must be placed where the documentation expects it to be. Doing this by hand doesn’t scale.

The solution was to automate the entire process.

The documentation site itself is built using a static site generator. By integrating the firmware build process into that same pipeline, firmware artifacts and documentation are generated together. Variants are declared once, built automatically, and placed into the site structure alongside the documentation that describes them.

This ensures that documentation and firmware never drift apart.

---

## Delivering Firmware Directly From the Docs

The final piece is delivery.

Instead of asking users to download tools or run scripts, firmware is delivered directly from the documentation site. Users connect a USB cable, select the firmware variant they want, and load it onto the device.

No IDEs. No build steps. No ambiguity.

The documentation doesn’t just explain the system—it delivers it.

---

## What This Solves (and What It Avoids)

This approach solves several problems at once:

- Feature growth without exclusion
- User choice without developer burden
- Operational firmware without post-install configuration
- Scalable builds without manual intervention

Just as importantly, it avoids freezing the project’s future. New features can be added, new variants defined, and new use cases supported without breaking existing users or redefining the entire system.

---

## Takeaways

As embedded projects mature, firmware variants are not a sign of failure—they are a sign of growth.

The challenge is not avoiding variants, but **owning them**. By treating variants and configuration data as deliverables, integrating them into documentation, and automating their creation and delivery, it’s possible to remain flexible without becoming inaccessible.

The real constraint isn’t flash or RAM. It’s how much complexity users are asked to absorb.

Designing around that constraint changes everything.
