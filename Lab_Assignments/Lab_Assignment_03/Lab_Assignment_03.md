
---

# Lab Assignment: ADC Driver Development and Application  

**Course:** Microcontrollers and Embedded Systems  
**Lab Title:** ADC Driver Implementation and Sensor-Controlled PWM Application  
**Author:** Carlos Villarreal  
**Date:** April 29, 2026  

---

## 1. Objectives
- Design and implement an ADC driver based on the provided Software Requirements Specification (SRS).  
- Develop an **Analog Sensor module** that reads sensor values using the ADC driver.  
- Use the **PWM module** developed on ([Lab Assignment 02](../Lab_Assignment_02.md)) to generate a PWM output signal on a GPIO pin.  
- Integrate both modules so that the analog sensor signal controls the PWM duty cycle.  
- Demonstrate modular design and hardware abstraction principles.  

---

## 2. Background
Analog-to-Digital Converters (ADC) in STM32 microcontrollers are essential for measuring analog signals such as temperature, light intensity, or potentiometer voltage. A reusable ADC driver simplifies application development by abstracting hardware details and providing a clean API.  

Pulse Width Modulation (PWM) signals are widely used in embedded systems for motor control, LED dimming, and sensor-actuator feedback. By combining the ADC driver with a PWM module, students can build applications where sensor input directly influences actuator output.  

---

## 3. Pre-Lab Preparation
- Review the **SRS for the ADC driver** ([SRS-ADC_Driver](../../SRS/ADC/SRS-ADC_Driver.md)).  
- Study STM32 ADC register definitions (`CR1`, `CR2`, `SQRx`, `SMPRx`, `SR`, `DR`).   
- Locate the pins connected to the analog sensor input and PWM output in the user manual of your development board ([UM1724-STM32-NULCEO-64](../../Documents/um1724-stm32-nucleo-64.pdf)).  
- Use Visual Studio Code as your text editor and the terminal (Git Bash) to build and flash the code to the STM32 microcontroller.  

---

## 4. Lab Tasks

### Task 1: ADC Driver Implementation
- Implement the ADC driver functions as defined in the ADC SRS.  
- Ensure compliance with functional requirements (FR-1 through FR-9).  
- Provide error handling for invalid ADC instance or channel inputs.  

### Task 2: Sensor Module Implementation
- Implement functions:  
  - `sensor_init`  
  - `sensor_startConversion`
  - `sensor_readValue`  
- Use ADC driver functions internally to configure and read sensor values.  
- Verify sensor readings using a potentiometer or analog sensor connected to the board.  

### Task 3: Application Integration
- Configure ADC to read sensor input (e.g., potentiometer voltage).  
- Map ADC reading to PWM duty cycle (e.g., 0–4095 ADC value → 0–100% duty cycle).  
- Demonstrate real-time control: turning the potentiometer changes LED brightness via PWM.  

---

## 5. Deliverables
- Source code for the ADC driver, TIM driver, GPIO driver, Sensor module, and PWM module.  
- Software Design Document (SDD) of the ADC driver based on the template ([SDD_Template](../../SDD/SDD_Template.md)).  
- Lab report documenting:  
  - Design decisions  
  - Test outcomes  
  - Observed behavior on hardware (sensor readings, PWM waveform verification, LED brightness control)  

---

## 6. Evaluation Criteria
- **Correctness:** Driver functions meet SRS requirements.  
- **Modularity:** Sensor and PWM modules reuse ADC and TIM drivers cleanly.  
- **Documentation:**  
  - Clear lab report with results and discussion.  
  - Clear SDD of the ADC driver based on the SRS.  
- **Hardware Validation:** Sensor readings and PWM waveform verified on STM32 hardware.  

---
