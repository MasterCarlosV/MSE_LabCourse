
---

# Software Requirements Specification (SRS)  
**Module:** I2C Driver  
**Version:** 1.0  
**Author:** Carlos Villarreal  

---

## 1. Introduction

### 1.1 Purpose  
This document defines the requirements for the I2C driver module. The driver provides standardized functions for initializing the I2C peripheral, writing data to devices, and reading data from devices using register-based or direct addressing.

### 1.2 Scope  
The I2C driver will be integrated into embedded firmware to manage communication with external devices such as sensors, EEPROMs, and displays. It supports both register-based and direct device transactions, enabling developers to implement reliable I2C communication in STM32 microcontrollers.

### 1.3 Definitions, Acronyms, and Abbreviations  

| **Term** | **Definition** |
|----------|----------------|
| I2C      | Inter-Integrated Circuit, a serial communication protocol |
| Address  | 7-bit or 10-bit unique identifier for an I2C device |
| Register | Internal memory location within an I2C device |
| ACK/NACK | Acknowledge/Not Acknowledge signals used in I2C transactions |

### 1.4 References  
- Recommended Practice for Software Requirements Specifications: [IEEE Std 830-1998](https://ieeexplore.ieee.org/document/720574).  
- Microcontroller datasheet: [STM32F411RE](../../Documents/stm32f411re.pdf).  
- Microcontroller reference manual: [RM0383-STM32F411xC/E](../../Documents/rm0383-stm32f411xce.pdf).  

---

## 2. Overall Description

### 2.1 Product Perspective  
The I2C driver is a low-level software component that interfaces directly with STM32 I2C hardware registers. It provides abstraction for higher-level modules requiring communication with external I2C devices.

### 2.2 Product Functions  
- Initialize I2C subsystem  
- Write data to a device register  
- Write data directly to a device  
- Read data from a device register  
- Read data directly from a device  

### 2.3 User Characteristics  
Intended users are embedded software developers with knowledge of C programming and STM32 hardware.

### 2.4 Constraints  
- Must be implemented in C language  
- Must be portable across STM32 families supporting I2C peripherals  
- Must operate within real-time constraints  
- Device addresses must conform to I2C protocol standards  

### 2.5 Assumptions and Dependencies  
- Hardware provides I2C functionality with accessible registers  
- System clock and power management are configured externally  

---

## 3. System Features

### 3.1 `i2c_init`  
**Description:** Initializes the I2C subsystem.  
**Functional Requirements:**  
- FR-1: The system shall configure the I2C peripheral to a default state.  
- FR-2: The system shall enable clocking for I2C hardware.  

### 3.2 `i2c_writeRegDevice`  
**Description:** Writes data to a specific register of an I2C device.  
**Functional Requirements:**  
- FR-3: The system shall send the device address and register address.  
- FR-4: The system shall transmit multiple bytes of data to the device.

### 3.3 `i2c_writeDevice`  
**Description:** Writes data directly to an I2C device without specifying a register.  
**Functional Requirements:**  
- FR-5: The system shall send the device address.  
- FR-6: The system shall transmit multiple bytes of data to the device.

### 3.4 `i2c_readRegDevice`  
**Description:** Reads data from a specific register of an I2C device.  
**Functional Requirements:**  
- FR-7: The system shall send the device address and register address.  
- FR-8: The system shall read multiple bytes of data into a data buffer.  

### 3.5 `i2c_readDevice`  
**Description:** Reads data directly from an I2C device without specifying a register.  
**Functional Requirements:**  
- FR-9: The system shall send the device address.  
- FR-10: The system shall read multiple bytes of data into a data buffer.  

---

## 4. External Interface Requirements

### 4.1 Hardware Interfaces  
- I2C registers accessible via STM32 hardware.  

### 4.2 Software Interfaces  
- C language API exposed through header files.  

### 4.3 Communication Interfaces  
- I2C bus communication with external devices.  

---

## 5. Non-Functional Requirements

- NFR-1: The driver shall be lightweight and efficient.  
- NFR-2: The driver shall provide error handling for invalid device addresses, invalid buffer pointers or bus errors.  
- NFR-3: The driver shall meet real-time performance constraints.  

---

## 6. Other Requirements  
- Documentation shall include usage examples for register-based and direct device communication.  

---
