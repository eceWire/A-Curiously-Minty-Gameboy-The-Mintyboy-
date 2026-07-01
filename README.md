<img width="741" height="989" alt="IMG_5061" src="https://github.com/user-attachments/assets/61cc7ca7-40b6-472e-b40f-6075783a4b61" />

<img width="741" height="989" alt="IMG_5054" src="https://github.com/user-attachments/assets/a20bb075-97c9-4fdb-b30d-fe78f4f0c418" />
<img width="556" height="989" alt="IMG_5001 MOV" src="https://github.com/user-attachments/assets/44148fa6-aa6a-4021-bee3-aa8944b443dd" />
<img width="741" height="989" alt="IMG_5055" src="https://github.com/user-attachments/assets/8c2f74cb-133c-4b2f-b15b-e5de728c60b5" />
<img width="741" height="989" alt="IMG_5056" src="https://github.com/user-attachments/assets/f179e961-5689-46c2-9103-6ae0494a4200" />
<img width="741" height="989" alt="IMG_5057" src="https://github.com/user-attachments/assets/cac257ce-a5a4-4374-a8c5-ce0436eedfe4" />
<img width="741" height="989" alt="IMG_5058" src="https://github.com/user-attachments/assets/539304e4-12a0-4a00-928f-983b926ad9e1" />
<img width="741" height="989" alt="IMG_5059" src="https://github.com/user-attachments/assets/39878fa9-ade4-4f97-b843-7659b54976fb" />

<img width="527" height="516" alt="image" src="https://github.com/user-attachments/assets/0dfa8c94-ec5d-482f-aa88-3faee584e02d" />

<img width="517" height="522" alt="image" src="https://github.com/user-attachments/assets/71f3bd13-417c-4961-9f9f-84b9c30df483" />



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

## Story

I had only one question in mind: how much can you fit inside an Altoids box? That is what allowed me to create this project. At first, I had NO idea what Arduino was, until, Mark Rober. I saw one of his videos on YouTube in school and I wondered, "what can I do with that?" And from that day, eceWire was born. I've been working with so many projects on these since 10 years old, and currently. This has been one of my most advanced projects EVER. After documenting a lot of this, someone texted me a few days ago.

"Hey Arjun, I really like what you're doing, I'm running a club at the public library right now, I'll explain everything later, I promise it's not a scam!"

I was very suspicious at first, and was not sure if I wanted to go. But I did anyways.

The guy who messaged me ended up being somone who has given a TEDx before, and I thought that was just crazy! And currently, he's given me a spot in the TEDx in August to present the Mintyboy.

So, this has probably been one of the best thing's that has happened to me in my life, so remember "don't let anyone stop you, let your wildest dreams come true :)" - Arjun aka eceWire
## AI Usage

AI was not used to code at all, it was used a little to add comments in between (not the big on at the top of the code). It was not used to debug or fix code or write any at all. All code is handmade.

---

## Built For

Hack Club Stardance Challenge

---

## Creator

Arjun (eceWire)

YouTube: https://www.youtube.com/@eceWire

<img width="152" height="203" alt="IMG_5057" src="https://github.com/user-attachments/assets/c17223cf-8e7a-473c-b32f-a6f04087cb50" />
<img width="581" height="1033" alt="IMG_4996 MOV" src="https://github.com/user-attachments/assets/bda7cf39-6021-4f9a-8fdf-e6676d666dc0" />
<img width="152" height="271" alt="IMG_5001 MOV" src="https://github.com/user-attachments/assets/521ad85b-3b54-48ec-860c-5e3e71ee0a7d" />
<img width="775" height="1033" alt="IMG_4979" src="https://github.com/user-attachments/assets/5888fda7-f4ec-4fe4-805f-2710535899a0" />
<img width="825" height="1033" alt="IMG_4954" src="https://github.com/user-attachments/assets/9d862e46-4c13-4b7a-bd04-8f3b27e98a7d" />
<img width="959" height="719" alt="IMG_4950" src="https://github.com/user-attachments/assets/94eead8e-6f73-488d-9cf4-5ad1b6ba9f54" />

