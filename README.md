# Wireless Communication System – SDR-Based Implementation

This project presents a full-stack wireless communication system, designed and built using embedded hardware, analog circuits, RF components, and MATLAB-based SDR tools. Developed as part of the **CSE 4377/5392 Wireless Communication** course at UT Arlington, it represents a practical exploration of modern wireless system design.

> ⚠️ **Note**: Firmware and source code are not included in this repository to preserve academic integrity. This repository is for documentation and visual reference only.



## Project Overview

The system implements a baseband-to-RF digital communication chain, featuring:

- **Custom Embedded Transmitter**  
  A TM4C123GXL microcontroller runs a custom-built **numerically controlled oscillator (NCO)** and waveform generator. This module digitally synthesizes modulated signals such as BPSK, QPSK, and 16-QAM by reading from lookup tables and outputting them via a 12-bit DAC.

- **Signal Shaping and Conditioning**  
  Signals are shaped using **raised cosine filters**, and optional hard clipping is applied to study **nonlinear effects** and **spectral regrowth** in analog circuits.

- **Analog Front-End**  
  The analog output chain includes op-amp level shifters and mixers to produce a wide range of carrier frequencies. Signals are transmitted using a custom-designed patch antenna.

- **2.4 GHz Patch Antenna**  
  A microstrip patch antenna was designed in **KiCad**, simulated in **MATLAB**, fabricated, and tested for gain and radiation pattern performance.

- **Wireless Reception and Demodulation**  
  Signals are captured using an **RTL-SDR** dongle through a Raspberry Pi and processed in **MATLAB** for frequency correction, filtering, symbol recovery, and **bit error rate (BER)** analysis.



## Tools & Technologies

- **Hardware**: TI TM4C123GXL, Raspberry Pi 4, MCP4822 DAC, TLC072 op-amps, RTL-SDR v3.
- **Software**: MATLAB, KiCad, SerialTools, SDR#, Code Composer Studio, Embedded C.
- **Test Equipment**: Oscilloscope, spectrum analyzer, RF signal generator.



## System Architecture

The wireless transmission system is built from the ground up, with each stage independently verified and integrated into a complete pipeline.



## Key Technical Contributions

✅ **Custom Numerically Controlled Oscillator (NCO)**  
  Implemented in C on the TM4C123GXL, the NCO generates high-precision baseband signals based on phase accumulation and lookup tables. It forms the core of the digital modulation scheme.

✅ **Multi-Scheme Modulation Support**  
  The firmware supports BPSK, QPSK, 8-PSK, and 16-QAM using compact lookup tables and symbol mappers.
  In addition to outputting SIN and COS waves across various frequencies with a clipping feature.

✅ **Analog Signal Conditioning**  
  Hardware circuits perform level shifting and IF mixing. Experiments include amplifier compression and spectral analysis of clipped waveforms.

✅ **Antenna Design and Fabrication**  
  Designed a 2.4 GHz rectangular patch antenna with a ground plane and microstrip feed. Simulations matched fabricated measurements closely.

✅ **MATLAB-Based SDR Receiver**  
  Offline scripts process the captured IQ data, apply matched filtering, frequency offset correction, and symbol recovery for BER analysis.


## Visual Highlights

### DAC Connected to the Microcontroller
![NCO](https://github.com/user-attachments/assets/4b1a3405-789c-421b-8b21-fc93a9fec5a3)

### Custom Modulated Output (QPSK)
![QPSK](https://github.com/user-attachments/assets/cff75268-b755-4d3b-aef4-09d316d5cb61)

### DAC Output (SIN+iCOS)
![SINCOS](https://github.com/user-attachments/assets/c5a4b500-654b-4ce0-81f0-ce2f4ab5dbcf)

### Clipping and Spectral Distortion
![clipping](https://github.com/user-attachments/assets/87988d6b-23a1-4167-b97a-458a30e5da41)
![distortion](https://github.com/user-attachments/assets/04b7f53e-f9d6-4e04-b1f6-22233a6eab54)

### Custom 2.4 GHz Patch Antenna
![antenna](https://github.com/user-attachments/assets/cc019902-feed-49db-9fde-f13353e19373)
![optimization](https://github.com/user-attachments/assets/dcde66e1-11d0-4b9e-945f-2a208a697e94)



## 📊 Results Snapshot

| Metric                        | Result                                 |
|------------------------------|----------------------------------------|
| Carrier Frequency (IF)       | 27.1 MHz                                |
| Symbol Rates Supported       | 10 kSym/s to 100 kSym/s                 |
| Clipping Threshold Tested    | 0.2V to 0.5V                            |
| Patch Antenna RX Power       | ~ -70 dBm at 2.34 GHz, 17" separation   |
| BER (Low-SNR Capture)        | ~46% on QPSK with offset correction     |



## Outcomes

- Developed a working NCO and embedded waveform generator
- Integrated DAC and op-amp hardware to build analog front-end
- Designed and simulated antennas from scratch
- Captured and demodulated real RF signals using SDR tools
- Gained insight into non-ideal effects like clipping, offset, and noise


## NOTE

This repository is for educational and documentation purposes only. No code is shared to protect academic integrity and maintain the value of future coursework.


## 🙏 Acknowledgements

- **Dr. Jason Losh** - Being a great mentor throughout this project.
- **UTA EE Makerspace** - For printing many of my failed antennae for cheap.
