# Ball-Balancing-Project-For-Educators
This is the repository of the Ball Balancing Project for Educators. Contained is a manual.pdf detailing:

## Electronics Knowledge ##
- Closed circuit topology & power routing (5V → VCC, GND → ground)
- Breadboard internal connection patterns & wiring best practices
- Digital input conditioning with external 10 kΩ pull-down resistors
- Power distribution strategies (Arduino USB vs. dedicated 4xAA battery pack)

## Feedback Control Systems ##
- PD controller fundamentals: Proportional (`Kp`) and Derivative (`Kd`) terms
- System degrees of freedom: ball position `x` and beam angle `θ`
- Calibration workflow: coarse angle → fine alignment → center distance reference
- Why P/PD is preferred over PID for this educational scope (technical debt & complexity trade-offs)

## Hardware Setup & Validation ##
- Generating wiring schematics via Circuitro.io
- Downloading & using boilerplate firmware for individual component testing
- Arduino IDE configuration, board/port selection, and sketch verification/upload workflow
- Serial Monitor interaction for real-time diagnostics

## AI-Assisted Firmware Development ##
- Spec-Driven Development (SDD) vs. Vibe Coding: why precision matters in control systems
- Structuring effective specifications (user story, constraints, success criteria)
- Deploying specs through agentic coding platforms (Google Antigravity, Cursor, Claude Code, etc.)
- The `Generate → Test → Iterate` feedback loop for firmware refinement

## Troubleshooting & System Tuning ##
- Diagnosing control loops by isolating variables (`x` vs. `θ`)
- Calibration failure vs. code error identification
- Damping behavior: underdamped (oscillatory), overdamped (sluggish), critically damped (target)
- Recommended starting gains: `Kp ≈ 1.0`, `Kd ≈ 0.3`

---

## 📦 Repository Contents
| Path | Description |
|------|-------------|
| `manual.pdf` | Complete educator guide & technical reference (v1.3) |
| `firmware/` | Circuitro.io boilerplate package for component validation |
| `specs/` | Example SDD prompts & specification templates |
| `docs/` | Supplementary diagrams, wiring references, and tuning guides |

## ⚙️ Hardware Requirements
- Arduino Uno R3
- HC-SR04 Ultrasonic Sensor
- Standard Micro Servo Motor
- 2× Mini Pushbutton Switches (with color-coded caps)
- 2× 10 kΩ Resistors (pull-down)
- 4xAA Battery Holder + Power Supply
- Full-size Breadboard & Jumper Wires

## 💻 Software Requirements
- Arduino IDE v1.x or v2.x
- Circuitro.io account (for schematic generation & boilerplate download)
- AI Agentic Coding Platform (e.g., Google Antigravity, Cursor, Claude Code, OpenClaw, etc.)
- Serial Monitor terminal (built into Arduino IDE)

## 🛠️ Quick Start Workflow
1. **Build & Validate**: Follow Circuitro.io wiring diagram → upload boilerplate → verify each component via Serial Monitor.
2. **Write Specification**: Define problem scope, map hardware to control roles, outline user story, list constraints, and set success criteria.
3. **Generate Firmware**: Paste specification into your chosen AI coding agent → review generated code → flash to Arduino.
4. **Calibrate & Tune**: Run calibration sequence → adjust `Kp`/`Kd` via physical buttons → monitor response → save config to EEPROM.
5. **Iterate**: Observe behavior, identify gaps, refine specification, and regenerate until system meets critical damping targets.

## 🔍 Tuning Reference Matrix
| Symptom | Likely Cause | Adjustment |
|---------|--------------|------------|
| Ball stuck on sensor side | Code error / calibration failure | Verify ultrasonic zero-reference; check pin assignments |
| Ball stuck on flat side | Calibration misalignment | Re-run coarse/fine angle alignment with ball centered |
| Continuous wobbling | Underdamped loop | ↓ `Kp` or ↑ `Kd` in small increments |
| Slow/sluggish response | Overdamped loop | ↑ `Kp` or ↓ `Kd` slightly |
| Configuration lost after power cycle | EEPROM write failure | Verify save step; check non-volatile memory logic |

## 📜 License & Attribution
This project is designed for technical education and classroom deployment. The `manual.pdf` and associated materials are provided under an educational use license. Adaptations, translations, or commercial redistribution require explicit permission from the kit publisher.

> 💡 **Educator Pro Tip**: Encourage students to treat specification gaps as learning opportunities, not failures. The `Generate → Test → Iterate` cycle mirrors real-world embedded systems engineering and builds critical debugging intuition.

For questions, troubleshooting support, or curriculum integration guidance, refer to Section 8 (`Troubleshooting`) and Section 9 (`Appendix: Further Details`) in the included manual.
