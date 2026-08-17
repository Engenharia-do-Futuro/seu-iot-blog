![Cover](https://raw.githubusercontent.com/Engenharia-do-Futuro/seu-iot-blog/main/images/seuiot_common/Capa.png)

# Seu IoT 1.0: the platform's debut, the way it was always meant to be

**Seu IoT evolved step by step, driven by the needs of each project, but the original idea was always to get here. We rebuilt the platform's entire operating system to support that vision.**

**Version:** 1.0.0 | **Date:** 2026-08-16

---

We've reached version **1.0.0**, and with it, Seu IoT's true debut as it was envisioned from the start. Along the way, the platform evolved to meet the needs of each customer and each project, a feature here, a screen there. But the original idea was always different: to put you in charge of **designing how your system works**, not just registering devices and filling out forms. To get there, we rebuilt the platform's entire **operating system**, and that's the work this post presents.

At the center of it all is the new **Projects** page, a visual board styled like a "technical blueprint" where you create **processes**, connect them with **triggers**, and see each sensor's reading in real time, right on its card. This is the part we're proudest of in this version: building a project became far more dynamic, freer to organize your way, without losing everyday practicality.

![Overview of a project's Blueprint canvas, with processes connected by triggers](https://raw.githubusercontent.com/Engenharia-do-Futuro/seu-iot-blog/main/posts/release/1.0.0-estreia-do-seu-iot/images/blueprint_overview.gif)

---

## Projects: a new way to organize your devices

**Projects** arrive to replace and complement the old Repositories. Each project has a **name**, **description**, **free-form tags** (with automatic suggestions from tags you've already used), and an **icon** chosen from **78 options** organized by theme.

**What you get:**

- **Search and filters:** find projects by name, description, or tag, and filter by any combination of tags you want.
- **Sorting:** by name, creation/edit date, or number of devices.
- **Two views:** cards or table on desktop; always cards on mobile.
- **Contextual help:** a "What is a project?" explanation available both on the empty screen and through a help button, for anyone just getting started.

![Projects page with search, tag filtering, and switching between cards and table view](https://raw.githubusercontent.com/Engenharia-do-Futuro/seu-iot-blog/main/posts/release/1.0.0-estreia-do-seu-iot/images/projects_page_overview.gif)

**Why it matters:** the sidebar menu was reorganized and "Repositories" became a legacy section, shown only to those who still have repositories, which are now also listed right below projects. Nobody loses anything, but the recommended path from now on is the Project.

Linking and unlinking devices also got clearer: a modal separates **"In this project"** from **"Other devices"** (with search), and the device count on the card or table is now **clickable**, opening that modal directly.

![Device linking modal for a project, separating "In this project" from "Other devices"](https://raw.githubusercontent.com/Engenharia-do-Futuro/seu-iot-blog/main/posts/release/1.0.0-estreia-do-seu-iot/images/project_device_link_modal.gif)

Other news on the project page: the address now uses a **friendly name** based on the title (instead of a long code), and there's a new project **settings page**, covering microcontroller, network type, process counters by type, trash, and provisioning/calibration links. All of it translated into **Portuguese, English, and Spanish**.

---

## The Blueprint canvas: the heart of this debut

Here's the biggest news of this version. The project page became a **visual board styled like a "technical blueprint,"** with a cyanotype effect, where you **drag**, **zoom**, and arrange elements however makes the most sense for your process, with no fixed grid, no forced hierarchy.

![Blueprint canvas with zoom and free arrangement of processes](https://raw.githubusercontent.com/Engenharia-do-Futuro/seu-iot-blog/main/posts/release/1.0.0-estreia-do-seu-iot/images/blueprint_canvas_pan_zoom.gif)

**Why it matters:** building a project stopped being about filling out forms in sequence and became about designing how your system works, which makes both creating and reading a project much more intuitive, especially when many processes relate to each other.

### What makes up the board

- **Fixed identification card:** a card in the corner shows the icon, name, creation/edit dates, number of devices, and owner of the project, always visible even as you navigate the board.
- **Comments:** create, edit with simple formatting (**bold**, *italic*, ~~strikethrough~~), move, resize, and delete comments right on the board. The text saves itself when you click away, with an option to undo.

![Creating and editing a comment on the Blueprint, with formatting and autosave](https://raw.githubusercontent.com/Engenharia-do-Futuro/seu-iot-blog/main/posts/release/1.0.0-estreia-do-seu-iot/images/blueprint_comments.gif)

- **Charts as cards:** charts were also adapted for projects, now they're just another type of card, which you place freely on the Blueprint. Choose the processes, the time period, the axis grouping, and the chart type (line, bar, step, area, scatter, or pie), with a live preview as you configure it.
- **Category-colored minimap:** see the whole project in miniature, with each process colored by its category and the connection lines between them also shown.
- **Board search:** search by name, filter by item type, and the view **automatically centers** on the result, useful in projects with many processes.

![Category-colored minimap and search inside the canvas centering the view](https://raw.githubusercontent.com/Engenharia-do-Futuro/seu-iot-blog/main/posts/release/1.0.0-estreia-do-seu-iot/images/blueprint_minimap_search.gif)

- **Loading with personality:** an animated loading screen avoids a blank screen when opening a project.
- **Link Device:** a button in the project header shows linked devices, with search, online/offline status, and approximate location.

![Header "Link Device" button showing devices with status and location](https://raw.githubusercontent.com/Engenharia-do-Futuro/seu-iot-blog/main/posts/release/1.0.0-estreia-do-seu-iot/images/blueprint_link_device.gif)

### What about mobile?

The Blueprint got a version adapted for small screens: a simplified top bar, switching between project info and the minimap, and larger handles for easier touch interaction.

![Blueprint canvas version adapted for mobile](https://raw.githubusercontent.com/Engenharia-do-Futuro/seu-iot-blog/main/posts/release/1.0.0-estreia-do-seu-iot/images/blueprint_mobile.gif)

---

## Process types: creation itself explains how they work

Every process type now has its **own creation screen**, with **animated diagrams** showing how that parameter behaves, no longer a generic form of loose fields. This is the other part we love most about this version: you can understand what you're configuring as you configure it.

![Process creation screen with animated diagrams explaining the parameter](https://raw.githubusercontent.com/Engenharia-do-Futuro/seu-iot-blog/main/posts/release/1.0.0-estreia-do-seu-iot/images/process_creation_animated_diagram.gif)

Processes available in this version:

- **ADC (analog reading):** pin, resolution, attenuation, and number of samples, with diagrams showing the signal conversion and the effect of each parameter on the reading.
- **Digital Read / Digital Write:** turning pins on/off, with diagrams explaining reading noise and the need to amplify the signal (transistor/relay) when writing.
- **Pulse Counting:** counts electrical pulses, with the option to count by rising/falling edge and noise filtering.
- **PWM:** controls intensity (duty cycle) and frequency, with configurable smooth fade.
- **Bit Banging Serial:** reads sensors using a simple serial protocol (data + clock).
- **PID:** Proportional-Integral-Derivative control, with a **live chart** showing how each gain affects the controlled system's response.

![PID configuration screen with a live chart showing the effect of the gains](https://raw.githubusercontent.com/Engenharia-do-Futuro/seu-iot-blog/main/posts/release/1.0.0-estreia-do-seu-iot/images/process_pid_live_chart.gif)

- **Linearization:** converts another process's raw reading into a real unit (e.g., voltage → temperature), automatically calculating the line and equation from calibration points you provide.
- **Qualification:** classifies another process's reading into bands you name (e.g., "low/medium/high").

Three processes in this version are new enough to deserve their own section, right below: **I2C**, **Bit Mask**, and **Timer / Timeout**.

### Catalog, execution, and real-time reading

All types are organized into a **catalog by category** (Peripherals, Events, Data Processing), with search and filtering. Types not yet implemented show a **"coming soon"** badge.

![Process type catalog organized by category, with search, filtering, and "coming soon" badge](https://raw.githubusercontent.com/Engenharia-do-Futuro/seu-iot-blog/main/posts/release/1.0.0-estreia-do-seu-iot/images/process_catalog.png)

- Every process has a **customizable name** (with an automatic "Process N" suggestion).
- A **"Run"** button on the card forces a new execution without needing to reconfigure anything.
- The process card on the canvas shows the **latest reading in real time**, and can switch to a **mini history chart**, with color and icon matching the category.

![Process card on the canvas switching between real-time reading and a mini history chart](https://raw.githubusercontent.com/Engenharia-do-Futuro/seu-iot-blog/main/posts/release/1.0.0-estreia-do-seu-iot/images/process_realtime_card.gif)

- **Automatic conflict detection:** the platform identifies pins/channels already used by other processes, avoiding configuration errors.
- **Visual confirmation:** the system now shows when the device has actually applied a created or edited process, instead of leaving you with no feedback.

On mobile, the process creation screen is **simplified**, just the parameter table, without the animated diagrams.

---

## I2C: a brand-new communication protocol

**I2C** is the most original process in this version: a communication protocol new to Seu IoT, built from scratch to talk to sensors and peripherals that use this bus, very common in temperature, humidity, and pressure sensors, accelerometers, displays, and countless other modules.

The implementation ships as four processes: **Channel** (defines the bus and the data/clock pins), **Read**, **Write**, and **Scan**. Like the other processes in this version, the configuration screen comes with diagrams explaining how the bus works.

![I2C channel configuration with a bus diagram](https://raw.githubusercontent.com/Engenharia-do-Futuro/seu-iot-blog/main/posts/release/1.0.0-estreia-do-seu-iot/images/process_i2c_channel.gif)

**Scan** works like a "scanner": it sweeps the bus and shows, in an address grid, which I2C devices are responding, useful both for checking wiring and for discovering a new sensor's address before configuring Read.

![I2C Scan showing the address grid of devices connected to the bus](https://raw.githubusercontent.com/Engenharia-do-Futuro/seu-iot-blog/main/posts/release/1.0.0-estreia-do-seu-iot/images/process_i2c_scan.gif)

**Why it matters:** I2C opens the door to a much larger family of sensors compatible with Seu IoT, including ones that pack several pieces of data into a single chip, which ties directly into the next feature.

### Bit Mask: separating what comes bundled in the same data

Many I2C sensors return **more than one piece of information in a single value**, for example, some bits of the data represent the reading itself, and other bits represent a status flag or a second quantity. **Bit Mask** was created specifically to handle this scenario: a process that **extracts a specific part** of a value read by another process, isolating just the bits that matter.

![Bit Mask configuration extracting part of a value read via I2C](https://raw.githubusercontent.com/Engenharia-do-Futuro/seu-iot-blog/main/posts/release/1.0.0-estreia-do-seu-iot/images/process_bitmask.gif)

**Why it matters:** without this process, you'd need to handle the raw data outside the platform to separate what comes mixed into a single value. With Bit Mask, that separation happens right inside the Blueprint.

> **Example:** an I2C sensor returns a 16-bit value where the 12 lowest bits are the temperature reading and the 4 highest bits are a status code. Set up two Bit Masks over the same I2C Read, one isolating the 12 temperature bits, the other isolating the 4 status bits, and treat each one as an independent process in your project.

---

## Timer / Timeout: sampling became a process

In Repositories, the sampling rate, how often a sensor is read, was configured **inside each process**: ADC, Pulse Counting, Digital Read, and Bit Banging Serial, each with its own interval field, isolated from the others.

Now there's a dedicated process for this: **Timer / Timeout**. You configure the interval once (days, hours, minutes, or seconds) and **connect that Timer, via a trigger, to one or more processes** that should be triggered by it. The Timer's card shows a **visual countdown** to the next trigger.

![Timer process configured with a countdown, connected to other processes via triggers](https://raw.githubusercontent.com/Engenharia-do-Futuro/seu-iot-blog/main/posts/release/1.0.0-estreia-do-seu-iot/images/process_timer_triggers.gif)

**Why it matters:** the same sampling rhythm becomes **reusable** across multiple processes, instead of repeated in each one, and it's clearly visible on the Blueprint which processes are triggered by which Timer.

> **Example:** a 30-second Timer connected to three different processes, a temperature ADC, a door sensor's Digital Read, and an I2C Scan. All three run together, at the same pace, without repeating the timing configuration in each one.

---

## ESP32-S3: the first supported device variant

Until now, every project on Seu IoT was built around a single reference hardware: the original ESP32. This version brings the platform's **first supported device variant**: the **ESP32-S3**.

On the project settings page, you define **which device model** that project targets, ESP32 or ESP32-S3. Based on that choice, process configuration screens now respect the **correct pin limits for that model**, preventing you from configuring a pin that doesn't exist or is already reserved on the board.

![Project configuration defining the device model, ESP32 or ESP32-S3](https://raw.githubusercontent.com/Engenharia-do-Futuro/seu-iot-blog/main/posts/release/1.0.0-estreia-do-seu-iot/images/esp32_s3_project_config.png)

And it's not just configuration: it's now also possible to **flash firmware onto ESP32-S3 devices** through the platform's installation flow, the same way it already worked with the ESP32.

![Flashing firmware onto an ESP32-S3 device through the installation flow](https://raw.githubusercontent.com/Engenharia-do-Futuro/seu-iot-blog/main/posts/release/1.0.0-estreia-do-seu-iot/images/esp32_s3_flashing.gif)

**Why it matters:** it's the first step on a bigger path, supporting different hardware variants within the same project and the same flow, so you don't need to learn a different platform for every board.

---

## Triggers: connect processes with a stroke

You can **connect processes to each other** by drawing a line from one card's output to another's input, for example, a **pulse count** triggers a **PWM**.

![Drawing a connection between two processes on the canvas, creating a trigger](https://raw.githubusercontent.com/Engenharia-do-Futuro/seu-iot-blog/main/posts/release/1.0.0-estreia-do-seu-iot/images/triggers_connecting.gif)

- An **arrow** shows the direction of the flow; the line uses a **color gradient** between the source and destination categories.
- The system warns you when you try to **click** instead of **drag** to create the connection.
- When you delete a process, its associated connections **disappear automatically**.

**Why it matters:** it's the piece that turns a set of isolated processes into a real automation, all drawn out, all visible, without needing to open a separate form to configure "if this, then that."

> **Example:** connect a **Pulse Count** from a flow sensor to a **PWM** that controls a pump, so the pump's intensity automatically responds to the measured flow, all visible as a line between the two cards on the Blueprint.

---

## Navigation and general usability

A series of tweaks make the platform smoother day to day:

- Several buttons and cards that used to only navigate on click became **real links**, so you can open them in a new tab with a right-click or Ctrl/Cmd+click.
- **Reorganized sidebar menu** into groups (Overview, Organization, Monitoring, Devices, System), with updated icons.

- New device-linking **"hub" screen**, bringing Install / Connect / Provisioning Links together in one place, with an animated preview of each step.
- **Redesigned Welcome page:** cards for recent projects and dashboards, a numbered step-by-step quick guide, a mini blog with the latest posts, and a clickable storage card.

- New **favicon** (browser tab icon).
- **"Back to site"** button in the platform header.
- Option to link a device with **"no project and no repository"** when installing or editing it.

---

## Other news in this version

A few improvements that came along, in areas separate from what we covered above:

- **Isolated credentials on MQTT:** each device now has its own login on the MQTT broker, the channel it uses to exchange data with the platform, restricted by an **ACL** (access control list) to only that specific device's topics. That credential continues to renew automatically every day, as it already did before, but it's now unique per device. In practice, this isolates the risk of a physical breach: if someone extracts a device's credentials, they only get access to that device's data, and every other device's communication channels stay protected.
- **SSL on HTTP and MQTT WebSocket:** communication is now encrypted on these channels, with no visible change on screen, but more security.
- **Feedback channel:** a new form for you to send feedback directly through the platform.

- **Blog with cover images:** blog listing cards now show the post's cover image, with a default image when none is set.

---

## Summary of what's new

| Area | What changes for you |
|---|---|
| Projects | New concept with name, description, tags, icon, search, filters, and sorting |
| Blueprint canvas | The project becomes a visual board: drag, zoom, comment, use the minimap, search, and charts as cards |
| Process types | Dedicated screens with animated diagrams and a catalog by category |
| I2C and Bit Mask | New communication protocol, with Channel, Read, Write, and Scan; extract parts of a read value |
| Timer / Timeout | Sampling became a dedicated process, triggering other processes |
| ESP32-S3 | First supported device variant, with its own pin limits and flashing |
| Triggers | Connect processes by drawing a line, with an arrow and color gradient |
| Security | Per-device exclusive MQTT credentials (ACL) and SSL on HTTP and MQTT WebSocket |
| Feedback | Feedback form directly in the platform |

---

**It's all live.** Open a project and see the Blueprint for the first time, create a process, watch the animations explaining each parameter, and connect two processes with a trigger. It's the version we've always wanted to deliver, and now it finally exists. Tell us what you think: **your feedback guides the next versions.**
