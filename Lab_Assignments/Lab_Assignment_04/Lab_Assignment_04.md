
---

# Lab Assignment: UART Driver and Serial Communication

**Course:** Microcontrollers and Embedded Systems  
**Lab Title:** UART Driver Implementation and Serial Communication  
**Author:** Carlos Villarreal  
**Date:** May 14, 2026

---

## 1. Objectives
- Design and implement a **UART driver** based on the provided SRS.
- Integrate the **Utils module** for string formatting and data conversion.
- Develop a **Serial module** that provides a high-level API for terminal communication.
- Demonstrate real-time telemetry by reporting sensor data to a Serial Monitor (integrated into VS Code).

---

## 2. Background
Serial communication is vital for debugging embedded systems. To send readable information (like `voltage: 2500 mV`), the system must convert numerical data into ASCII strings. By combining a low-level UART driver with a **Serial module** and **Formatting Utilities** (`utils`), developers can create professional terminal interfaces for monitoring system behavior.

---

## 3. Pre-Lab Preparation
- Review the **SRS for the UART driver** ([SRS-UART_Driver](../../SRS/UART/SRS-UART_Driver.md)).
- Review the functions provided in the **Utils module** (`utils_snprintf`, `utils_itoa`, etc.).
- Study the STM32 USART register definitions (`SR`, `DR`, `BRR`, `CR1`) in the Reference Manual ([RM0383-STM32F411XCE](../../Documents/rm0383-stm32f411xce.pdf)).  
- Review GPIO configuration for alternate function mode to configure the UART pins in the microcontroller datasheet ([STM32F411RE](../../Documents/stm32f411re.pdf)).  
- Locate the USART2 TX and RX pins in the user manual of your development board ([UM1724-STM32-NULCEO-64](../../Documents/um1724-stm32-nucleo-64.pdf)).  
- Use Visual Studio Code as your text editor and the terminal (Git Bash) to build and flash the code to the STM32 microcontroller.  
- Ensure the **Serial Monitor extension** is installed in VS Code to view MCU output directly in the IDE.  

---

## 4. Lab Tasks

### Task 1: UART Driver Implementation
- Implement the UART driver functions according to the UART SRS.
- Ensure compliance with functional requirements (FR-1 through FR-5).  

### Task 2: Serial Module Implementation
- Implement functions:  
  - `serial_init`  
  - `serial_printf`  
- Use UART driver functions internally to configure and send string characters.  
- Use Utils module for string formatting and data conversion. 

### Task 3: Application Integration
- Use the **ADC module** to read a potentiometer value.
- Every 500 ms (using a **Timer module** delay), use `serial_printf` to send the following message:
    `"ADC Value: %d | Voltage: %d mV\n"`
- Use `utils_itoa` if manual conversion is required for specific data formatting.

### Task 4: VS Code Integration
- Build and flash the project using the terminal.
- Open the **VS Code Serial Monitor**.
- Configure the port to the ST-Link COM port and the baud rate to **115200**.
- Verify that the telemetry data appears correctly on the screen.

---

## 5. Deliverables
- Source code for: UART driver, GPIO driver, TIM driver, ADC driver, Sensor module, Serial module, and Utils module.  
- Software Design Document (SDD) of the UART driver following the standard template ([SDD_Template](../../SDD/SDD_Template.md)).  
- Lab report documenting:  
  - Design decisions  
  - Test outcomes (Screenshot of Serial Monitor data)  
  - Observed behavior on hardware (UART TX signal on Logic Analyzer or oscilloscope).

---

## 6. Evaluation Criteria
- **Correctness:** Driver functions meet SRS requirements.  
- **Modularity:** Serial module reuse GPIO and UART drivers cleanly.  
- **Documentation:**  
  - Clear lab report with results and discussion.  
  - Clear SDD of the UART driver based on the SRS.  
- **Hardware Validation:** Serial data transmission and TX signal verified on STM32 hardware.  

---
