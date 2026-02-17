# WT32-ETH01 MQTT Client Node Setup

This repository includes a basic setup for an MQTT client node that communicates over TCP using the **WT32-ETH01 (ESP32 + Ethernet)** module.

The following guide explains how to place the WT32-ETH01 into **programming mode** so you can flash firmware.

---

## Entering Programming Mode (WT32-ETH01)

Putting the WT32-ETH01 into programming mode can feel confusing the first time, but once you've done it once, it becomes straightforward.

---

## Required Hardware

You will need a **USB-to-TTL serial programmer**.

Example used for this project:
- Waveshare USB to RS232 / RS485 / TTL Converter

Any reliable 3.3V-compatible USB-to-TTL adapter should work.

---

## Wiring the WT32-ETH01 for Programming

### Power Connections

- **5V → Pin 12** (WT32-ETH01)
- **GND → Ground rail**
- Also connect **GND → Pin 11**

> ⚠️ Ensure your programmer and power supply share a common ground.

---

### UART Connections

- **Programmer RX → WT32-ETH01 TX0**
- **Programmer TX → WT32-ETH01 RX0**

> TX and RX must be crossed.

---

### Boot Mode Jumper

To enter flashing mode:

- Connect **Pin 24 (IO0)** to **Pin 23 (GND)** using a jumper wire.

This forces the ESP32 into bootloader mode on reset.

---

## Enter Programming Mode

1. Ensure IO0 (Pin 24) is connected to GND (Pin 23).
2. Briefly touch **Pin 1 (EN)** to GND to reset the module.
3. Remove the IO0-to-GND jumper.

The WT32-ETH01 is now in **programming mode** and ready to flash firmware.

---

## Return to Normal Operation

After flashing firmware:

1. Ensure IO0 is NOT connected to GND.
2. Briefly connect **Pin 1 (EN)** to GND again to reset.

The module will now boot normally and run your uploaded firmware.

---

## Notes

- If flashing fails, double-check:
  - TX/RX are crossed correctly
  - IO0 is grounded during reset
  - Common ground is connected
- Some USB-to-TTL programmers require selecting 3.3V logic mode.

---

Your WT32-ETH01 should now be ready for MQTT-based TCP communication.

![alt text](<Screenshot from 2025-06-28 18-05-10-1.png>)
