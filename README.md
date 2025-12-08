# quantum-inspired-dsp

This repository contains the Max/MSP and Max for Live implementation of a real-time digital signal processing (DSP) model that transforms incoming audio using the temporal evolution of the quantum harmonic oscillator (QHO). The system applies coherent and kitten-state dynamics as spectral modulation masks, making quantum behavior directly audible through frame-by-frame spectral deformation.


## 1. Conceptual Basis

This DSP model takes as input a sound and transforms it by applying the time evolution of the QHO wavefunction.  
The evolution of coherent states and their superpositions (“kitten states”) is used as a dynamic control structure that modulates the spectral content of the signal in real time.

Each time step of the simulated wavefunction corresponds to one modulation frame.  
These frames are stored as matrices (e.g., 2048×512, 4096×512) and applied directly to FFT-domain audio, creating a continuous link between quantum dynamics and timbre.



## max-msp/

Core patches and simulation data:

- **FG_Spectral_DSP.maxpat** — Main DSP engine implementing FFT analysis, quantum-informed modulation, and resynthesis.  
- **SpectralFFT.maxpat** — Supporting patch for spectral analysis and reconstruction.  
- **Simulation matrices (.txt)**:  
  - `real_psi_coherent_coll_2048x512.txt`  
  - `real_psi_kitten_coll_4096x512.txt`  

These contain precomputed simulations of coherent and kitten states used as modulation masks.


## MaxForLive/

A Max for Live device enabling performance integration inside Ableton Live.

It provides access to parameters such as:

- Dry/Wet control  
- Selection of quantum states (coherent or kitten states)  
- Simulation freeze toggle  
- Temporal velocity of quantum evolution  
- Amplitude scaling  
- Zoom (focus on specific matrix regions)  
- Spatial offset of the modulation mask  

This interface enables expressive real-time interaction with quantum-inspired timbral transformations.


## 2. DSP Architecture and Signal Flow

### **Stage 1 — Spectral Analysis**  
Incoming audio is segmented into short windows and transformed to the frequency domain using FFT.  
Each spectral bin is represented in polar coordinates (magnitude and phase).

### **Stage 2 — Quantum-Informed Modulation**  
For every spectral frame:

1. A row from the quantum simulation matrix is selected (time step).  
2. The row is normalized and scaled.  
3. Each frequency bin is multiplied by the corresponding value in the mask.  

This deformation reshapes the spectral profile according to the evolving structure of the QHO wavefunction or kitten-state interference.

### **Stage 3 — Resynthesis**  
The processed data is returned to Cartesian coordinates and transformed back to the time domain via inverse FFT, producing a continuously evolving timbral transformation.


## 3. Quantum Simulation Data

Quantum states were simulated in Python by numerically solving the time-dependent Schrödinger equation for the QHO.

Simulation details:

- Spatial domain: 512 points in \([-5, 5]\)  
- Temporal evolution: 2048 steps (one oscillator period)  
- States included:
  - Coherent states  
  - Kitten states (2–4 components with phase offsets)

Each row of the matrix corresponds to the real part of the normalized wavefunction at a specific time step.

These matrices drive the spectral shaping in the DSP engine.


## 4. Artistic Potential

The DSP model is conceived as a performance-oriented tool that expands creative possibilities for musicians and sound artists.

The Max for Live device integrates:

- Real-time spectral transformation  
- Quantum-state exploration  
- MIDI-mapped parameters for expressive control  

This tool also serves educational and outreach purposes, offering an accessible way to engage with complex quantum behaviors through sound.

Future developments aim to refine interaction design, collaborate with performers, and explore a standalone hardware implementation (e.g., pedal-based unit).

## 5. Requirements

- Max/MSP 8+  
- Ableton Live + Max for Live (optional)


**Felipe González de la Maza**  
Based on research conducted at **ICFO – The Institute of Photonic Sciences**  
Master in Multidisciplinary Research in Experimental Sciences (ICFO–UPF–BIST)

