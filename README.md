# ELE529E Embedded Systems Project Progress Report  

**Course:** ELE529E Embedded Systems  
**Submission Date:** 30/04/2026  

---

## 1. Project Overview  
| Project Title | STM32-Based Drum Machine with Velocity-Sensitive Pads |  
|---------------|---------------------|  
| Team Members | Emre Inceoglu |  
| Project Start Date | 30/03/2026 |  
| Expected Completion | 30/05/2026 |  

---

## 2. Project Milestones & Delivery Plan  
| Milestone | Tasks | Deadline | Status |  
|----------|------|----------|--------|  
| Requirement Analysis | Define system scope and constraints | 05/04/2026 | ✓ |  
| System Design | Hardware + software architecture | 15/04/2026 | ✓ |  
| Prototype Development | Pad + ADC + velocity detection | 30/04/2026 | ✓ |  
| Testing & Debugging | Latency + accuracy validation | 20/05/2026 | ✗ |  
| Final Demo | DAW + UI + final report | 30/05/2026 | ✗ |  

---

## 3. Individual Contribution Plan  

### Emre Inceoglu  
| Task | Responsibility | Time |  
|------|--------------|------|  
| Hardware Design | Pad construction, piezo mounting | 2 weeks |  
| STM32 Setup | ADC + UART configuration | 1.5 weeks |  
| Embedded Logic | Velocity detection algorithm | 1 week |  
| UI Development | LCD interface (ILI9341 / LTDC) | 2 weeks |  
| RTOS | Task scheduling | 2 weeks |  
| MIDI Integration | DAW connection | 1 week |  
| Step Sequencer Design | Loop engine, timing system, step buffer implementation | 1.5 weeks |  
| Sequencer Integration | Pad input + recording + playback logic | 1 week |  

---

## 4. Quality Utility Tree  

Functional Correctness  
- Velocity accuracy  
  - Metric: ADC peak-to-velocity mapping linearity (R² > 0.9)  
  - Metric: Repeatability (std deviation < 5% for identical hits)  
- Real-time response (pad hit → trigger detection)  
  - Metric: Detection latency < 10 ms (measured via GPIO toggle + logic analyzer)  
- UI responsiveness  
  - Metric: Frame update latency < 50 ms  

Robustness  
- Noise handling  
  - Metric: False trigger rate < 1 per 100 hits  
- Stable triggering  
  - Metric: Double-trigger rate < 2%  

Performance  
- Audio latency (pad hit → MIDI/trigger output)  
  - Metric: End-to-end latency < 5 ms  
- Sequencer timing accuracy  
  - Metric: Step jitter < 2 ms  

Maintainability  
- Modular code  
  - Metric: Separate driver layers (ADC, UI, MIDI)  
- Documentation  
  - Metric: Code comments + GitHub documentation  

---

## 5. System Architecture  

Hardware  
- STM32H723ZG (LTDC-capable MCU for high-performance UI)  
- Piezo Pads  
- ILI9341 (prototype) → LTDC display (final system)  

Software  
- FreeRTOS  
- ADC Driver (pad input)  
- Sequencer Engine  
- UART / MIDI Communication  
- UI Task  

---

## 6. Activity Flow  

Initialize system  
→ Read piezo input  
→ Detect peak (velocity)  
→ Trigger output / record step  
→ Update UI  
→ Send MIDI (future)  
→ Repeat  

---

## 7. Current Progress  

- 3mm acrylic plates cut into 5x5 cm pads  
- EVA foam layers applied to piezo sensors  
- Piezo modules with jumper outputs integrated  
- Velocity detection tested via Hercules terminal  
- Velocity output observed to scale with hit intensity  
- ILI9341 display tested with STM32F410RB  
- SPI-based display shows noticeable refresh delay  
- STM32H723ZG selected for LTDC-based UI improvement  

---

## Demo Videos  

Velocity Test:  
[Video Link Here]

Display Test:  
[Video Link Here]

---

## 8. Risks  

| Risk | Mitigation |
|------|-----------|
| Noise | Filtering + threshold tuning |
| UI lag | LTDC hardware acceleration |
| RTOS issues | Priority scheduling |
| MIDI latency | Interrupt-driven pipeline |

---

## 9. Conclusion  

Initial prototype is successfully completed:  

- Working velocity-sensitive drum pad  
- Reliable ADC-based detection  
- Real-time UART output  
- Basic display integration  

Velocity detection behaves correctly with respect to hit strength.

---

## 10. Step Sequencer (Planned Feature)  

A loop-based **step sequencer** will be implemented (inspired by MPC-style workflow).

### Concept  

- 16-step loop (1 bar)  
- Each step can trigger pads  
- Loop continuously plays  

---

### Data Structure  

```
uint8_t sequence[12][16];
```

Each value:  
0 = off  
1 = trigger  

---

### Timing  

```
Step = (60 / BPM) / 4
```

Example:  
120 BPM → 125 ms  

---

### Playback Logic  

For each step:  

- Iterate all pads  
- Trigger active steps  
- Maintain strict timing using RTOS  

---

### Required Buttons (Total: 5)

- MODE (Live / Sequencer)  
- REC (record input)  
- PLAY / STOP  
- TEMPO+  
- TEMPO-  

---

### Real-Time Constraints  

- Sequencer timing jitter < 2 ms (ensures rhythmic accuracy)  
- Audio latency (pad → output) < 5 ms (ensures playability)  
- UI update latency < 50 ms (ensures usability)  

---

### Future Extensions  

- Velocity per step  
- Swing timing  
- Pattern chaining  
- LCD grid UI  

---

## 11. Remaining Timeline  

Week 1  
- FreeRTOS integration + task separation  

Week 2  
- UI optimization (LTDC transition)  

Week 3  
- MIDI + DAW integration  

Week 4  
- Latency optimization + final demo  

---

## Appendices  

Hardware Progress  
- Acrylic pads fabricated  
- EVA foam applied  
- Piezo modules integrated  

GitHub  
https://github.com/inceoglu26/ELE529E-Final-Project  

Videos  

Velocity Test:  
[Drum Pad Video](./drum-pad.mp4)

Display Test:  
[LCD Display Video](./lcd-display.mp4)