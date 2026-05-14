
---

# Lab Assignment: I2C & SPI Driver Development and Sensor Integration  

**Course:** Microcontrollers and Embedded Systems  
**Lab Title:** I2C/SPI Driver Implementation and Sensor-Controlled Application  
**Author:** Carlos Villarreal  
**Date:** May 13, 2026  

---

## 1. Objectives
- Design and implement **I2C and SPI drivers** based on their respective Software Requirements Specifications (SRS).  
- Develop a **Sensor driver** that communicates via I2C, SPI, or both depending on the sensor interface.  
- Integrate the sensor driver into an application that reads sensor data and performs an action (e.g., controlling LED brightness or motor speed).  
- Demonstrate modular design, hardware abstraction, and driver reuse principles.  

---

## 2. Background
I2C and SPI are widely used serial communication protocols in embedded systems.  
- **I2C** is a two-wire protocol (SCL, SDA) commonly used for sensors and EEPROMs.  
- **SPI** is a four-wire protocol (MISO, MOSI, SCK, CS) used for high-speed communication with displays, ADCs, and memory chips.  

Developing reusable drivers for these protocols allows seamless integration of external devices. By building a sensor driver on top of I2C/SPI, students will learn how to abstract hardware communication and expose a clean API for application development.  

---

## 3. Pre-Lab Preparation
- Review the **SRS for the I2C driver** ([SRS-I2C_Driver](../../SRS/I2C/SRS-I2C_Driver.md)).  
- Review the **SRS for the SPI driver** ([SRS-SPI_Driver](../../SRS/SPI/SRS-SPI_Driver.md)).  
- Study STM32 I2C register definitions (`CR1`, `CR2`, `CCR`, `TRISE`, `SR1`, `SR2`, `DR`).  
- Study STM32 SPI register definitions (`CR1`, `CR2`, `SR`, `DR`).  
- Review datasheet of the chosen sensor (I2C or SPI interface).  
- Locate the pins connected to the sensor interface in the user manual of your development board ([UM1724-STM32-NULCEO-64](../../Documents/um1724-stm32-nucleo-64.pdf)).  
- Use Visual Studio Code as your text editor and the terminal (Git Bash) to build and flash the code to the STM32 microcontroller.  

---

## 4. Lab Tasks

### Task 1: I2C Driver Implementation
- Implement the I2C driver functions as defined in the I2C SRS.  
- Ensure compliance with functional requirements (FR-1 through FR-10).  
- Provide error handling for invalid addresses or bus errors.  

### Task 2: SPI Driver Implementation
- Implement the SPI driver functions as defined in the SPI SRS.  
- Ensure compliance with functional requirements (FR-1 through FR-8).  
- Provide error handling for invalid buffer pointers or bus errors.  

### Task 3: Sensor Driver Development
- Implement functions:  
  - `sensor_init` (configure sensor via I2C/SPI).  
  - `sensor_readData` (retrieve sensor measurement).  
  - `sensor_config` (optional: configure sensor registers).  
- Use I2C or SPI driver functions internally depending on sensor interface.  
- Verify sensor readings using a debugger or serial output.  

### Task 4: Application Integration
- Configure sensor driver to read sensor data (e.g., temperature, light, or accelerometer).  
- Map sensor data to an application output:  
  - Example: Sensor value controls PWM duty cycle of an LED.  
  - Example: Sensor value is printed via UART.  
- Demonstrate real-time control: sensor input directly influences actuator output.  

---

## 5. Deliverables
- Source code for: GPIO driver, I2C driver, SPI driver, and Sensor driver.  
- Software Design Document (SDD) of the I2C driver based on the template ([SDD_Template](../../SDD/SDD_Template.md)).  
- Software Design Document (SDD) of the SPI driver based on the template ([SDD_Template](../../SDD/SDD_Template.md)).  
- Lab report documenting:  
  - Design decisions  
  - Test outcomes  
  - Observed behavior on hardware (sensor readings, actuator response)  

---

## 6. Evaluation Criteria
- **Correctness:** Driver functions meet SRS requirements.  
- **Modularity:** Sensor driver reuses I2C/SPI drivers cleanly.  
- **Documentation:**  
  - Clear lab report with results and discussion.  
  - Clear SDDs of the I2C and SPI drivers based on their SRS.  
- **Hardware Validation:** Sensor readings and actuator behavior verified on STM32 hardware.  

---
