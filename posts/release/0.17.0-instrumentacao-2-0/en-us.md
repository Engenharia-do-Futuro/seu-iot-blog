![Cover](https://raw.githubusercontent.com/Engenharia-do-Futuro/seu-iot-blog/main/images/seuiot_common/Capa.png)

# Instrumentation 2.0: calibrate sensors seeing the result in real time

**Faster, less error-prone calibration, calibration links (manual and automatic), a new Links page, and the platform now in Spanish.**

**Version:** 0.17.0 | **Date:** 2026-06-19

---

This update brings the biggest leap in sensor configuration since the platform launched: **Instrumentation 2.0**. If you calibrate or linearize sensors, the new screen shows the result of your configuration as you type — no guesswork. And there's more: calibration links to use in the field (including automatic ones when provisioning), a new Links page, a revamped Blog, and full Spanish support.

![Overview of the new Instrumentation 2.0 screen](https://raw.githubusercontent.com/Engenharia-do-Futuro/seu-iot-blog/main/posts/release/0.17.0-instrumentacao-2-0/images/instrumentation_overview.png)

---

## Instrumentation 2.0: configure while seeing the result

We completely redesigned the instrumentation screen. The new form organizes everything into **two methods**, each on its own tab: **Qualification** (classify readings into states) and **Linearization** (adjust the raw reading to the real value). Everything comes with **localized numeric input** (the field respects your language's decimal separator) and charts that show, in real time, how the sensor will respond.

---

### Qualification: turn readings into classifications

The feature formerly called *Quantization* is now called **Qualification** — and it's clearer to use.

**What changed:** Qualification lets you **classify readings** by **threshold bands**. You create a list of bands, and each band has a **name** and a **threshold value**. The rule is simple and unique: *if the reading is **greater than or equal to** (`≥`) the threshold, it gets that band's name*.

How it works in practice:

- Bands are **sorted automatically** (from highest threshold to lowest) and evaluated top to bottom.
- The reading takes the name of the **first band** whose threshold it reaches.
- There is a **"Default"** band (catch-all) that classifies any reading that doesn't reach any threshold.
- A **side timeline** shows the bands visually as you configure them.

To "qualify" a reading is, in a few words, to **give meaning to the raw number**. Instead of just showing `82`, you define bands that translate that value into a readable state.

**Why it matters:** readings become states/classifications that are useful for dashboards and rules, in a far clearer way than looking at loose numbers.

> **Example:** create the **"Critical"** band with threshold `80`, the **"Warning"** band with threshold `60`, and leave the **"Default"** band as "Normal". This way, a reading of `82` becomes **"Critical"**, `65` becomes **"Warning"**, and `40` becomes **"Normal"**.

> **Another example — temperature:** imagine classifying a thermistor reading into heat states. You create the bands **"Very hot"** (`≥ 4000`), **"Hot"** (`≥ 3000`), **"Warm"** (`≥ 2000`), and **"Cold"** (`≥ 1000`), and leave the **"Default"** band as **"Very cold"** (catching everything below that). With this, a reading of `3128` is classified as **"Hot"**, `2400` as **"Warm"**, and `500` as **"Very cold"**. The side timeline shows these bands stacked, from hottest to coldest, as you configure them.

![Qualification tab with bands, thresholds, and side timeline](https://raw.githubusercontent.com/Engenharia-do-Futuro/seu-iot-blog/main/posts/release/0.17.0-instrumentacao-2-0/images/qualification_calibration.gif)

---

### Device-assisted linearization

**Linearization** is the platform's method for converting the sensor's raw reading into the real value, fitting a line to reference points. Now you define those points with **real sensor data**, captured on the spot.

**What changed:** when linearizing, a **"Device readings" mini-chart** shows the values from the selected device. You also get:

- **"Request reading" button**: ask the device to capture a data point **live**, right away, without waiting for a scheduled send.
- **Point selection on the chart**: select **one or more points** (drag to mark a range). When you pick several, the system computes their **average** and **automatically fills in** the comparator value at the linearization point.

**Why it matters:** linearizing becomes faster and more accurate — you use real sensor readings, and the average **reduces the effect of noise** from individual measurements.

**How to use it:**

1. Select the **device** on the instrumentation screen.
2. Click **"Request reading"** to capture a live data point.
3. **Drag** over the desired points on the mini-chart.
4. The **comparator value fills in by itself** (average of the selected points).

![Selecting multiple points on the mini-chart, auto-filling the comparator value](https://raw.githubusercontent.com/Engenharia-do-Futuro/seu-iot-blog/main/posts/release/0.17.0-instrumentacao-2-0/images/linearization_selection_of_points.gif)

---

### Linearization feedback: know if the fit is good

As you add linearization points, the platform **fits a line** and shows a panel with **fit-quality metrics**. Each field means:

- **Calibrated range** — the range of values covered by your linearization points. Readings outside it require extrapolation and may have reduced accuracy.
- **Equation (`y = ax + b`)** — the line fitted by least squares; `a` is the gain and `b` is the offset applied to the reading.
- **R²** — the coefficient of determination, from 0 to 1: the closer to 1, the better the fit. Values below ~0.99 may indicate non-linearity or noise.
- **σ (standard deviation)** — the average dispersion between the points and the fitted line; the smaller, the better.
- **Margin of error (±2σ)** — the maximum expected error in calibrated readings, equal to twice the standard deviation.

**Why it matters:** you know **right away** whether the linearization turned out well, with an **objective** estimate of the error — instead of "guessing" it's right.

![Linearization curve with feedback panel: Equation, R², σ, and Margin of error](https://raw.githubusercontent.com/Engenharia-do-Futuro/seu-iot-blog/main/posts/release/0.17.0-instrumentacao-2-0/images/linearization_calibration_curve.gif)

---

### Different linearization per device

The same base instrumentation can now have **distinct linearizations per device** (variants).

**Why it matters:** sensors of the same type often have unique characteristics and respond differently to the **same environment**. Linearizing individually ensures correct and **comparable** readings across devices.

> **Example:** two identical humidity sensors, installed side by side, report different values in the same spot. With a dedicated linearization for each, both end up reporting the correct value.

![Distinct linearizations per device on the same instrumentation](https://raw.githubusercontent.com/Engenharia-do-Futuro/seu-iot-blog/main/posts/release/0.17.0-instrumentacao-2-0/images/differents_calibrations_per_device.png)

---

## Field calibration: the provisioning link

Whoever calibrates the sensor isn't always the person on the platform. That's why we created a **calibration flow via "magic link"**: you generate a link and the work is done through a **dedicated public page**, without going through the entire platform flow.

Importantly, this public page **opens the same instrumentation tools** — **Linearization** and **Qualification**. In other words, the person in the field performs the real operation (typically **Linearization**, adjusting the points with real sensor readings) and the result becomes a **variant of that device**.

A **modal** on the device screen lets you generate the link and track the sessions in progress.

**Why it matters:** it makes field linearization easier and lets you **delegate the task** to whoever is physically with the device — a technician, a partner, or the customer themselves.

**How to use it:**

1. On the device screen, open the **calibration link generation modal**.
2. Share the link with whoever will do the linearization.
3. Track the **calibration sessions** from the same modal.

![Creating the calibration link and calibrating through the public page via link](https://raw.githubusercontent.com/Engenharia-do-Futuro/seu-iot-blog/main/posts/release/0.17.0-instrumentacao-2-0/images/creating_calibration_link_and_calibration_by_link.png)

---

## New Links page, with text and images

We added a **Links page** to the platform. You can now configure a repository's **automatic calibration links**.

**Why it matters:** sharing resources, instructions, and materials with your team or your customers became clearer and more presentable.

![New repository Links page with text and images](https://raw.githubusercontent.com/Engenharia-do-Futuro/seu-iot-blog/main/posts/release/0.17.0-instrumentacao-2-0/images/pagina_de_links_do_repositorio.png)

---

## Automatic calibration links at provisioning

What if every new device was born with calibration links ready to go? Now it is. You configure it **just once per repository** and, for every new device provisioned via the provisioning link, the platform **creates the calibration sessions on its own** for the instrumentations you chose.

**What it's for:** when you provision many devices — especially in the field — generating a manual link for each one is repetitive. With automatic links, whoever is installing already gets everything ready and **calibrates on the spot**, without anyone needing to open the platform.

**How it works:**

- You define which **instrumentations** get automatic calibration and the **default duration** of the links.
- For every new device provisioned through the provisioning link, the platform creates **one calibration session per selected instrumentation** and generates the corresponding links (each with its own validity).
- Nothing needs to be generated manually for each device.

**How to configure it:**

1. Go to the **Links** page.
2. Click **"Automatic links"**.
3. In the **"Automatic links at provisioning"** modal, select the **instrumentations** that should receive automatic calibration.
4. Set the **default link duration**, in hours (minimum 1; the default is **2 hours**).
5. **Save the configuration**.

From then on, every new device provisioned through the provisioning link is born with calibration links ready.

![Editing the automatic calibration link at provisioning](https://raw.githubusercontent.com/Engenharia-do-Futuro/seu-iot-blog/main/posts/release/0.17.0-instrumentacao-2-0/images/editing_automatic_calibration_link.gif)

---

## The platform now speaks Spanish

SEU IoT now has **full Spanish (es-ES) support**, including **documentation** and **Terms of Use**. A new **language selector with flags** makes switching a single click away.

**Why it matters:** we opened the platform to Spanish-speaking users — more reach for you and for your product.

![Switching the language to Spanish via the flag selector](https://raw.githubusercontent.com/Engenharia-do-Futuro/seu-iot-blog/main/posts/release/0.17.0-instrumentacao-2-0/images/changing_language_to_spanish.gif)

---

## Revamped Blog

The Blog got a nice makeover:

- **Multilingual:** each post can have versions in **Portuguese, English, and Spanish**, and you read it in the language selected on the platform.
- **Dynamic content:** posts are published from a content repository, so **new posts go live without needing a new deploy** of the platform.
- **Share with one click:** copy the post link or share it directly on **LinkedIn**.
- **Search and filters** by category, tags, and date to quickly find what interests you.

![Blog post with tags, share button, and return button](https://raw.githubusercontent.com/Engenharia-do-Futuro/seu-iot-blog/main/posts/release/0.17.0-instrumentacao-2-0/images/blog_post_with_tags_share_and_return_button.png)

---

## SEO and sharing: your links well presented

Behind the scenes, we improved how the platform's and the blog's links appear out there:

- **Nice preview when sharing:** when you paste a post link into social networks or messaging apps, it shows up with the **correct title, description, and image** — the Open Graph tags are now generated **on the server**, including for search-engine crawlers.
- **Per-language versions for Google:** each post signals its PT/EN/ES versions via **hreflang**, so people find the content in their own language.
- **Dynamic sitemap:** the `sitemap.xml` is now generated automatically and **includes the blog posts**, helping indexing.

**Why it matters:** more people find and share the content — and it shows up the right way.

---

## Summary of what's new

| Feature | What changes for you |
|---|---|
| Instrumentation 2.0 | Linearize with real sensor data, see the fit quality (R², σ, error), and qualify readings into states |
| Linearization per device | Dedicated linearization for each device, even on the same base instrumentation |
| Calibration by link | Generate a link and delegate field linearization/calibration |
| Automatic links at provisioning | New devices are born with calibration links ready |
| Links page | Share content with text and images |
| Platform in Spanish | Full es-ES language, with docs and Terms of Use |
| Revamped Blog | Posts in PT/EN/ES, dynamic content, and sharing |
| SEO and sharing | Correct link preview, hreflang, and dynamic sitemap |

---

**It's all live.** Log in to the platform and open the new instrumentation screen to feel the difference when calibrating your next sensor. Then tell us: what got better, and what would you still like to see? **Your feedback guides the next versions.**
