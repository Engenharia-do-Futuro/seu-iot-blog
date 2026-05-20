![Cover](https://raw.githubusercontent.com/Engenharia-do-Futuro/seu-iot-blog/main/images/seuiot_common/Capa.png)

# What's New: Bluetooth Configuration, Personnas, and Provisioning Links

**Date:** May 2026 | **Version:** Post v0.15.0

---

This update brings major changes to how you configure and distribute devices. If you use Seu IoT to manage field sensors, install devices for clients, or scale your operations — this release was made for you.

---

## Configure devices via Bluetooth, directly from your browser

Previously, connecting a new device to the platform required AP mode: connecting to the device's own Wi-Fi network, opening a configuration page, typing in network credentials — a tedious process, especially in the field.

**Now you can configure any device via Bluetooth, right from your browser**, without switching Wi-Fi networks or installing any app.

### How it works in practice

1. Open the device configuration page in Seu IoT
2. Click **Connect via Bluetooth**
3. Select the device from the browser's device list
4. The system automatically detects the firmware version, MAC address, and current status
5. Choose the Wi-Fi network, select the repository the device will belong to, and you're done

The connection is **encrypted** — the device firmware and the server exchange security keys before any configuration is sent, so your Wi-Fi credentials travel safely.

> Example: you arrive at a client site with 5 new devices. Instead of connecting to each device's AP separately, you handle everything from your laptop screen via Bluetooth, without ever leaving the platform.

---

## Personnas: link devices to clients and operators

A practical need emerged for those managing devices across multiple clients: **who is responsible for that device? Which client is it associated with?**

The new **Personnas** section solves this. A Personna is a person or company profile that you link to your devices.

### What you can register in a Personna

- Full name or company name
- CPF, CNPJ, or Tax ID (for international clients)
- Full address (street, number, neighborhood, city, state, ZIP code)
- Contacts: email, phone, or WhatsApp
- Role: **customer** (the end user of the device) or **operator** (the person who maintains it)

### What it's good for

- You install a temperature sensor at a client's factory → register the client as a Personna and link it to the device
- If you need to call them about maintenance, their contacts are right there
- You can see, directly in the devices table, which client is associated with each device

---

## Provisioning Links: let your client configure their own device

This is one of the most powerful features in this release. You can **generate a link or QR Code** and send it to your client. When they open the link, a guided flow appears so they can connect the device to the platform themselves — **without needing a Seu IoT account**.

### Why this matters

Think of a distributor that ships 200 sensors a month. Before, a technician had to configure each one. Now, the client receives a link, opens it on their phone or laptop, and completes the Bluetooth setup in minutes.

### Controls you have when creating a link

- **Link name** — so you can identify which campaign or client it belongs to
- **Target repository** — which project the devices will be added to
- **Usage limit** — how many devices can be configured using the link
- **Expiration date** — the link can expire on a specific date
- **Automatic Personna association** — the client fills in their own details during the flow and gets registered automatically

Each link automatically generates a **QR Code** that you can print, put on product packaging, or send by email.

> Example: you close a deal with 50 units. You create a provisioning link with a limit of 50 uses and a 30-day expiration. You send the link to your client. They configure devices at their own pace, and everything lands in the correct repository in your account.

---

## Device location map

During Bluetooth configuration, the browser now **captures the geographic location** (with the user's permission) and saves the device's coordinates.

On the devices page, you can **switch to map view** and see where each device is installed. Nearby devices are automatically clustered on the map for easier visualization.

> Useful for those with devices spread across multiple cities or regions — you can see at a glance whether any area has more offline devices, for example.

---

## More reliable firmware flashing

An important fix: before writing firmware to the device, the flash memory is now **fully erased first**. This resolves cases where the device was left in an inconsistent state after an update, especially when a previous write had been interrupted.

---

## Full platform documentation

The platform now has **official documentation** available in both Portuguese and English, accessible from the Help menu. It covers everything from connecting your first device to using dashboards, calibrating sensors, and understanding data storage rules.

---

## Summary

| Feature | What changes for you |
|---|---|
| Bluetooth configuration | Configure devices from the browser, no AP mode needed |
| Encrypted communication | Your Wi-Fi credentials are transmitted securely |
| Personnas | Associate clients and operators with each device |
| Provisioning Links | Send a link/QR Code so clients can configure devices themselves |
| Device map | See where your devices are installed |
| Flash erase before write | More reliable firmware flashing |
| Documentation | Complete platform guide in PT and EN |
