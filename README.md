# Voltage-Controlled Function Generator (VCFG)

A voltage-controlled function generator producing **square** and **triangular** waveforms using a closed-loop op-amp system.  
The circuit uses a **Schmitt trigger → digital switch → DC-to-±DC converter → integrator** loop.  
Output frequency varies **linearly with control voltage (Vc = 0–5 V)**, and the circuit offers **two selectable ranges** via a switch.  
Both waveforms pass through a **user-adjustable gain stage** (0–8 Vpp).

---

## ⚙️ Overview

- **Control Voltage:** 0–5 V → linear frequency control  
- **Frequency Ranges:**  
  - Range A: 20 Hz – 700 Hz  
  - Range B: 100 Hz – 3.5 kHz  
- **Outputs:** Square + Triangular, each 0–8 Vpp (adjustable)  
- **Op-amps:** LM318N (high-slew, low-distortion)  
- **Power Supply:** ±12 V  
- **Simulation Tool:** NI MultiSIM  

---

## 🔁 System Operation

| Stage | Description |
|--------|--------------|
| **1. Schmitt Trigger** | Generates a stable digital square output that drives the digital switch. |
| **2. Digital Switch** | Directs control logic to the DC-converter based on the Schmitt output. |
| **3. DC → ±DC Converter** | Converts 0–5 V control signal (Vc) into a bipolar control that biases the integrator. This sets the slope → frequency. |
| **4. Integrator** | Integrates the DC-converted signal to create a linear triangular waveform. Output feeds back to the Schmitt to close the loop. |
| **5. Gain Stage** | Independent user-controlled amplifier adjusts both square and triangular outputs between 0–8 Vpp. |

The circuit’s **frequency response** depends on the converter output magnitude; increasing Vc increases the integrator’s slope → higher frequency.  
Switch S1 swaps timing-network components (R/C) to toggle between the two operating ranges.

---

## 📊 Performance

| Parameter | Range A | Range B |
|------------|----------|----------|
| Frequency | 20 – 700 Hz | 100 – 3.5 kHz |
| Control Voltage | 0 – 5 V | 0 – 5 V |
| Output Voltage | 0 – 8 Vpp (user adjustable) | 0 – 8 Vpp (user adjustable) |
| Waveforms | Square + Triangular | Square + Triangular |
| Power | ±12 V | ±12 V |

---

## 🧠 Design Notes
- **LM318N** chosen for its **70 V/µs** slew rate, ensuring waveform linearity at high frequency.  
- **2N3904** + **1N4148** provide current steering for the DC-converter section.  
- **1N5339B Zeners** clamp reference levels for the Schmitt trigger thresholds.  
- The converter ensures that Vc (0–5 V) maps linearly to ±control levels feeding the integrator, maintaining consistent waveform symmetry.  
- Switching network (S1) changes RC time constants for dual-range operation.

---

## 📁 Repository Layout

