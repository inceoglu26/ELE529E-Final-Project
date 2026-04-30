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

---

## 4. Quality Utility Tree  

Functional Correctness  
- Velocity accuracy  
- Real-time response (<10 ms)  
- UI responsiveness  

Robustness  
- Noise handling  
- Stable triggering  

Performance  
- Low latency (<5 ms)  
- Efficient scheduling  

Maintainability  
- Modular code  
- Documentation  

---

## 5. System Architecture  

Hardware  
- STM32F410RB  
- Piezo Pads  
- ILI9341 Display  

Software  
- FreeRTOS (planned)  
- ADC Driver  
- UART Communication  
- MIDI Output  

---

## 6. Activity Flow  

Initialize system  
→ Read piezo  
→ Detect peak  
→ Convert to velocity  
→ Send via UART  
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
| UI lag | Switch to LTDC |
| RTOS issues | Priority scheduling |
| MIDI latency | Optimize pipeline |

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

A loop-based **step sequencer** will be implemented (similar to MPC workflow).

### Concept  

- 16-step loop (1 bar)  
- Each step can trigger pads  
- Loop continuously plays  

### Data Structure  

```
uint8_t sequence[12][16];
```

Each value:  
0 = off  
1 = trigger  

---

### Timing  

Step duration:  

```
Step = (60 / BPM) / 4
```

Example:  
120 BPM → 125 ms  

---

### Playback Logic  

For each step:  

- Check all pads  
- Trigger active ones  

---

### Required Buttons (Total: 5)

- MODE (Live / Sequencer)  
- REC  
- PLAY / STOP  
- TEMPO+  
- TEMPO-  

---

### Real-Time Constraints  

- Timing jitter < 2 ms  
- Latency < 5 ms  

---

### Future Extensions  

- Velocity per step  
- Swing timing  
- Pattern chaining  
- LCD grid UI  

---

## 11. Remaining Timeline  

Week 1  
- FreeRTOS integration  

Week 2  
- UI optimization  

Week 3  
- MIDI + DAW connection  

Week 4  
- Latency tuning + demo  

---

## Appendices  

Hardware Progress  
- Acrylic pads fabricated  
- EVA foam applied  
- Piezo modules integrated  

GitHub  
[Repo Link]

Videos  
[Velocity Video]  
[Display Video]