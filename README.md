# A Curiously Minty Gameboy (The Mintyboy)

A Curiously Minty Gameboy, or The Mintyboy, is a handheld gaming and utility system built inside an Altoids tin for the Hack Club Stardance Challenge.

It started as a simple Arduino Nano project focused only on games, but gradually evolved into a full embedded system. After switching to an Arduino Nano ESP32, I was able to turn it into a connected handheld device with WiFi, Bluetooth, SMS messaging, weather data, NASA data systems, stock tracking, EEPROM storage, a calculator, and a full settings interface.

The goal was to push how much real functionality I could fit into a very constrained physical device while still keeping it usable and stable.

A lot of the project ended up being about managing complexity rather than just adding features.

---

## Core Idea

The Mintyboy is a compact handheld system that behaves more like a tiny operating system than a single-purpose device.

It combines:
- Games
- Real-time internet data systems
- Communication features
- Utilities
- Persistent storage
- Device configuration

Everything runs on a single ESP32 inside an Altoids tin, which forced constant tradeoffs between performance, memory, and functionality.

---

## Games System

The games system was the foundation of the project and influenced how the rest of the device was designed.

It includes:

- 2048
- Tetris
- Pong
- Flappy Bird
- Snake
- Simon Says


Each game is fully custom-built for:
- small TFT display constraints
- physical button input
- limited RAM and flash storage

A major challenge was making sure games didn’t interfere with system features. As more features were added, memory pressure increased, so game optimization became necessary rather than optional.

---

## NASA Data System (Multi-Source Integration)

NASA integration is not just a single feature, but part of a broader real-time data system.

The device connects to NASA APIs and can retrieve multiple types of live space and science data, including:
- Astronomy Picture of the Day (APOD)
- space imagery and metadata feeds
- structured NASA API responses (JSON-based)


The system displays this on the ST7789 TFT display.

This required handling:
- JSON parsing under memory constraints
- inconsistent API response sizes
- image and metadata formatting limitations
- network reliability issues

This module was one of the first times the device felt like it was truly connected to real-world scientific data rather than just running local code.

---

## Stock Tracking System

The stock tracking system pulls real-time financial data from online APIs.

It supports:
- live stock price retrieval
- parsing multiple API responses
- simplified financial dashboards
- quick switching between tracked symbols

Here's how it works:

1.Put in your ticker symbol (there is no defualt one, the most simplest one would be KO [coca cola]) and use the push buttons to navigate around. It uses Yahoo Finance API key to work!
2. Watch the data come and a graph print on the screen in real time !

The biggest challenge was not fetching data, but making it usable on a very small screen while dealing with inconsistent API formats and network latency.


---

## Calculator

A built-in calculator provides basic arithmetic functionality.

It supports:
- addition
- subtraction
- multiplication
- division

It is designed to be fast, minimal, and usable entirely through button input, without relying on external libraries.

---

## Weather System

The weather system connects to online APIs and retrieves live environmental data.

It includes:
- current temperature
- weather conditions (clear, cloudy, rain, etc.)
- humidity levels
- wind speed
- air quality index (AQI when available from API source)

This system required careful formatting because weather APIs return large datasets that must be reduced into readable information for a small screen.

---

## SMS Messaging (Twilio Integration)

The Mintyboy can send SMS messages using WiFi and the Twilio API.

It supports:
- sending text messages from the device
- cloud-based authentication (SID and token handling)
- configurable destination numbers

This feature required careful handling of:
- HTTP request formatting
- authentication reliability
- WiFi dependency before sending messages

It effectively turns the device into a basic cloud-connected communication tool.

---

## WiFi System

WiFi is the foundation of all online features.

It enables:
- network scanning
- connecting to WiFi networks
- saving credentials
- reconnecting automatically on boot

All API-based systems depend on this module, so stability here directly affects everything else in the device.

---

## Bluetooth System

The ESP32 Bluetooth system is included as a foundation for future expansion.

It is currently used as:
- a system capability layer
- preparation for future device-to-device communication
- potential external control or companion integration

---

## Settings System

The device includes a full settings system that organizes all features into a structured interface.

It includes:
- WiFi management (scan, connect, save networks)
- Bluetooth controls
- display mode (light/dark)
- system reset and data clearing
- configuration tools for system behavior

This system was necessary to prevent the device from becoming a flat collection of disconnected features.

---

## EEPROM Data Storage

EEPROM is used for persistent storage across power cycles.

It stores:
- WiFi credentials
- system settings
- device state

Without EEPROM, the system would reset on every reboot, making long-term use impossible.

---

## Hardware

- Arduino Nano ESP32
- ST7789 TFT display
- Physical push buttons
- Altoids tin enclosure
- Battery power system

The physical size constraint of the Altoids tin heavily influenced design decisions across the entire project. Every feature had to justify its memory, space, and processing cost.

---

## Wiring

### Display Connections

| Pin | ESP32 |
|-----|------|
| VCC | 3.3V |
| GND | GND |
| SCK | D13 |
| MOSI | D11 |
| CS | User defined |
| DC | User defined |
| RST | User defined |
| BLK | 3.3V |

---

### Button Mapping

| Function | Pin |
|----------|-----|
| Up       | D3 |
| Down     | D5 |
| Left     | D2 |
| Right    | D4 |
| Mode     | D6 |

---

## Hardware Limitations

The project was heavily constrained by hardware throughout development.

Main limitations included:
- limited RAM causing feature conflicts
- flash storage constraints limiting expansion
- UI space restrictions due to small screen size
- WiFi instability affecting all online systems
- EEPROM size limitations
- performance drops when multiple systems ran together

A major part of development was constantly balancing features so the system remained stable rather than overloaded.

---

## Why I Switched to ESP32

The original Arduino Nano was sufficient for early prototypes but quickly became limiting.

Switching to the ESP32 enabled:
- WiFi connectivity
- Bluetooth support
- significantly more memory
- faster processing
- support for multiple real-time APIs

This upgrade is what made the full system possible.

---

## Challenges

- fitting a full system into an Altoids tin
- managing memory constraints across multiple features
- designing a usable UI on a very small display
- integrating multiple APIs (NASA, stocks, weather, Twilio)
- keeping code organized as complexity increased
- WiFi instability and reconnect handling
- EEPROM debugging and data persistence issues
- preventing system features from interfering with each other

---

## What I Learned

- embedded systems are defined by constraints
- memory management is critical in multi-feature devices
- API integration on microcontrollers is non-trivial
- UI design matters even more on small hardware
- system architecture becomes essential as features scale
- hardware limitations directly shape software design

---

## Future Improvements

- more games and utilities
- improved UI navigation system
- better WiFi setup and stability handling
- Bluetooth communication features
- notification system
- OTA updates
- improved power efficiency
- expanded stock and data dashboards

---

## AI Usage

AI was not used to code at all, it was used a little to add comments in between (not the big on at the top of the code). It was not used to debug or fix code or write any at all. All code is handmade.

---

## Built For

Hack Club Stardance Challenge

---

## Creator

Arjun (eceWire)

YouTube: https://www.youtube.com/@eceWire
