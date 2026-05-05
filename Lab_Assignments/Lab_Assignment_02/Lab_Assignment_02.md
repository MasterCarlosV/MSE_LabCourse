
---

# Lab Assignment: TIM Driver Development and Application  

**Course:** Microcontrollers and Embedded Systems  
**Lab Title:** TIM Driver Implementation and Delay/PWM Application  
**Author:** Carlos Villarreal  
**Date:** April 15, 2026  

---

## 1. Objectives
- Design and implement a TIM driver based on the provided Software Requirements Specification (SRS).  
- Develop a **Timer module** that generates delays using hardware timers.  
- Develop a **PWM module** that generates a PWM output signal on a GPIO pin.  
- Demonstrate modular design and hardware abstraction principles.  

---

## 2. Background
Timer (TIM) peripherals in STM32 microcontrollers are essential for time-based operations such as delays, periodic events, and PWM signal generation. A reusable TIM driver simplifies application development by abstracting hardware details and providing a clean API.  

PWM signals are widely used in embedded systems for motor control, LED dimming, and communication protocols. By combining the TIM driver with GPIO output, students can generate PWM signals and verify them using an oscilloscope or logic analyzer.  

---

## 3. Pre-Lab Preparation
- Review the **SRS for the GPIO driver** ([SRS-GPIO_Driver](../../SRS/GPIO/SRS-GPIO_Driver.md)).
- Review the **SRS for the TIM driver** ([SRS-TIM_Driver](../../SRS/TIM/SRS-TIM_Driver.md)).  
- Study STM32 GPIO register definitions (`MODER`, `AFRx`) in the Reference Manual ([RM0383-STM32F411XCE](../../Documents/rm0383-stm32f411xce.pdf)).  
- Study STM32 TIM register definitions (`PSC`, `ARR`, `CNT`, `CCRx`, `CCMRx`, `CR1`, `SR`, `CCER`, clock enable registers) in the Reference Manual ([RM0383-STM32F411XCE](../../Documents/rm0383-stm32f411xce.pdf)).  
- Review GPIO configuration for alternate function mode to output PWM signals in the microcontroller datasheet ([STM32F411RE](../../Documents/stm32f411re.pdf)).  
- Locate the pins connected to the user LED or external header for PWM output in the user manual of your development board ([UM1724-STM32-NULCEO-64](../../Documents/um1724-stm32-nucleo-64.pdf)).  
- Use Visual Studio Code as your text editor and the terminal (Git Bash) to build and flash the code to the STM32 microcontroller.  

---

## 4. Lab Tasks

### Task 1: TIM Driver Implementation
- Implement the TIM driver functions as defined in the TIM SRS.  
- Ensure compliance with functional requirements (FR-1 through FR-11).  
- Provide error handling for invalid timer or channel inputs.  

### Task 2: GPIO Alternate Function Implementation
- Implement the new GPIO driver functions as defined in the updated GPIO SRS.  
- Ensure compliance with functional requirements (FR-8).  
- Provide error handling for invalid ports, pins or alternate function mode inputs. 

### Task 3: Timer Module (Delay Generation)
- Implement functions:  
  - `timer_init`  
  - `timer_delay_ms`  
- Use TIM driver functions internally to configure timers for delay generation.  
- Verify delay accuracy using an oscilloscope or LED blink test.  

### Task 4: PWM Module
- Implement functions:  
  - `pwm_init`  
  - `pwm_setSignal`
  - `pwm_start`  
  - `pwm_stop`  
- Use TIM driver functions internally to configure capture/compare channels in PWM mode.  
- Output PWM signal on a GPIO pin configured in alternate function mode.  
- Verify PWM frequency and duty cycle using an oscilloscope.  

### Task 5: Application Integration
- Configure one timer for delay generation (e.g., blinking LED every 500 ms).  
- Configure another timer for PWM generation on a GPIO pin (e.g., LED dimming with 50% duty cycle).  
- Demonstrate both modules working simultaneously.  

---

## 5. Deliverables
- Source code for the TIM driver, GPIO driver, Timer module, PWM module and LED module.  
- Software Design Document (SDD) of the TIM driver based on the template ([SDD_Template](../../SDD/SDD_Template.md)).
- Updated Software Design Document (SDD) of the GPIO driver based on the template ([SDD_Template](../../SDD/SDD_Template.md)).  
- Lab report documenting:  
  - Design decisions  
  - Test outcomes  
  - Observed behavior on hardware (LED blink timing, PWM waveform verification)  

---

## 6. Evaluation Criteria
- **Correctness:** Driver functions meet SRS requirements.  
- **Modularity:** Timer and PWM modules reuse TIM driver cleanly.  
- **Documentation:**  
  - Clear lab report with results and discussion.  
  - Clear SDD of the TIM driver based on the SRS. 
  - Clear SDD of the updated GPIO driver based on the SRS. 
- **Hardware Validation:** PWM waveform and delay timing verified on STM32 hardware.  

---
