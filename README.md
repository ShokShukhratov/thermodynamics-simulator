# Kinetic — Thermodynamic Particle Simulator

A real-time molecular dynamics simulation of the **Ideal Gas Law (PV=nRT)** 
built from scratch in Python with no external libraries. Individual gas particles 
bounce around a resizable container, and macroscopic properties like pressure, 
temperature, and volume emerge naturally from their collisions.

Built as a term project for 15-112 (Fundamentals of Programming) at Carnegie Mellon University.

---

## Demo

![Kinetic Simulator Demo](https://github.com/user-attachments/assets/ecc3c89e-9e1b-4142-b5df-a94f19d9b81c)

---

## Features

- **2D Elastic Collision Physics** — particles interact using real normal vector 
  decomposition and impulse-momentum equations, conserving kinetic energy and momentum
- **Ideal Gas Law Visualization** — live P, V, T, N readouts update in real time 
  and reflect accurate thermodynamic relationships as you interact
- **Speed Color Coding** — particles are colored blue (slow), white (medium), 
  or red (fast) based on their speed relative to the current distribution
- **Volume Slider** — drag to compress or expand the container and watch 
  pressure respond accordingly
- **Heat / Cool Controls** — add or remove kinetic energy from all particles 
  and observe temperature change instantly
- **Maxwell-Boltzmann Histogram** — live speed distribution graph that naturally 
  forms a right-skewed bell curve through emergent collision physics — no code 
  explicitly enforces the shape
- **Thermal Equilibrium Indicator** — green label appears when particle speeds 
  have statistically settled into a stable distribution
- **Collision Counter** — tracks total particle-particle collisions in real time

---

## How to Run

1. Make sure you have Python installed
2. Install CMU Graphics:
pip install cmu-graphics
3. Clone the repository:
git clone https://github.com/yourusername/kinetic-simulator.git
5. Run the file:
python gas_simulator.py

---

## Controls

| Key / Input | Action |
|---|---|
| Drag slider | Resize container (change volume) |
| HEAT + button | Increase particle kinetic energy |
| COOL - button | Decrease particle kinetic energy |
| A | Add 5 particles |
| D | Remove 5 particles |
| H | Heat the gas |
| C | Cool the gas |
| SPACE | Pause / resume |
| R | Reset simulation |
| G | Load showcase state (40 particles) |
| J | Compress to minimum volume |
| K | Heat dramatically |
| L | Cool dramatically |

---

## Physics Background

This simulation models the **Kinetic Molecular Theory** of gases. Each particle 
obeys Newtonian mechanics and collisions are resolved using:

- **Normal vector decomposition** — momentum is only exchanged along the line 
  connecting two particle centers
- **Impulse-momentum theorem** — `impulse = 2 * relativeSpeed / (m1 + m2)`
- **Pressure calculation** — accumulated wall impulse (Δp = 2mv) averaged over 
  fixed time intervals
- **Temperature** — derived from average kinetic energy: `KE = ½mv²`, 
  proportional to T by the equipartition theorem

Over time, the speed distribution naturally converges to the 
**Maxwell-Boltzmann distribution** — a hallmark result of statistical mechanics — 
purely as an emergent property of elastic collisions.

---

## Project Structure
```
gas_simulator.py
│
├── Section 1 — Model & Classes
│     ├── Particle class (position, velocity, collision, color)
│     └── Container class (walls, pressure calculation, resizing)
│
├── Section 2 — Physics Helper Functions
│     ├── distance()
│     ├── regulateElasticCollisions()
│     ├── computeTemperature()
│     ├── getSpeedColor()
│     ├── capParticleSpeed / floorParticleSpeed()
│     └── makeParticle()
│
├── Section 3 — Initialization
│     └── onAppStart()
│
├── Section 4 — Views
│     ├── drawSimulation()
│     ├── drawUIPanel()
│     ├── drawHistogram()
│     └── drawPauseOverlay()
│
└── Section 5 — Controllers
      ├── onStep / physicsStep()
      ├── onMousePress / Drag / Release()
      └── onKeyPress / Release()
```

## Built With

- **Python 3**
- **CMU Graphics** — Carnegie Mellon's beginner-friendly graphics library
- No external physics or math libraries — all collision and thermodynamic 
  logic implemented from scratch

---

## Author

**Shokhjakhon Shukhratov**  
Carnegie Mellon University — Intended Major: Computational Physics  
sshukhra@andrew.cmu.edu  
[LinkedIn](https://www.linkedin.com/in/shokhjakhon-shukhratov-b4b210288/)
