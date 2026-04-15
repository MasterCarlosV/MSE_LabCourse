
---

# Software Requirements Specification (SRS)  
**Module:** Timer (TIM) Driver  
**Version:** 1.0  
**Author:** Carlos Villarreal

---

## 1. Introduction

### 1.1 Purpose  
This document defines the requirements for the TIM driver module. The driver provides standardized functions for initializing timers, configuring time intervals or frequencies, and controlling capture/compare channels in STM32 microcontrollers.

### 1.2 Scope  
The TIM driver will be integrated into embedded firmware to manage hardware timers. It supports multiple timers and channels, enabling developers to configure periodic events, PWM signals, and compare operations efficiently.

### 1.3 Definitions, Acronyms, and Abbreviations  

| **Term** | **Definition** |
|------|------------|
| TIM  | Timer peripheral in STM32 microcontrollers |
| PSC  | Prescaler register, divides input clock |
| ARR  | Auto-Reload Register, defines timer period |
| PWM  | Pulse Width Modulation |
| Channel | Capture/Compare channel within a timer |

### 1.4 References  
- Recommended Practice for Software Requirements Specifications: [IEEE Std 830-1998](https://ieeexplore.ieee.org/document/720574)
- Microcontroller datasheet: [STM32F411RE](../../Documents/stm32f411re.pdf)
- Microcontoller reference manual: [RM0383-STM32F411xC/E](../../Documents/rm0383-stm32f411xce.pdf)

---

## 2. Overall Description

### 2.1 Product Perspective  
The TIM driver is a low-level software component that interfaces directly with STM32 TIM hardware registers. It provides abstraction for higher-level modules requiring precise timing and signal generation.

### 2.2 Product Functions  
- Initialize TIM subsystem and individual timers  
- Configure timers by time interval (ms) or frequency (Hz)  
- Enable and disable timers  
- Configure capture/compare channels for PWM or event triggering  
- Set compare thresholds and modes  
- Wait for timer events  
- Disable capture/compare channels  

### 2.3 User Characteristics  
Intended users are embedded software developers with knowledge of C programming and STM32 hardware.

### 2.4 Constraints  
- Must be implemented in C language  
- Must be portable across STM32 families supporting TIM peripherals  
- Must operate within real-time constraints  
- ARR and PSC values must fit within hardware register limits  

### 2.5 Assumptions and Dependencies  
- Hardware provides TIM functionality with accessible registers  
- System clock and power management are configured externally  

---

## 3. System Features

### 3.1 `tim_init`  
**Description:** Initializes the TIM subsystem.  
**Functional Requirements:**  
- FR-1: The system shall configure all TIM peripherals to a default state.  


### 3.2 `tim_initTimer`  
**Description:** Initializes a specific TIM peripheral.  
**Functional Requirements:**  
- FR-2: The system shall enable clocking and configure the specified timer.  

### 3.3 `tim_setTimerMs`  
**Description:** Configures a timer with a specified time interval in milliseconds.  
**Functional Requirements:**  
- FR-3: The system shall calculate PSC and ARR values to achieve the requested interval.  

### 3.4 `tim_setTimerFreq`  
**Description:** Configures a timer with a specified frequency in Hz.  
**Functional Requirements:**  
- FR-4: The system shall calculate PSC and ARR values to achieve the requested frequency.  

### 3.5 `tim_enableTimer`  
**Description:** Enables and starts a timer.  
**Functional Requirements:**  
- FR-5: The system shall start counting and generate update events.  

### 3.6 `tim_disableTimer`  
**Description:** Disables a specific timer.  
**Functional Requirements:**  
- FR-6: The system shall stop the specified timer from counting and generating events.  

### 3.7 `tim_waitTimer`  
**Description:** Waits until the specified timer completes its current cycle.  
**Functional Requirements:**  
- FR-7: The system shall block execution until the timer reaches its overflow/update event.  

### 3.8`tim_setTimerCompareChannelValue`  
**Description:** Sets the threshold value for a capture/compare channel.  
**Functional Requirements:**  
- FR-8: The system shall trigger a compare event when the counter reaches the threshold.  

### 3.9 `tim_setTimerCompareMode`  
**Description:** Configures the compare mode (e.g., PWM mode).  
**Functional Requirements:**  
- FR-9: The system shall allow configuration of compare modes using register settings.  

### 3.10 `tim_enableTimerCompareChannel`  
**Description:** Enables a specific capture/compare channel.  
**Functional Requirements:**  
- FR-10: The system shall activate the specified channel to generate compare events.  

### 3.11 `tim_disableTimerCompareChannel`  
**Description:** Disables a specific capture/compare channel.  
**Functional Requirements:**  
- FR-11: The system shall deactivate the specified channel, preventing compare events.  

---

## 4. External Interface Requirements

### 4.1 Hardware Interfaces  
- TIM registers accessible via STM32 hardware.  

### 4.2 Software Interfaces  
- C language API exposed through header files.  

### 4.3 Communication Interfaces  
- No external communication required; operates locally on hardware.  

---

## 5. Non-Functional Requirements

- NFR-1: The driver shall be lightweight and efficient.  
- NFR-2: The driver shall provide error handling for invalid timer or channel inputs.  
- NFR-3: The driver shall meet real-time performance constraints.   

---

## 6. Other Requirements  
- Documentation shall include usage examples for interval timers, frequency timers, and PWM configuration.  

---
