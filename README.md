# AC-Motor-Controller
Designed and built a Velleman K2636 AC motor controller to regulate AC motors with carbon brushes, utilizing a Triac for precise phase-cutting control. Implemented variable speed control for motors up to 5.5A current load, ensuring high-torque performance while adhering to sound engineering principles.

Here’s a refined version of your overview and theory of operation for your README file:

---

# Overview

The **Velleman K2636 AC Motor Control Kit** is engineered to control AC motors with carbon brushes, utilizing a unique phase-cutting method that operates once per AC cycle, unlike standard dimmers that operate every half cycle. This design allows for variable speed adjustment from 5% to 95% via a potentiometer, enabling high torque even at low speeds. Additionally, there’s another potentiometer to set the minimum speed of the AC motor.

This kit operates with an input of 115 VAC and provides an output of 6 VAC, designed to run on mains voltage to regulate current flow to the AC motor. Notably, we tested the circuit using a wall socket providing 167 VAC, and it functioned as intended.

![Functional Block Diagram of K2636 AC Motor Controller](https://github.com/danvinn/AC-Motor-Controller/blob/main/Block.png)

The circuit begins with a **power supply block** that feeds AC mains voltage to a transformer. This transformer steps down the high AC voltage from the wall outlet to a suitable lower voltage level for the rest of the circuit. After stepping down the voltage, it travels to the **rectifier block**, which converts the AC waveform into pulsating DC voltage. The **filter block** smooths out any fluctuations, providing a steadier DC voltage output for the control circuit.

The **control circuit block** acts as the brain of the operation, using the steady DC voltage to control the **Triac block**. By generating a specific control signal, the control circuit regulates how much power is delivered to the AC motor, effectively acting as a variable resistor for AC current.

# Theory of Operation

The **K2636 AC Motor Controller** consists of five main sections that drive its operation. Below is the circuit schematic, showcasing how current flows throughout the system to operate the motor.

![Overall Schematic of K2636 AC Motor Controller](https://github.com/danvinn/AC-Motor-Controller/blob/main/Schematic.png)

- **Section 1:** The power supply accepts an input of 110 - 240 VAC. For this demonstration, it provides 115 VAC to the circuit, with a 6-0-6 center-tapped transformer stepping down the voltage to 6 VAC, ideally achieving a 19:1 ratio.

- **Section 2:** The rectifier, composed of two 1N4007 diodes and two 1N4148 diodes, converts AC voltage from the transformer into unregulated pulsating DC voltage.

- **Section 3:** The control circuit employs analog components such as resistors, capacitors, potentiometers, and transistors to control the Triac (BT137F-600 voltage regulator), which regulates power to the load. The control circuit sends a pulse to the gate terminal of the Triac at a precise moment relative to the AC waveform. This triggers the Triac’s regenerative switching action, allowing current to flow as long as it exceeds the gate pulse. The Triac turns off when the current drops below the holding current level at the zero-crossing points of the AC waveform. This section includes a 3 mm red LED, which verifies functionality and indicates that sufficient voltage is present.

- **Section 4:** The Pi-filter consists of a 1 mH inductor and two 470 nF capacitors, smoothing out fluctuations in current. The inductor opposes changes in current, helping to maintain steady flow, while the capacitors store and release energy to stabilize the DC voltage output.

- **Section 5:** This section contains additional transistors, diodes, and resistors to maintain voltage regulation and ensure a consistent current flow through the circuit, effectively creating a voltage divider that feeds a specific portion of current to the load.

The circuit regulates a maximum power of 1200W at 240V (max. 5A). A jumper wire must be soldered to specify whether the circuit runs on US or UK mains voltage; we configured it for US mains voltage at 120V and 60 Hz.

---
