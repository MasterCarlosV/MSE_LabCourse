
---

# Lab Assignment: GPIO Driver Development and Application

**Course:** Microcontrollers and Embedded Systems  
**Lab Title:** GPIO Driver Implementation and LED/Pushbutton Application  
**Author:** Carlos Villarreal  
**Date:** April 7, 2026  

---

## 1. Objectives
- Design and implement a **GPIO driver** based on the provided Software Requirements Specification (SRS).   
- Develop an **application module** that toggles an LED when a Push-Button is pressed.  
- Demonstrate modular design and hardware abstraction principles.  

---

## 2. Background
General Purpose Input/Output (GPIO) pins are fundamental to microcontroller-based systems. They allow digital signals to be read (inputs) or driven (outputs). A reusable GPIO driver simplifies application development by abstracting hardware details and providing a clean API.

---

## 3. Pre-Lab Preparation
- Review the **SRS for the GPIO driver** ([SRS-GPIO_Driver](../../SRS/GPIO/SRS-GPIO_Driver.md)).  
- Study STM32 GPIO register definitions (`MODER`, `ODR`, `IDR`, `BSRR`, clock enable registers).  
- Locate the pins connected to the user LED and the user Push-Button in the user manual of your develpment board ([UM1724-STM32-NULCEO-64](../../Documents/um1724-stm32-nucleo-64.pdf)).
- Use Visual Studio Code as your text editor and the terminal (Git Bash) to build and flash the code to the STM32 microcontroller.   

---

## 4. Lab Tasks
### Task 1: GPIO Driver Implementation
- Implement the GPIO driver functions as defined in the SRS.  
- Ensure compliance with functional requirements (FR-1 through FR-8).  
- Provide error handling for invalid ports/pins.  

### Task 2: LED Module
- Implement functions:  
  - `led_init`
  - `led_on`  
  - `led_off`  
  - `led_toggle`  
- Use GPIO driver functions internally.  

### Task 3: Button Module
- Implement function:  
  - `button_init`
  - `button_get_state`  
- Use GPIO driver functions to detect button state.  

### Task 4: Application Integration
- Configure one pin as **output (LED)** and another as **input (Push-Button)**.  
- In the main loop, toggle the LED whenever the Push-Button is pressed.  
- Add debounce logic if necessary.  

---

## 5. Deliverables
- Source code for the GPIO driver, LED module, and Button module.  
- Software Design Document of the GPIO driver based on the template ([SDD_Template](../../SDD/SDD_Template.md)).  
- Lab report documenting:  
  - Design decisions  
  - Test outcomes  
  - Observed behavior on hardware  

---

## 6. Evaluation Criteria
- **Correctness:** Driver functions meet SRS requirements.
- **Modularity:** LED and Button modules reuse GPIO driver cleanly.  
- **Documentation:** 
  - Clear lab report with results and discussion.  
  - Clear SDD of the GPIO driver based on the SRS.

---
