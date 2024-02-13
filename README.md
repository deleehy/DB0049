# DB0049
## Overview
This repository contains implementations of the demo board DB0049, which aims to demonstrate the functionalities of the ecomatBasic Products (Controller und 4.3“ Display) in a systematic context.

**Contact Person**: 
  -  Controller: _Georg Engelmann_
  -  mIoT: _Patrick Bühner_
  -  Display: _Florian König_
  -  Implementation V.1: _Dagmar Schymonski-Dederichs_
  -  Implementation V.2: _Hyung Joo Lee_
    
**Codesys Requirements**
  -  **CR413S**: Codesys V3.5 SP18 SP0 (64-bit)
  -  **CR1140/1142**: Codesys V3.5 SP19 SP5 (64-bit)

-The mIoT device **CR3133** is mainly configured in Maintenance Tool.\
-The version 2 was generated during the training period.  The entire system is, naturally, open to implementation in various creative ways. Feel free to explore different approaches ;)

## Purpose of the demonstration
The main focus is on demonstrating a simple shredder which is controlled with the ecomatBasic Controller [**CR413S**](https://github.com/deleehy/DB0049/tree/cr413s) based on the user inputs from the ecomatDisplay [**CR1140**](https://github.com/deleehy/DB0049/tree/cr1140). The status of the operation is wirelessly transfered via the CANWireless **CR3133** to the other ecomatDisplay [**CR1142**](https://github.com/deleehy/DB0049/tree/cr1142). The second controller on the right side serves as a placeholder and just blinks without any further tasks.

## Get Started
Set the desired speed and the operation time in CR1140. Press on the _Start_ CT Buttons to start the operation. The operation will stop after the defined operation time. Otherwise you can stop the operation using the stop button. 

  - The Safe application has 2 different states (_NonSafe, Operational_). The NonSafe state is critical and gets triggerred by the emergency stop button or door guard. Once triggered, it immediately stops the operation and can be released only after the explicit confirmation in the display **and** an additional release through the start button.\
  From the NonSafe application there are 3 more states that can stop the operation: _OReached_ and _CTStop_, where _OReached_ stands for OperatingTimeReached (which the user has defined in the display) and CapacityStopButton pressed. The current state is always visualized in the display.

-   It is important to note that **you can only start the operation again using the specific sequence**: 1) Release the E-Stop/ Door Guard 2) Confirm on the display 3) Start Button. This gives another safety to the overall system.
    
  - After initiation, the system enters the idle state, and it gradually regulates the shredder based on the specified operation time and desired speed. You can see that the stop behavior varies (soft/hard) depending on whether the stop is initiated from the _OReached_ state or other states, such as emergency situations.

  - Speed adjustment can be accomplished through two methods: either by configuring a precise target speed or by incrementally adjusting it using the speed control buttons in P1.

  - For the configuration of **CR3133**, please look into to the tutorials in the project management hub.

  - The button colors of CR1140 indicate the current state of the system: $${\color{green}Running}$$ $${\color{orange}Idle}$$ $${\color{red}NonSafe}$$  $${\color{blue}ConfirmAwaited}$$

  - Currently, following numbers are logged in **CR1140**: System On Time, System Up Time, Energy Consumption for Shredding and the Stop Events.

## TO-DOs:
  -  The board can be extended by incorporating a meaningful task for CR403s, as it currently serves just as a placeholder
    
