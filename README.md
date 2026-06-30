# ORP - the Open Robotics Platform

The Open Robotics Platform (placeholder name) is a project that has the goal of simplifying the controlling of electromechanical and electronic components commonly used in robotics and electronics projects.

### The Vision
The ORP project will allow users to set-up simple input stages to accept wide ranges of input types and voltages and have them act upon wide ranges of output types and voltages. Furthermore, functionality will be expanded with simple, inexpensive add-on modules.

### What It Is RIGHT NOW
The ORP project currently has a working, fleshed out input stage that includes:
- Reverse polarity protection
- 1W of dissipation potential allowing a wide input range
- optoisolation
- hardware debouncing

This is very much a WIP - stay tuned!
---

## Why does this thing exist?

I believe that a lot of the complexity of robotics and electronics projects isn't necessary. It shouldn't be necessary to understand how to:
1. Pick the right microcontroller
2. Install software, drivers, programmers
3. Learn to code
4. Diagnose compile and flashing issues
5. Selecting electronic components
6. Learning semi-advanced electronics concepts
7. Breadboard a mess of wiring

**Just to get a motor turning, a servo moving, a solenoid firing, a LED flashing.**

The ORP project would mean that a high school student would just need to connect a few wires and select a few drop-downs to immediately start experimenting with robotics and electronics. The project aims to reduce the cost of entry in both monetary terms and mental overhead.
> - When you lower barriers to entry, you increase participation.
> - When you increase participation, you make the thing better for everyone.

### Why the ORP vs Arduino or a PLC?

The simple answer is accessibility. You can buy cheap Arduino clone boards or starter kits and have a motor connected to it in seconds. But to get it to actually spin would require:

1. Installing of the Arduino IDE
2. Installing drivers (ex. CH340)
3. Understanding of C programming
4. Understanding of Arduino boilerplate
5. Understanding of Arduino libraries
6. Uploading the code (and diagnosing issues that may arise)
7. Understanding of basic wiring (this is also present in the ORP)
8. Understanding motor drive boards
9. Understanding inputs

To go the PLC route, you would have to add expensive hardware (the PLC itself) and expensive proprietary hardware as well.

The goal of the ORP is to significantly reduce the time between ideation and result. It should take minimal instructions and minimal time to:

1. Link a smart device to the ORP (tablet, phone, laptop etc...)
2. Select inputs and outputs via the smart device
3. Make connections
4. Get results

No strict device requirements, no electronics knowledge beyond **extremely** basic concepts, just pure trial and error and fun!

---

## How It Works

The idea is that the board is self-contained, it has clearly marked terminals where you can connect inputs and outputs, powers and grounds. You would connect the device itself to USB power, or a battery and it would power on, and then you would connect to it via your device (at the moment, it's a web interface) and set-up your inputs and outputs on your device's screen. Once that is setup, there will be a display showing you what to connect where, make your connections and hit **"run"**. The device will reset and then the inputs and outputs will be active, ready to be used.

---

## Hardware

### Microcontroller choice

The ideal candidate for this would be an **ESP32-S3**

1. It has **very** flexible pins that can be used as inputs/outputs/I2C/SPI etc...
2. Built-in BLE and WiFi
3. Dual core to handle the load of hosting a webserver/webpage
4. Large amount of built-in memory
5. Available in many form-factors for flexibility of design
6. Inexpensive
7. Ubiquitous

### Input stage

The input stage needs to be considered carefully and at the time of this writing the requirements are as stands:

1. Wide input range ~3-24V
2. Protected inputs from over voltage/current/noisy inputs
3. Schmitt trigger inputs to ensure clean edges for triggering

### Output stage

The output stages also need to be considered carefully, at the time of this writing the requirements are as stands:

1. Wide control voltage ~3-24V
2. Low-side MOSFET control for higher current and independent voltage
3. Series breakers (resettable) to resist damage from short-circuits

---

## Software

The firmware is currently being decided on - the two main competitors would be:
1. Arduino IDE
2. MicroPython

### A case for Arduino IDE
The Arduino ecosystem is well-documented and has libraries for most anything that can possibly be thought of for this project. It is based on C/C++ so performance will be effective and everything is very well documented.

The down sides are that it is a proprietary platform and therefore beholden to changes and decisions made by various stakeholders, and that the codebase is a lot slower to develop for - C can be obtuse in development

### A case for MicroPython
MicroPython being a fork of vanilla Python is a positive aspect - it's an open standard and not beholden to anyone but the Python steering committee. It is quick to develop for and has clear, easy to understand structure that might make it easier to get new developers interested in co-developing the software.

On the down side, Python is an interpreted language and has overhead while running, and garbage collection. The project might grow large enough to make it so that micropython would be too slow to get real-time control of a plurality of inputs and outputs, especially if there is some important math to be done at the same time.

Micropython also relies on other projects to upload to the microcontroller - possibly involving something like platform.io or Thonny

### The leanings
The current leaning is to go with micropython to start-off with that until the performance is inadequate or a RTOS (Real-Time Operating System) becomes required and then switch to C/C++

---

# What's Next?

Once the documentation is finished, the next step will be as follows:

1. Researching component selection for input stage
2. Reseatching component selection for output stage
3. Building a breadboard prototype
4. Building software prototype
5. Designing a PCB
6. Designing an enclosure

## The First Goalpost

The first goalpost is to have a working prototype and produce a YouTube video to get viewer feedback.
I feel like this is important to do early in production so that changes can be made early. Having a fully-functional prototype will also allow the entire system to be tested as a whole to make sure all the parts interact with each other.