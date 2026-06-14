**A Curiously Minty Gameboy (The Mintyboy)**

A Curiously Minty Gameboy, or The Mintyboy, is a handheld gaming and utility system built inside an Altoids tin for the Hack Club Stardance Challenge.

The project started as a simple gaming device using an Arduino Nano, but eventually grew into something much larger. After switching to an Arduino Nano ESP32, I was able to add WiFi, Bluetooth, SMS functionality, weather integration, and a much more advanced settings system.

The goal was to see how much functionality I could fit inside an Altoids tin while still making it practical and fun to use.

**Features:**

** Games:**

The Mintyboy currently includes three games:

* 2048
* Tetris
* Pong

Each game was programmed specifically for the device and optimized to work with the physical controls and display.

**Settings:**

Instead of being just a game launcher, the Mintyboy includes a settings interface that behaves more like a real handheld device.

Current settings include:

* WiFi management
* Bluetooth controls
* Light and dark mode
* Data clearing and reset options

The WiFi menu can scan nearby networks, connect to them, and save credentials for future use.

**SMS Messaging:**

One of the newest features is SMS support.

Using WiFi and the Twilio API, the Mintyboy can send text messages directly from the device. This allows it to act as more than just a gaming console and demonstrates how embedded devices can communicate with cloud services.

**Weather:**

The Mintyboy can connect to the internet and retrieve weather information through an online API. Weather data is displayed directly on the device.

**Hardware:**

Main components:

* Arduino Nano ESP32
* ST7789 TFT Display
* Push Buttons
* Altoids Tin
* Battery Power System

**Connections**

**Display:**

| Display Pin | Arduino Nano ESP32 |
| ----------- | ------------------ |
| VCC         | 3.3V               |
| GND         | GND                |
| SCK         | D13                |
| MOSI        | D11                |
| CS          | User Defined       |
| DC          | User Defined       |
| RST         | User Defined       |
| BLK         | 3.3V               |

**Buttons:**

| Function |Pin|
| -------- | --|
| Up       |D3 |
| Down     |D5 |
| Left     |D2 |
| Right    |D4 |
| Mode     |D6 |

Update these values to match your actual wiring.

**Twilio Setup**

To enable SMS functionality, create a Twilio account and obtain:

* Account SID
* Auth Token
* Twilio Phone Number

Add them to your project:

```cpp
const char* TWILIO_SID = "YOUR_ACCOUNT_SID";
const char* TWILIO_AUTH = "YOUR_AUTH_TOKEN";
const char* TWILIO_FROM = "+1234567890";
```

You will also need to specify the destination phone number used for testing.

The device must be connected to WiFi before SMS features can be used.

**Why I Switched to the Nano ESP32:**

The project originally used a standard Arduino Nano. While it worked well for basic games, I quickly ran into limitations.

Switching to the Arduino Nano ESP32 gave me:

* Built-in WiFi
* Built-in Bluetooth
* More memory
* Faster processing
* Internet connectivity
* Support for cloud services like Twilio

The upgrade made it possible to expand the project beyond gaming and turn it into a connected handheld system.

**Challenges**
One of the biggest challenges was fitting everything into an Altoids tin while keeping it usable.

Other challenges included:

* Designing a user interface for a small screen
* Managing memory usage
* Building multiple games
* Implementing WiFi connectivity
* Integrating SMS support
* Organizing a growing codebase

**What I Learned**

This project taught me a lot about:

* Embedded systems
* Arduino development
* ESP32 networking
* User interface design
* API integration
* Hardware and software integration
* Game development

**Future Plans**

Some ideas for future improvements include:

* More games
* Better password input for WiFi
* Bluetooth communication features
* Notifications
* Improved battery life
* Over-the-air updates

Built For

Hack Club Stardance Challenge

Created by Arjun :) AKA eceWire.

Check you my YouTube Channel!

https://www.youtube.com/@eceWire
