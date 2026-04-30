
---

# Software Requirements Specification (SRS)  
**Module:** ADC Driver  
**Version:** 1.0  
**Author:** Carlos Villarreal  

---

## 1. Introduction

### 1.1 Purpose  
This document defines the requirements for the ADC driver module. The driver provides standardized functions for initializing ADC peripherals, configuring sampling channels, and retrieving digital conversion results from analog inputs in STM32 microcontrollers.

### 1.2 Scope  
The ADC driver will be integrated into embedded firmware to manage analog-to-digital conversions. It supports multiple ADC instances and channels, enabling developers to measure analog signals such as sensor outputs and voltage levels efficiently.

### 1.3 Definitions, Acronyms, and Abbreviations  

| **Term** | **Definition** |
|----------|----------------|
| ADC      | Analog-to-Digital Converter peripheral |
| Channel  | Input line connected to ADC multiplexer |
| Injected Channel | Special ADC channel triggered by external events |
| Resolution | Number of bits in the digital conversion result (e.g., 12-bit) |
| Vref     | Reference voltage used for conversion scaling |

### 1.4 References  
- Recommended Practice for Software Requirements Specifications: [IEEE Std 830-1998](https://ieeexplore.ieee.org/document/720574)
- Microcontroller datasheet: [STM32F411RE](../../Documents/stm32f411re.pdf)
- Microcontroller reference manual: [RM0383-STM32F411xC/E](../../Documents/rm0383-stm32f411xce.pdf)

---

## 2. Overall Description

### 2.1 Product Perspective  
The ADC driver is a low-level software component that interfaces directly with STM32 ADC hardware registers. It provides abstraction for higher-level modules requiring analog signal measurement.

### 2.2 Product Functions  
- Initialize ADC subsystem  
- Enable ADC peripherals  
- Configure regular and injected channels  
- Start single, continuous, or injected conversions  
- Read conversion results  

### 2.3 User Characteristics  
Intended users are embedded software developers with knowledge of C programming and STM32 hardware.

### 2.4 Constraints  
- Must be implemented in C language  
- Must be portable across STM32 families supporting ADC peripherals  
- Must operate within real-time constraints  

### 2.5 Assumptions and Dependencies  
- Hardware provides ADC functionality with accessible registers  
- System clock and reference voltage are configured externally  

---

## 3. System Features

### 3.1 `adc_init`  
**Description:** Initializes the ADC subsystem.  
**Functional Requirements:**  
- FR-1: The system shall enable clocking and configure all ADC peripherals to a default state.  

### 3.2 `adc_enableAdc`  
**Description:** Enables the ADC instance.  
**Functional Requirements:**  
- FR-2: The system shall activate the ADC for conversions.  

### 3.3 `adc_setChannel`  
**Description:** Configures a regular ADC channel.  
**Functional Requirements:**  
- FR-3: The system shall allow selection of valid channels.  

### 3.4 `adc_setInjectedChannel`  
**Description:** Configures an injected ADC channel.  
**Functional Requirements:**  
- FR-4: The system shall allow selection of valid injected channels.  

### 3.5 `adc_startSingleConversion`  
**Description:** Starts a single conversion on the configured channel.  
**Functional Requirements:**  
- FR-5: The system shall begin conversion and set status flags.  

### 3.6 `adc_startContinuousConversion`  
**Description:** Starts continuous conversions.  
**Functional Requirements:**  
- FR-6: The system shall repeatedly convert input signals until stopped.  

### 3.7 `adc_startInjectedConversion`  
**Description:** Starts conversion on an injected channel.  
**Functional Requirements:**  
- FR-7: The system shall trigger conversion based on external events.  

### 3.8 `adc_readData`  
**Description:** Reads the result of the last regular conversion.  
**Functional Requirements:**  
- FR-8: The system shall return the digital value corresponding to the analog input.  

### 3.9 `adc_readInjectedChannelData`  
**Description:** Reads the result of the last injected channel conversion.  
**Functional Requirements:**  
- FR-9: The system shall return the digital value for the specified injected channel.  

---

## 4. External Interface Requirements

### 4.1 Hardware Interfaces  
- ADC registers accessible via STM32 hardware.  

### 4.2 Software Interfaces  
- C language API exposed through header files.  

### 4.3 Communication Interfaces  
- No external communication required; operates locally on hardware.  

---

## 5. Non-Functional Requirements

- NFR-1: The driver shall be lightweight and efficient.  
- NFR-2: The driver shall provide error handling for invalid ADC instance or channel inputs.  
- NFR-3: The driver shall meet real-time performance constraints.  

---

## 6. Other Requirements  
- Documentation shall include usage examples for single, continuous, and injected conversions.  

---
