# 🚀 Rocket Launch Simulator

An interactive, browser-based simulator for a multi-stage rocket flying straight up. Design up to three stages, launch, and watch thrust, drag, gravity and changing mass play out live, with altitude and velocity plotted as it flies.

**▶ Live demo:** https://gitucha.github.io/rocket-sim/
**📘 Physics write-up:** [physics.html](https://gitucha.github.io/rocket-sim/physics.html)

---

## Features

- **Multi-stage rockets (1–3 stages):** set thrust, dry mass, fuel mass and Isp for each stage. Spent stages separate and fall away, and the next stage ignites after a 1.5 s coast.
- **Live design feedback:** TWR, burn time and ideal Δv for each stage (Tsiolkovsky), plus total Δv, update as you move the sliders.
- **Real physics, step by step:**
  - mass that falls as propellant burns (`ṁ = T / (Isp·g₀)`)
  - drag with an exponential atmosphere (`D = ½ρv²CdA`)
  - inverse-square gravity
  - Max Q tracking during ascent
  - escape-velocity detection
- **Live charts:** altitude and velocity against time, with staging events marked and your last four flights shown faded for comparison.
- **Flight log:** burnout, separation, ignition, apogee and impact events with time, altitude and speed.
- **Time warp:** 1×, 5×, 20× and 100×. Warp runs more physics steps per frame and never uses a bigger step, so accuracy doesn't change.
- **No dependencies:** one HTML file with plain JavaScript and Canvas. It works on phones.

## Default rocket

A two-stage sounding rocket with a 100 kg payload:

| | Stage 1 | Stage 2 |
|---|---|---|
| Thrust | 70 kN | 12 kN |
| Isp | 230 s | 250 s |
| Dry / fuel mass | 1000 / 2400 kg | 250 / 450 kg |
| TWR at ignition | 1.70 | 1.53 |
| Ideal Δv | 1.91 km/s | 2.03 km/s |

**Result:** an apogee of about 392 km, Max Q of about 39 kPa at T+50 s, and a flight time of about 13.7 min. A single-stage rocket with the same total mass and propellant only reaches about 150 km, which is why staging matters.

## The model in one equation

```
m(t)·a = T − ½·ρ(h)·v·|v|·Cd·A − m(t)·g₀·(R/(R+h))²
ρ(h)  = 1.225·e^(−h/8500)
ṁ     = T / (Isp·g₀)
```

It's integrated with semi-implicit Euler at `dt = 0.01 s`. A convergence check shows the apogee changes by about 0.02% when going down to `dt = 0.001 s`. The full derivation, worked example and loss analysis are in [physics.html](physics.html).

## Run it locally

No build step. Clone the repo and open the file:

```bash
git clone https://github.com/gitucha/rocket-sim.git
cd rocket-sim
open index.html        # macOS. On Windows: start index.html, on Linux: xdg-open index.html
```

## Project structure

```
rocket-sim/
├── index.html          # the simulator (UI, rendering and physics engine)
├── physics.html        # equations, worked example, assumptions
├── docs/
│   └── experiments.md  # guided experiments to try
└── README.md
```

The physics engine sits between the `ENGINE START` and `ENGINE END` markers in `index.html`. It's plain functions with no DOM access (`createSim`, `stepSim`, `analyse`), so it can be tested on its own in Node.

## Assumptions and limits

- Vertical flight only, with no gravity turn, so it can't reach orbit.
- Constant thrust, Isp and Cd, with no Mach effects and no difference between sea-level and vacuum Isp.
- Exponential atmosphere, no wind, no Earth rotation, no parachute.

## Roadmap

- [x] Single-stage vertical flight
- [x] Multi-stage rockets with separation
- [ ] 2D flight with a gravity turn, the path to orbit
- [ ] Mach-dependent drag coefficient
- [ ] Sea-level vs vacuum Isp
- [ ] Parachute recovery
- [ ] Export flight data to CSV

## Author

Built by **[@gitucha](https://github.com/gitucha)**, an aerospace engineering student 🇰🇪.
