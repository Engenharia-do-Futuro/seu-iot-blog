![Cover](https://raw.githubusercontent.com/Engenharia-do-Futuro/seu-iot-blog/main/images/seuiot_common/Capa.png)

# Seu IoT 1.1: your data on any screen, and connected to the rest of the world

**A new data visualization hub, tables and maps that span projects, online/offline status for every device, an open API with widgets you can paste into your website, and connection to AI assistants. All under your control.**

**Version:** Platform 1.1.0 | Firmware 2.0.1 | **Date:** 2026-10-13

---

The previous 1.0 release brought Blueprint and a way to **build** how your system works. **1.1** is about what comes next: **seeing what your system is producing** and **taking that data wherever you need it**.

There were three fronts of work:

1. **Data visualization:** new chart types, indicators (KPIs), gauges, tables and maps, and a completely redesigned chart creation screen.
2. **Device connection state:** the platform now records when each device went online and offline, and that becomes data for charts.
3. **Integrations:** an open API for third-party systems, widgets you paste into any page, and access for AI assistants (Claude, Cursor, Gemini CLI and others) via MCP.

Alongside the platform, **firmware 2.0.1** fixes editing processes directly on the device and lets you chain an I2C read into an I2C write.

![Overview of a panel with the new chart types side by side](https://raw.githubusercontent.com/Engenharia-do-Futuro/seu-iot-blog/main/posts/release/1.1.0-visualizacao-de-dados-e-integracoes/images/dashboard_overview.gif)

---

## A new screen for creating charts

Before getting to the charts themselves, here is the change that supports them: chart creation now has its **own screen**, with the type selection (**Line chart, Composition, Indicator, Gauge, Container, Heatmap, Table and Map**) and a **live preview** while you configure. It is the same screen, with the same options, both inside a **project (Blueprint)** and in the **panel**.

![Choosing the chart type with the live preview](https://raw.githubusercontent.com/Engenharia-do-Futuro/seu-iot-blog/main/posts/release/1.1.0-visualizacao-de-dados-e-integracoes/images/chart_creator_catalog.gif)

**Why it matters:** in the panel, a chart can now gather **signals from several projects and devices** in one place. Before, each panel chart was tied to a single source. An operations panel no longer needs one chart per project: it can compare what is happening in all of them.

The panel also gained a **Fullscreen** mode, designed to stay open on a TV or a control-room monitor.

![Panel in fullscreen](https://raw.githubusercontent.com/Engenharia-do-Futuro/seu-iot-blog/main/posts/release/1.1.0-visualizacao-de-dados-e-integracoes/images/dashboard_fullscreen.png)

---

## New chart types

### Indicators (KPIs): from the last value to real statistics

The **Last value** indicator now shows the **unit of measurement** (e.g., "23.5 °C"), and it has company: there are **14 indicator (KPI) types**, organized into groups (Reading, Trend & comparison, Period statistics, Normal range, Fleet & accumulated), each with an explanation and an example in the type catalog.

![Indicator type catalog, with an example of each one](https://raw.githubusercontent.com/Engenharia-do-Futuro/seu-iot-blog/main/posts/release/1.1.0-visualizacao-de-dados-e-integracoes/images/kpi_type_catalog.gif)

| Indicator type | What it shows |
|---|---|
| Last value | The last reading received |
| Period statistic | Average, minimum, maximum or count of readings over the card's period |
| Comparison with target | The last reading against a target value you define |
| Simple trend arrow | Whether the value is going up or down |
| With last reading time | The reading with "3 min ago" next to it |
| % of samples within normal range | How much of the period stayed within what is expected |
| Comparison with previous period | The current period against the previous one (hour, day, week, month or year) |
| Percentile (p90/p95) | The value that ignores rare spikes |
| Standard deviation/variability | How much the reading fluctuates |
| Out-of-range count | How many times the value left the normal range |
| Cycle/execution count | How many times the process published a reading |
| Simple projection (linear extrapolation) | Extrapolates the trend and estimates when the limit will be reached |
| Fleet ranking | The device's position compared to the others in the project |
| Calculated accumulated consumption | Running total over time (e.g., kWh) |

You choose what to show along with the value: time, device, location, process, operator and customer.

> **Example:** the "% of samples within normal range" indicator for a lab freezer shows "92% within range (7 days)". At a glance you know whether the equipment is behaving, without opening any chart.

### Gauge and container: see the level, not just the number

Two new ways to show **a value within a scale** (minimum and maximum), with **color bands** that change as the value crosses each limit:

- **Gauge:** in the **Speedometer, Full ring, Half ring and Quarter ring** styles.
- **Container:** the level really fills up, in nine shapes: **Tank, Silo, Horizontal tank, Open box, Hopper, Gas cylinder, Barrel, Loading bar and Battery**.

The color can be in **blocks** (it changes as it crosses each limit) or a **continuous gradient** between the bands.

![Gauge and container with color bands, changing color as they cross the limits](https://raw.githubusercontent.com/Engenharia-do-Futuro/seu-iot-blog/main/posts/release/1.1.0-visualizacao-de-dados-e-integracoes/images/gauge_and_container.gif)

![Gallery of container shapes](https://raw.githubusercontent.com/Engenharia-do-Futuro/seu-iot-blog/main/posts/release/1.1.0-visualizacao-de-dados-e-integracoes/images/container_shapes.gif)

> **Example:** a reservoir's level as a Tank, green above 40%, yellow between 20% and 40%, red below 20%. Anyone walking past the screen understands the state without reading a single number.

### Heatmap (calendar)

**One value per day** painted on a calendar, GitHub-contributions style. Choose the **aggregation** (**Average, Sum, Count, Max or Min**) and the **calendar period** (**Month or Year**). More intense days are darker, and the tooltip shows the date, the value and how many samples went into the day. There are buttons to go to the previous period, the next one, and back to today.

![Heatmap switching between Average and Count](https://raw.githubusercontent.com/Engenharia-do-Futuro/seu-iot-blog/main/posts/release/1.1.0-visualizacao-de-dados-e-integracoes/images/calendar_heatmap.gif)

**Why it matters:** patterns that go unnoticed in a months-long line chart (like "every Monday consumption spikes") become obvious on a calendar.

### Histogram

Among the **Composition** styles (Pie, Treemap, Horizontal bar and Histogram), the **Histogram** shows the **distribution** of a process's values over a period: how many readings fell into each range. The **Number of bins** can be **Automatic (Sturges' rule)** or fixed, and there is a gradient from the first to the last bin. Changing the period recalculates everything.

![Composition styles](https://raw.githubusercontent.com/Engenharia-do-Futuro/seu-iot-blog/main/posts/release/1.1.0-visualizacao-de-dados-e-integracoes/images/composition_types.gif)

![Histogram changing the number of bins and the period](https://raw.githubusercontent.com/Engenharia-do-Futuro/seu-iot-blog/main/posts/release/1.1.0-visualizacao-de-dados-e-integracoes/images/histogram.gif)

### Line and area colored by value band

The stroke of the line or area chart **changes color** as the value crosses the bands you defined (green, yellow, red), in blocks or as a gradient. Just look at the line to know when, and by how much, the value left what is expected.

![Line chart changing color as it crosses the configured bands](https://raw.githubusercontent.com/Engenharia-do-Futuro/seu-iot-blog/main/posts/release/1.1.0-visualizacao-de-dados-e-integracoes/images/colored_line_by_band.gif)

### Reference lines

Fixed annotations over the chart, independent of the data: a **horizontal** line (an operating limit), **vertical** (a cutoff time) or **slanted**, between two points. Each one has a **label, color and style** (solid, dashed, dotted or dash-dot).

![Horizontal reference lines on a chart](https://raw.githubusercontent.com/Engenharia-do-Futuro/seu-iot-blog/main/posts/release/1.1.0-visualizacao-de-dados-e-integracoes/images/reference_lines.gif)

### Tweaks to existing charts

- **Bar chart:** the bar width now adapts to narrow cards and many points, without spilling outside the chart, and the first and last bars are no longer cut off at the edges.
- **Calibration charts:** they now show the last **15 points** instead of 80, which ended the unreadable "sea of points". Dragging to select and calculate the average still works even if the mouse leaves the chart area. The reading in focus in the list is highlighted on the regression chart, and values never appear in scientific notation.
- **Tooltips and axes** with more readable colors in both light and dark themes, and the Y axis adjusts to the real width of the numbers.

---

## Tables and maps that span projects

This is the change that most expands what the panel can do. Until now, a chart or data widget pointed to **one** project. Now you define a **device rule** (with the **Add rule** button) and the platform resolves, on every load, which devices are included, no matter which project they belong to.

The rule can filter by:

- **Project** and **repository**
- **Personna** (operator and customer)
- **Models** (e.g., only ESP32-S3)
- **Online only:** devices with a reading in the last 24 hours
- **Geographic area:** a circle on the map, with a center and a **Radius (km)** that you drag

### Configurable table

One row per device, and **you choose the columns** (**Add column**). The first is always the device; the others can be of five types:

- **Identity:** Local IP, Public IP, Project, Status, Model, Operator, Customer and Location.
- **KPI:** any of the 14 indicator types, calculated for each device.
- **Gauge:** the gauge inside the cell.
- **Chart:** the recent trend in a small chart with no axes.
- **Action:** a button, switch, slider or text field that **runs the process on that device**, straight from the table row. The button for a reading is **Read now**.

![Device table with Identity, KPI, Gauge, Chart and Action columns](https://raw.githubusercontent.com/Engenharia-do-Futuro/seu-iot-blog/main/posts/release/1.1.0-visualizacao-de-dados-e-integracoes/images/table_widget.gif)

When you click a row's operator, customer or location, a tooltip shows the **contact details**, with shortcuts to copy, send an email, open WhatsApp or open in Google Maps.

> **Example:** a "Cold rooms" table gathering all of customer X's devices across 5 different projects: online status, current temperature with a gauge, the trend over the last few hours, and a button to force a new reading. All on one screen, without entering any project.

### Map with values on the markers

The **Map** uses the same device rule. Each pin shows **informational data** that you configure (indicators, gauges and charts). **The pin's color comes from the primary informational data**, which must be a gauge and is marked with the star (for example, red on devices above the temperature limit), and the tooltip shows the other data when you click the device. Above each pin you can also toggle the device name, the operator, the customer and the time.

![Device map with pins colored by the primary data and a tooltip with the informational data](https://raw.githubusercontent.com/Engenharia-do-Futuro/seu-iot-blog/main/posts/release/1.1.0-visualizacao-de-dados-e-integracoes/images/geo_map_values.gif)

Table and map also work **inside a project's Blueprint**, now as one more card type. The map now uses **OpenStreetMap**, no longer depending on a tile provider that started requiring an API key.

---

## Online and offline: each device's connection history

Until now the platform knew **whether** a device was online. Now it also knows **when** it connected and disconnected. The MQTT broker now reports each event, and Seu IoT keeps the history.

The status is updated **in real time** in device lists and modals, with no need to reload the page.

![Device list with the online/offline status changing in real time](https://raw.githubusercontent.com/Engenharia-do-Futuro/seu-iot-blog/main/posts/release/1.1.0-visualizacao-de-dados-e-integracoes/images/device_live_status.gif)

And most importantly: connectivity becomes a **signal like any other** in your charts, tables and maps, in the **Connectivity** group when choosing the signal. There are four variations:

| Signal | What it shows |
|---|---|
| Connection state | 1 when connected, 0 when disconnected, one point per event |
| Disconnect count | How many times the device dropped |
| Time connected | Accumulated seconds online |
| Time disconnected | Accumulated seconds offline |

![Chart of a device's connection state over the course of the day](https://raw.githubusercontent.com/Engenharia-do-Futuro/seu-iot-blog/main/posts/release/1.1.0-visualizacao-de-dados-e-integracoes/images/connection_state_chart.gif)

**Why it matters:** answering "is this sensor dropping a lot?" becomes a matter of reading a chart or a table column (the week's disconnect count, or the percentage of time online), not of digging through logs.

---

## Storage: per-project recycle bin

The **recycle bin** now also applies to **project** data. You can move a device's data from a project to the recycle bin, restore it, or delete it for good, and your plan's automatic cleanup rule now takes care of both repository and project data. Connection events are also part of that cleanup.

The storage usage card shows consumption **summing repositories and projects**, and whatever is in the recycle bin no longer appears in charts, in live readings or in the device's "last message".


---

## Automatic publishing of processes

For a process to appear in charts, it needs to **publish** its result on every execution. Now that is a click away:

- An **envelope icon** on the process card turns **Automatic publishing** on and off (the icon says "click to disable" or "click to enable").
- In the **project settings**, the **Automatic publishing by default** option defines whether **new processes are born publishing** (yes, by default). Created processes really do inherit this default.
- The button that toggles between the value and the mini chart is **disabled, with an explanation**, when the process doesn't have any data to plot yet.

![Envelope icon on the process card and the Automatic publishing by default option in the project settings](https://raw.githubusercontent.com/Engenharia-do-Futuro/seu-iot-blog/main/posts/release/1.1.0-visualizacao-de-dados-e-integracoes/images/publish_on_execute.gif)

---

## Open API: your data in third-party systems

Your data can now be read by **systems that don't have a Seu IoT account**, without exposing your login and without opening up the whole project.

This is done through **API contracts**, created in the project settings. A contract is a **limited view** of the project: you choose **which processes** (and, if you want, which devices) it can see. Each contract delivers:

- **HTTPS key:** to query history and the current value.
- **MQTT/WS credential (real-time):** to receive values **in real time**, as soon as the device publishes, without having to keep asking.
- **Embeddable widgets** (see below).

![Creating an API contract by choosing the scope's processes and devices](https://raw.githubusercontent.com/Engenharia-do-Futuro/seu-iot-blog/main/posts/release/1.1.0-visualizacao-de-dados-e-integracoes/images/api_contract_creation.gif)

**Security and control:**

- You can **revoke, reactivate, regenerate credentials, set when the contract expires and edit the scope** at any time.
- The key and password are shown **once**, at the moment they are generated.

**Usage tracking:** the contract list shows the **API (30 days)** and **Widgets (30 days)** columns, and the **View usage** button opens the **per-day** breakdown (days in UTC-0) of API requests and widget reads. The limit is 60 requests per minute per contract. Real-time data (MQTT) doesn't count toward the limit, and that is why it is the recommended path for anyone who wants "live" data.

![A contract's daily usage](https://raw.githubusercontent.com/Engenharia-do-Futuro/seu-iot-blog/main/posts/release/1.1.0-visualizacao-de-dados-e-integracoes/images/api_contract_usage.png)

The **Help Center** gained an **API documentation** page, with the description of the routes, the data format, code examples and best-practice guidance, and the examples and images live in a public examples repository.

![API documentation page in the Help Center](https://raw.githubusercontent.com/Engenharia-do-Futuro/seu-iot-blog/main/posts/release/1.1.0-visualizacao-de-dados-e-integracoes/images/api_docs_page.png)

### Widgets to paste into your website

Want to show your greenhouse's temperature on your company's page, without writing a line of integration? From a contract, you create a **widget**: you choose the signal (within what the contract allows), the chart type and the look, see the result in a **preview** and copy the **Embed code**, a ready-made `<script>` to paste into the site.

The widget **updates itself** in real time and supports the most commonly used chart types: line charts, gauges, containers, indicators, heatmap, histogram and others.

![Seu IoT widget running on an external HTML page](https://raw.githubusercontent.com/Engenharia-do-Futuro/seu-iot-blog/main/posts/release/1.1.0-visualizacao-de-dados-e-integracoes/images/widget_embedded_external_page.gif)

**Why it is safe to paste:** the public page **never receives the contract key**. Each widget has its **own** credential, limited exactly to the signals it shows, and which you can **revoke individually** without affecting the rest. Revoked? The page that already had the code starts showing "widget disabled by its owner", with no need for you to touch the site. You can also regenerate the embed code, which makes the old `<script>` stop working.

---

## Connect an AI to Seu IoT (MCP)

Seu IoT can now be operated by **AI assistants** (Claude, Cursor, Gemini CLI and any client compatible with the **MCP** protocol). The AI becomes one more interface over your account: it **sees only the projects you allow** and **does only what you permit**.

You ask, in natural language, things like "list the offline devices in the Greenhouse project", "create a calendar chart of last month's temperature" or "set up the I2C read for this sensor", and the AI does the work.

### You decide what the AI can do

When connecting, Seu IoT opens the **Authorize access to your account** screen: you choose the **projects** and, in a permissions table, what the app can do. Each permission has two options: **Allow** and **Ask for my confirmation**. At the end, **Authorize** or **Deny**.

| Permission | The AI can |
|---|---|
| View projects | List projects, devices (online/offline), processes, triggers and charts |
| Read data | Query samples and summaries (minimum, maximum, average, p95, by hour/day/week/month) |
| Edit allowed projects | Create and edit processes, triggers, charts and card positions |
| Create new projects | Create new projects |
| Delete processes and links | **Ask** to delete processes, triggers and charts |
| Create access codes | **Ask** for API contracts, embeddable widgets and the first access key |
| Run processes (play) | Run a process right now, like the play button |

![Authorize access to your account screen, with the permissions table and project selection](https://raw.githubusercontent.com/Engenharia-do-Futuro/seu-iot-blog/main/posts/release/1.1.0-visualizacao-de-dados-e-integracoes/images/ai_consent_screen.gif)

**What the AI never does:** delete projects or devices, delete collected data, rotate keys or touch billing and administration. That always stays with you, on the platform.

### Approvals and transparency

- When an action requires confirmation, **nothing is changed** until you approve. The pending item shows up in the **Notifications** bell, with the **before and after** of what would be done.
- **Keys and tokens always require your approval.** And you choose whether the credential goes **straight to the AI** (which retrieves it a single time, within 15 minutes) or whether **only you see it**.
- In **Configuration > Connected apps** you keep track of each app, **widen or narrow** its permissions on the spot and **revoke** with one click.
- The **"What this app did"** button shows the history of everything the app read and wrote (including what was refused), never displaying credentials.

![Approval queue in Notifications, with the before and after of a change proposed by the AI](https://raw.githubusercontent.com/Engenharia-do-Futuro/seu-iot-blog/main/posts/release/1.1.0-visualizacao-de-dados-e-integracoes/images/ai_proposal_review.gif)

![Connected apps screen with the "What this app did" history](https://raw.githubusercontent.com/Engenharia-do-Futuro/seu-iot-blog/main/posts/release/1.1.0-visualizacao-de-dados-e-integracoes/images/ai_connected_apps.gif)

### An AI that doesn't have to guess

The AI receives **documentation inside the protocol itself**: for each process type (ADC, PWM, I2C, PID and the others) and each chart type, it looks up the **valid parameters, the data format and ready-made examples**, including the correct pins and channels for the project's board (ESP32 or ESP32-S3). It can also run a **dry run** (validation without creating anything) before proposing a change, and look up **which pins are free**.

**Why it matters:** less trial and error, fewer useless approvals in your queue, and correct results from the very first proposal.

> **Example:** you ask "create a process that writes to the I2C display the value read by the sensor". The AI looks up the operation sheets, checks the free pins, validates the dry run and only then sends **one** proposal for you to approve, with all the right parameters.

---

## Firmware 2.0.1

Two changes on the device (processes and the platform work with the previous firmware, but these features depend on the update):

- **Editing a process now actually updates the device.** Before, when you changed the parameters of an already created process, the device re-ran the process but kept using the old configuration. Now it starts using the new parameters immediately.
- **I2C Write triggered by a trigger.** When an **I2C Write** is triggered by another process (for example, an I2C Read or a calculated value), the received data **becomes the content sent to the chip**. Numbers are converted into bytes at the width you configured (e.g., 65281 → `FF01`), and hexadecimal text is sent as is. The trigger's value applies **only to that execution** and never overwrites what is saved in the process.

> **Example:** a PID process calculates the power and, via a trigger, feeds an I2C Write that adjusts a digital-to-analog converter, all designed in Blueprint.

---

## Other improvements

- **Bit Banging Serial:** the data pin (DT) was not being sent correctly to the device, which ended up always reading on pin 0. Fixed, and the card now shows the **DT/SCK** pins in the same style as the I2C SDA/SCL pins.
- **More stability in Blueprint:** when you return to the browser tab, the screen no longer overwrites a change you just made to comments, charts, processes and triggers.
- **Calibration layout on mobile:** the Linearization and Qualification areas no longer "collapse" on small screens.
- **Notifications:** it is now possible to open each notification's **details** in a window.
- **Support:** a new flow to **open a support ticket** straight from the platform.
- **Login:** after signing in, you go back to the page you were trying to reach.
- **Blog:** each post now shows its **author**, and the table of contents also appears in the search-engine and social-media versions.

---

## Summary of what's new

| Area | What changes for you |
|---|---|
| Chart creation | Dedicated screen with type selection and preview; panels with signals from several projects; Fullscreen mode |
| New charts | 14 indicator types, gauge, container, heatmap, histogram, line/area by band and reference lines |
| Tables and maps | Device rule across projects; Identity, KPI, Gauge, Chart and Action columns; map with informational data |
| Connection | Online/offline history, real-time status and four connectivity signals for charts |
| Storage | Per-project recycle bin and combined usage of repositories and projects |
| Automatic publishing | Envelope icon on the process and a per-project default |
| Open API | API contracts with key, real-time MQTT, usage tracking and documentation |
| Widgets | Embed code to paste into any site, with its own credential and revocation |
| AI via MCP | AI assistants with permissions, approvals, auditing and built-in documentation |
| Firmware 2.0.1 | Process edits applied on the device and I2C Write triggered by a trigger |

---

**It's all live.** Create an indicator, a gauge or a heatmap, build a table with devices from several projects, open an API contract and paste a widget into your site, or connect your favorite AI and ask it to build something for you. Also update your devices' firmware to **2.0.1**. Tell us what you think: **your feedback guides the next versions.**
