# Mintyboy Devlogs / Journal Entries

> Disclaimer: All of these are copy/pasted from devlogs from the Staradance challenge, Slack member told me to do so :)

---

# Devlog - 01

## 10h 22m 49s logged

### A Curiously Minty Gameboy😏

Using an Altoids tin and an Arduino, I’ve been building a fully functional mini “gameboy,” and I’m now at the point where the project is almost complete. Over the past few days, I’ve put in a lot of time refining the code, especially working on the 2048 game feature. I’m thinking about adding Pong and Tetris at this stage. After a long stretch of late-night debugging and tweaking, I finally have the game running smoothly on the display, which feels like a huge accomplishment.

At this stage, most of the core functionality is finished, and everything is coming together exactly how I imagined. The display works, the logic behind the game is solid, and the overall structure of the code is nearly finalized. The main thing left to polish is the pushbutton input system, since the controls still need to be a bit more responsive and reliable.

Once I fix that, the project will essentially be complete, and I can focus on final touches like optimizing performance and maybe adding a few extra features. It’s been a challenging but super rewarding experience, and I’m really close to having a fully working Arduino-powered “phone” inside an Altoids tin.

---

# Devlog - 02

## 30h 37m 19s logged

### A Curiously Minty Gameboy

This is probably one of my favorite builds so far—a tiny, Altoids powered “Gameboy” that somehow turned into a full-on mini gaming system.

What started as a simple project with an Arduino Nano quickly got an upgrade. I switched over to the Arduino Nano ESP32, and that change honestly unlocked everything. With more power, built-in WiFi and Bluetooth, and way more flexibility, the project went from “cool gadget” to something that actually feels like a real handheld console.

On the software side, I’ve packed in a bunch of classic games:

2048 (which took forever to get smooth and responsive)  
Tetris (definitely the most satisfying one to play)  
Pong (simple, but it just feels right on this device)

But the part I’m most proud of isn’t even the games—it’s the settings system. I built out a full menu where you can actually customize the device like a real piece of tech. Inside settings, you can:

Connect to WiFi  
Use Bluetooth  
Switch between light and dark mode  
And even clear all saved data if you want a fresh start  

That’s something I didn’t originally plan, but once I started adding features, it just made sense to treat it like a real OS instead of just a game launcher.

Hardware-wise, everything is crammed into an Altoids tin, which makes it feel super compact and kind of ridiculous in the best way. There’s still some tweaking left—mainly refining controls and polishing the UI—but it’s at the point where it’s fully usable and actually fun.

Overall, this project taught me a ton—not just about Arduino and ESP32, but about designing systems, managing features, and turning a small idea into something way bigger than I expected.

---

# Devlog - 03

## 11h 24m 58s logged

### A Curiously Minty Gameboy

Officially, I’ve given my project a name: The Minty Boy!

I call it that because it’s not just a regular Gameboy, it has a little “kick” to it, like a mint.

Instead of just running the 3 regular games: 2048, Tetris, and Pong, it can now send messages and display the weather accurately; moreover, I’ve added the feature where it can track your IP address and find out what the weather is in your location, and on the home screen, display the date/time of your location (according to the IP Address).

This project is reaching the end.

The end of the prototype, of course.

This is just the beginning of the Minty boy.

---

<div align="center">

# Ship #1

</div>

## What did you make?

I made A Curiously Minty Gameboy (The Mintyboy), a handheld gaming and utility device built inside an Altoids tin using an Arduino Nano ESP32. It includes games like 2048, Tetris, and Pong, along with WiFi, Bluetooth, SMS messaging, weather features, and a custom settings interface.

## What was challenging?

The biggest challenge was fitting so much functionality into a small device. Implementing WiFi connectivity, managing memory, creating a user-friendly interface on a tiny screen, and fitting all the hardware inside an Altoids tin required a lot of problem-solving.

## What are you proud of?

I'm most proud of turning a simple game console idea into a multifunctional connected device. Features like WiFi scanning, saved credentials, SMS messaging, and a polished settings system make it feel like a real handheld system rather than just a collection of games.

## What should people know so that they can test your project?

