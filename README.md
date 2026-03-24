# ISSR Project 01: Team Communication Audio Analysis (GSoC 2026)

This repository contains my technical submission for the ISSR Project 01 test. Having worked with this organization previously, I’ve designed this pipeline specifically to address the unique constraints of the **ISSR driving simulator environment**.

## Background & Inspiration
This solution is an evolution of my previous work with the ISSR organization. You can find the summary of my **GSoC 2025** implementation here:
[GSoC '25: Communication Analysis Tool for Human-AI Interaction Driving Simulator Experiments](https://eskayml.medium.com/gsoc-25-communication-analysis-tool-for-human-ai-interaction-driving-simulator-experiments-final-39c53d90672d)

Building on that foundation, this 2026 test focuses on more robust pre-processing specifically tuned for the **7-participant** high-density environment.

## The Core Challenge: 7-Participant Dynamics
Most standard meeting corpora focus on 3 or 4 people. However, based on my direct experience with the lab's footage, the ISSR driving simulator involves **7 participants** communicating in a high-density, high-noise environment. This creates a complex "cocktail party" effect and significant spectral overlap that retail-grade enhancement tools often struggle to resolve.
![footage sample](https://miro.medium.com/v2/resize:fit:1100/format:webp/1*_O_QMa1vY7a1bzqljRK1GA.png)
This test demonstrates my approach to cleaning and preparing this multi-channel data for high-accuracy transcription and diarization.

## Repository Layout
- `01_Data_Resource_Selection.ipynb`: Rationale for using the AMI Corpus as a 7-participant proxy.
- `02_Audio_Enhancement.ipynb`: A modular pipeline (Pre-emphasis, Spectral Gating, Normalization) designed for simulator noise.
- `requirements.txt`: Exact library versions for a stable environment.
- `input/` & `output/`: Sample management for the 3-5 minute test requirements.

## Why My Approach Works for ISSR
Instead of applying a generic "one-size-fits-all" filter, I've implemented a pipeline that prioritizes **speech formant clarity**. 

1.  **High-Density Scaling:** I chose the AMI Corpus because its circular microphone arrays are the closest structural match to how we capture 7-person interactions in the lab.
2.  **Noise-Floor Intelligence:** The spectral gating logic is tuned to the specific "engine hum" and mechanical vibrations characteristic of the TRIP LAB simulator runs.
3.  **Transcription-Ready Output:** The final stage focuses on normalization and pre-emphasis to ensure that downstream models like Whisper can "hear" through the overlapping dialogue of 7 speakers.

---
**Samuel Kalu**  
*GSoC 2026 Applicant & Former ISSR Contributor*
