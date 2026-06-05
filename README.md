# Live-ECG-in-FM-Telemetry-System

## Overview

This project presents the design and implementation of a live Electrocardiogram (ECG) telemetry system using Frequency Modulation (FM). The system acquires low-amplitude ECG signals through surface electrodes, amplifies them using an AD620 instrumentation amplifier, and transmits them via an FM-modulated analog communication channel.

At the receiver, the signal is demodulated using a slope detector and low-pass filtering to recover the original ECG waveform. The recovered signal is verified using a Digital Storage Oscilloscope (DSO), demonstrating reliable transmission of biomedical signals with improved noise immunity.

---

## Objectives

- Acquire real-time ECG signals using Ag/AgCl electrodes
- Amplify weak ECG signals using an AD620 instrumentation amplifier
- Implement FM modulation using an LM358-based Voltage Controlled Oscillator (VCO)
- Transmit ECG signals through an analog communication channel
- Recover the ECG waveform using slope detector demodulation
- Validate signal recovery using oscilloscope measurements

---

## System Architecture

```text
ECG Electrodes
      ↓
AD620 Instrumentation Amplifier
      ↓
Signal Conditioning (HPF + LPF)
      ↓
FM Modulator (LM358 VCO)
      ↓
Analog Communication Channel
      ↓
Differentiator
      ↓
Envelope Detector (1N4148)
      ↓
Low-Pass Filter
      ↓
Recovered ECG Signal (DSO)
```

---

## Components Used

### Signal Acquisition

- Ag/AgCl ECG Electrodes
- Lead Wires (RA, LA, RL)

### Signal Conditioning

- AD620 Instrumentation Amplifier
- LM358 / LM741 Operational Amplifiers
- Resistors and Capacitors

### Modulation & Demodulation

- LM358 Voltage Controlled Oscillator
- 1N4148 Diode (Slope Detector)

### Measurement

- Keysight DSOX1204A Digital Storage Oscilloscope

### Power Supply

- Dual ±9V DC Supply

### Hardware

- Breadboard
- Connecting Wires

---

## Working Principle

### 1. ECG Signal Acquisition

Surface electrodes capture the electrical activity of the heart in a standard Lead I / Lead II configuration. The acquired ECG signal typically has:

- Amplitude: 1–3 mV
- Frequency Range: 0.05–150 Hz

---

### 2. Signal Amplification

The ECG signal is amplified using an AD620 instrumentation amplifier.

Key advantages:

- High CMRR (>100 dB)
- Low noise amplification
- Excellent rejection of power-line interference
- Adjustable gain through external resistor (Rg)

---

### 3. Signal Conditioning

The amplified signal is filtered using:

- High-Pass Filter (HPF) to remove baseline wander and DC offset
- Low-Pass Filter (LPF) to suppress high-frequency noise

---

### 4. FM Modulation

The conditioned ECG signal drives an LM358 configured as a Voltage Controlled Oscillator (VCO).

Features:

- Carrier Frequency ≈ 5 kHz
- Instantaneous frequency varies according to ECG amplitude
- Constant amplitude improves noise immunity during transmission

---

### 5. Transmission

The FM signal is transmitted through an analog communication channel.

Advantages of FM:

- Resistance to amplitude-based noise
- Improved signal integrity
- Better reliability than direct ECG transmission

---

### 6. Demodulation

A slope detector is used for FM demodulation.

Components:

- RC Differentiator
- 1N4148 Envelope Detector
- Low-Pass Smoothing Filter

The recovered baseband signal corresponds to the original ECG waveform.

---

### 7. Signal Verification

The recovered ECG signal is displayed on a Digital Storage Oscilloscope (DSO) and compared with the original waveform to evaluate transmission fidelity.

---

## Circuit Modules

### Dual Power Supply

Provides ±9V supply rails required for analog signal processing.

### ECG Amplifier

- AD620 Instrumentation Amplifier
- ECG amplification from 1–3 mV to approximately 50–150 mV

### FM Modulator

- LM358-based VCO
- Frequency proportional to ECG voltage

### FM Demodulator

- Differentiator
- Envelope Detector
- Low-Pass Filter

---

## Experimental Results

| Parameter | Observed Value |
|------------|---------------|
| Raw ECG Signal | 1–3 mV |
| Amplified ECG | 50–150 mV |
| FM Carrier Frequency | ~5 kHz |
| FM Signal Amplitude | Constant |
| Recovered ECG | 40–120 mV |

---

## Key Observations

- Characteristic ECG features (P-wave, QRS complex, and T-wave) were successfully captured.
- FM modulation preserved signal integrity during transmission.
- Demodulated ECG waveform closely matched the original signal.
- High common-mode noise rejection was achieved using the AD620.
- FM transmission demonstrated superior noise immunity compared to direct transmission methods.

---

## Applications

- Wireless Patient Monitoring
- ICU and Ambulance Telemetry
- Remote Cardiac Monitoring
- Telemedicine Systems
- Wearable ECG Devices
- Biomedical Instrumentation Education

---

## Future Improvements

- Replace wired analog channel with RF wireless communication
- Implement PLL-based FM demodulation for higher accuracy
- Add digital signal processing for advanced noise removal
- Integrate microcontroller-based data logging
- Develop a portable battery-powered telemetry unit

---

## Repository Structure

```text
.
├── README.md
├── images/
│   ├── block_diagram.png
│   ├── transmitter_circuit.jpg
│   ├── receiver_circuit.jpg
│   ├── oscilloscope_output.jpg
│   └── setup.jpg
├── report/
│   └── ECG_FM_Telemetry_Project_Report.pdf
```

## Authors

- Shreya Das
- Sanjana B
- Kashika Tolani

### Guide

Dr. Christina Josephine Malathi A  
Department of Communication Engineering  
Vellore Institute of Technology

---

## License

This project was developed for academic and educational purposes.