To test all features, users should upload the code to an Arduino Nano ESP32 with the required display and button hardware connected. WiFi features require a nearby wireless network, and SMS functionality requires valid Twilio credentials configured in the code. The games and core interface work directly on the device once powered on. Some may ask: does it close? The answer is yes the tin does close (and it's magsafe, so you can attach it to your fridge or the back of your phone :0)!

---

# Devlog - Feature Expansion

## 48h 59m 29s logged

Mintyboy Devlog — Feature Expansion

Overview  
Mintyboy has evolved from a basic handheld into a small multi-purpose system. It now combines games, utilities, and live data features on a single ESP32 with a 1.96 inch TFT display.  
The main focus recently has been expanding functionality while keeping everything responsive and usable on very limited hardware.

Games  

2048  
Tetris  
Pong  
Flappy Bird  
Snake  
Breakout  
Minesweeper  
Simon Says  

Challenges  

The biggest challenge across all games is performance and memory. The ESP32 isn’t powerful in terms of graphics, so everything has to be drawn efficiently.

Tetris required a full grid system, rotation logic, and line clearing without slowing down rendering  
Minesweeper needed a hidden tile system, recursive reveals, and flag handling, which added complexity fast  
Flappy Bird was mostly about tuning physics and timing so button input felt responsive and fair  
Snake and Pong were simpler but still required smooth updates without flickering  

Another issue was keeping a consistent input system across all games. Since everything uses the same buttons, the controls had to feel natural in every game without rewriting input logic each time.

Calculator  

Supports basic math operations  
Displays a full expression before evaluation  
Shows results clearly on screen  

Challenges  

The biggest issue was input navigation. Without a keypad or touchscreen, selecting numbers and operators using buttons can feel slow if not designed well.  
Handling edge cases like multiple operations, clearing input, and preventing invalid expressions also needed extra logic.  
UI layout was another constraint, since everything has to fit on a very small screen without becoming confusing.

News Feature  

The news system pulls live headlines from a BBC RSS feed.  

No API key required  
Uses HTTP requests  
Parses XML data  
Displays headlines in a scrollable format  

Challenges  

Parsing XML on an embedded device is not ideal. Memory usage becomes a problem quickly, so the system only extracts the necessary parts instead of storing the full response.  
Text formatting was another issue. Headlines can be long, so they need to be wrapped correctly to fit the TFT display without cutting off words awkwardly.  
There’s also the delay from network requests, which had to be handled so the UI doesn’t freeze while loading.

Stocks Feature  

The stocks feature is one of the most complex systems so far.  

User inputs a ticker symbol  
Fetches data from Yahoo Finance  
Displays current price  
Renders a small price chart  

Challenges  

Handling API responses was the first hurdle. The data needs to be parsed and reduced to only what’s necessary.  
Drawing the graph was the hardest part. Since there’s no charting library, everything is done manually:  

Normalize price data  
Scale it to screen size  
Draw lines between points  

Another issue was keeping the graph readable on such a low-resolution display. Too much data makes it messy, so it had to be limited and simplified.

System Integration  

As more features were added, managing the overall system became harder.  

Avoiding blocking code so the device doesn’t freeze  
Managing memory between games and network features  
Keeping the UI consistent across completely different apps  
Handling transitions between menus and features cleanly  

System State  

Current features:  

Games system with multiple titles  
Calculator  
News reader (RSS-based)  
Stock tracker with chart rendering  

What else should I add guys??

---

# Devlog - NASA Feature

## 15h 43m 7s logged

Devlog: NASA Feature (Mintyboy)

Overview  

The NASA feature turns the Mintyboy from just a game console into a space exploration device. It combines real-world NASA data with a retro UI, letting users explore planets, missions, and daily space content directly from the device.

Planets & Moons Explorer  

Added a scrollable menu system for planets  

Each planet includes:  

Name  
Basic info  
Major moons (e.g., Europa, Titan, Luna)  

Designed to work smoothly on limited hardware  
Keeps everything lightweight and readable on a small screen  

This feature gives the Mintyboy a mini solar system database.  

Artemis II Mission  

Added a dedicated section for Artemis II  

Highlights:  

First crewed mission of the Artemis program  
Mission goal: orbit the Moon and return safely  

Acts like a featured story inside the NASA menu  

This connects the Mintyboy to real, modern space exploration.  

APOD (Astronomy Picture of the Day)  

Uses WiFi to connect to NASA’s APOD API  

Displays:  

Title  
Short description  

Images are simplified due to hardware limits; the TFT screen cannot display an image that is in APOD  

This makes the device feel dynamic, like it’s updating with new space content daily (which it kinda is)

Challenges:  

Fitting large astronomy data into a tiny display  
Managing memory limits  
Parsing API responses efficiently  
Keeping UI smooth alongside games  

Final Result  

The NASA feature transforms the Mintyboy into:  

A game console  
A learning tool  
A space exploration hub!

---

# Devlog - PCB

## 8h 45m 3s logged
**I don't know why on Stardance it says 18 hours, this was NOT 18 hours spent on this, coding was like a lot**

Devlog - PCB

I’ve been working on this PCB for a while, and I’ve made the project REALLY compact right now. So far, I’m thinking of the news feature to add actual articles instead of just the headlines (it won’t be easy, but I’ll try). In order to complete this, adding a PCB and not just on a breadboard is totally needed, and here’s how it looks so far :) Btw I’m actually not doing this on KiCad, I prefer EasyEDA.. I forgot to mention the code that I’ve been working on, I’m adding a little feature with a camera, but it’s been quite difficult, using OV7670, and it’s been taking a LOT of time
