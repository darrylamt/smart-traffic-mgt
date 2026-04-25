# Smart Traffic Management System — Live Simulation

**GIMPA · Data Communications & Networking · Group 7 · 2026**

A browser-based simulation of the Smart Traffic Management System proposed in our final project report. Demonstrates real-time adaptive signal control using IoT sensor data and cloud processing.

## How to run

Open `index.html` in any modern browser. No server or build step needed.

## What it shows

**4-intersection grid** (Tetteh Quarshie · Ako-Adjei · Circle · Kanda) — the same configuration used in our SUMO simulation model.

| Feature | Description |
|---|---|
| Smart mode | Dynamic green time: `Gi = min(60, 20 + Qi / 0.5 × 1.5)` |
| Fixed mode | Standard 30-second fixed timing |
| Emergency vehicle | RFID/GPS preemption → green within 5 seconds |
| Vehicle queues | Color-coded by density (blue → orange → red) |
| Stats comparison | Wait time, throughput, queue length vs baseline |

## Controls

- **SMART / FIXED** — toggle between adaptive and fixed-timing modes
- **Speed** — 1×, 3×, or 10× simulation speed
- **Dispatch Emergency Vehicle** — triggers RFID preemption at a random intersection

## Key results (from SUMO simulation in report)

| Metric | Fixed | Smart | Improvement |
|---|---|---|---|
| Avg wait time | 85s | 52s | **39%** |
| Queue length | 18 veh | 11 veh | **39%** |
| Throughput | 950 veh/hr | 1250 veh/hr | **+32%** |
| Emergency delay | 45s | 12s | **73%** |

## Architecture simulated

```
IoT Sensors (IR + Magnetic Loop + Camera)
        ↓
Edge Gateway · Raspberry Pi 4 (longest-queue-first algorithm)
        ↓  4G/LTE
Cloud · AWS IoT Core → Lambda → DynamoDB
        ↓
Monitoring Dashboard (this simulation)
        ↓
Traffic Signal Controller
```

## Team

Richard Kwaku Mensah · Gloria Akosua Apedo · Derek Kofi Agbeh  
Cornelius Selorm Akafo · George Okuampah Aning · Darryl Amoatey · Nancy Mensah
