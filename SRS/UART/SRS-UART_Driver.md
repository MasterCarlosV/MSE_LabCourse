
---

# Software Requirements Specification (SRS)
**Module:** UART Driver  
**Version:** 1.0  
**Author:** Carlos Villarreal  

---

## 1. Introduction
### 1.1. Purpose
This document defines the requirements for the UART driver module. The driver provides standardized functions for initializing the peripheral, configuring the baud rate, and transmitting raw data via the USART2 interface on STM32 microcontrollers.

### 1.2. Scope
The UART driver will be integrated into embedded firmware to enable serial communication. It focuses on low-level register manipulation for the USART2 peripheral, supporting asynchronous transmission.

### 1.3. Definitions, Acronyms, and Abbreviations
| **Term** | **Definition** |
| :--- | :--- |
| USART | Universal Synchronous Asynchronous Receiver Transmitter |
| Baud Rate | Speed of communication in bits per second (bps) |
| TXE | Transmit Data Register Empty flag |
| TE | Transmitter Enable |
| UE | USART Enable |

### 1.4. References
- Recommended Practice for Software Requirements Specifications: [IEEE Std 830-1998](https://ieeexplore.ieee.org/document/720574).
- Microcontroller datasheet: [STM32F411RE](../../Documents/stm32f411re.pdf).
- Microcontroller reference manual: [RM0383-STM32F411xC/E](../../Documents/rm0383-stm32f411xce.pdf).

---

## 2. Overall Description
### 2.1. Product Perspective
The UART driver is a low-level software component that interfaces directly with STM32 hardware registers. It serves as the foundation for higher-level communication modules like the **Serial Module**.

### 2.2. Product Functions
- Initialize the UART peripheral and clocking.
- Set communication baud rate.
- Transmit a single byte of data to the terminal.

### 2.3. Constraints
- Must be implemented in C language.
- Must operate within real-time constraints.
- Data transmission must check the hardware status flag (`TXE`) before writing to the data register.

---

## 3. System Features

### 3.1. `uart_init`
- **Description:** Initializes the USART2 hardware.
- **Functional Requirements:**
    - FR-1: The system shall enable the clock for the USART2 peripheral.
    - FR-2: The system shall configure the baud rate based on the system clock.
    - FR-3: The system shall enable the transmitter and the peripheral.

### 3.2. `uart_write`
- **Description:** Transmits a single byte of data.
- **Functional Requirements:**
    - FR-4: The system shall wait until the Transmit Data Register is empty.
    - FR-5: The system shall write the 8-bit character to the data register for transmission.

---

## 4. External Interface Requirements

### 4.1 Hardware Interfaces  
- UART registers accessible via STM32 hardware.  

### 4.2 Software Interfaces  
- C language API exposed through header files.  

### 4.3 Communication Interfaces  
- External communication required; the hardware shall be able to communcate to a serial terminal in a PC.  

---

## 5. Non-Functional Requirements

- NFR-1: The driver shall be lightweight and efficient.   
- NFR-2: The driver shall meet real-time performance constraints.   

---

## 6. Other Requirements  
- Documentation shall include usage examples for baud rate configuration and data transmission.  

---
