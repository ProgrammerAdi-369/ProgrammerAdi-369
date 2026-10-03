<div align="center">
  <picture>
    <source media="(prefers-color-scheme: dark)" srcset="assets/hero-dark.svg">
    <img alt="Aditya. Systems where timing, data and correctness all matter." src="assets/hero-light.svg" width="100%">
  </picture>
</div>

<br>

## I like problems where speed, data and correctness all have to hold at the same time.

| `BOOKING` | `MATCHING` | `MODELS` | `MAPPING` |
| :-- | :-- | :-- | :-- |
| A booking system that can never double-book a room. | A matching engine that has to be fast. | A model that has to be honest about its edge. | A map that has to be right about what is in front of a vehicle. |

Most of what's below is built in the open and documented properly. Each project has a technical write-up in its repo.

<br>

## Selected work

### [Vyas Room Booking ↗](https://github.com/I-R-I-S-MIT-WPU/Vyas-Faculty-Availability) &nbsp; ![Flagship](https://img.shields.io/badge/FLAGSHIP-9a6700?style=flat-square)

![React](https://img.shields.io/badge/React-30363d?style=flat-square) ![TypeScript](https://img.shields.io/badge/TypeScript-30363d?style=flat-square) ![Express 5](https://img.shields.io/badge/Express%205-30363d?style=flat-square) ![PostgreSQL](https://img.shields.io/badge/PostgreSQL-30363d?style=flat-square) ![Redis](https://img.shields.io/badge/Redis-30363d?style=flat-square) ![Socket.IO](https://img.shields.io/badge/Socket.IO-30363d?style=flat-square)

A full-stack room booking platform built for MIT World Peace University. Faculty browse the building floor by floor, see a live weekly calendar for any room, find a free room for a given time slot and book it in a few clicks. Everyone else's calendar updates in real time while they do. Administrators manage the rooms, approve bookings for restricted spaces and maintain the semester timetable.

It started on Supabase and was moved to a custom Express and PostgreSQL backend, with the migration documented. The backend lives in its own repository.

| **51+** | **40+** | **1 PRD** |
| :-: | :-: | :-: |
| implemented features | API endpoints | product requirements, written up |

<div align="center">
  <img src="assets/brag.jpg" alt="Vyas Room Booking: weekly room calendar on desktop and phone" width="100%">
</div>

<br>

### [Low-Latency Order Matching Engine ↗](https://github.com/ProgrammerAdi-369/Low-Latency-Order-Matching-Engine)

![C++17](https://img.shields.io/badge/C%2B%2B17-30363d?style=flat-square) ![CMake](https://img.shields.io/badge/CMake-30363d?style=flat-square)

An NSE/BSE-style matching engine with price-time priority (FIFO). It handles limit and market orders, partial fills, multi-level cascading matches and O(1) lazy cancellation. It ships with ten scenario tests that cover the edge cases, plus a latency and throughput analyzer.

<div align="center">

| **~5.2M** | **~0.19 µs** | **~0.8 µs** |
| :-: | :-: | :-: |
| orders / sec | average latency | P99 latency |

<sub>10,000-order stress test</sub>

</div>

<br>

### [Option Mispricing Pipeline ↗](https://github.com/ProgrammerAdi-369/Machine-Learning-Framework-for-option-mispricing)

![Python](https://img.shields.io/badge/Python-30363d?style=flat-square) ![XGBoost](https://img.shields.io/badge/XGBoost-30363d?style=flat-square) ![SciPy](https://img.shields.io/badge/SciPy-30363d?style=flat-square) ![Streamlit](https://img.shields.io/badge/Streamlit-30363d?style=flat-square)

Detects mispriced BANKNIFTY options from raw NSE option-chain data. Signals come from cross-sectional z-scores of how far each contract sits from a model's fair value. A walk-forward retraining layer keeps the model current as the market changes, and a seven-layer accuracy analysis checks the result.

```mermaid
flowchart LR
    A[NSE option chain] --> B["Clean + implied vol<br/>(brentq)"]
    B --> C[Volatility and<br/>liquidity features]
    C --> D[XGBoost<br/>fair value]
    D --> E[Cross-sectional<br/>z-score]
    E --> F[BUY / SELL<br/>signals]
    F --> G[Streamlit review]
    F -. walk-forward retrain .-> D
```

<br>

### [MAQOIDS ↗](https://github.com/ProgrammerAdi-369/REPLACE-WITH-MAQOIDS-REPO-NAME) &nbsp; ![In progress](https://img.shields.io/badge/IN%20PROGRESS-9a6700?style=flat-square)

![Python](https://img.shields.io/badge/Python-30363d?style=flat-square)

**Multi-Agent Quantitative Options Intelligence & Decision System.** It combines separate agents for option mispricing and volatility forecasting with a shared data layer, and is growing market-regime and risk agents. The interesting part is composition. One agent gives a coarse, index-level view of volatility, another gives a fine, per-contract one, and the system has to reconcile them.

<br>

### [AVRLM ↗](https://github.com/ProgrammerAdi-369/REPLACE-WITH-LIDAR-REPO-NAME)

![Python](https://img.shields.io/badge/Python-30363d?style=flat-square) ![Spiking Neural Networks](https://img.shields.io/badge/Spiking%20Neural%20Networks-30363d?style=flat-square) ![Streamlit](https://img.shields.io/badge/Streamlit-30363d?style=flat-square) ![PyQt6](https://img.shields.io/badge/PyQt6-30363d?style=flat-square)

**Adaptive Variable-Resolution LiDAR Mapping.** Real-time terrain mapping for an unmanned ground vehicle. A spiking PointNet++ labels LiDAR points as drivable, static obstacle or dynamic object. An event-driven grid then spends resolution where it matters, with fine cells close to the vehicle and coarse cells far away, and only updates cells that actually received spikes. The repo includes two dashboards, a radar-style operator view and an energy profiler.

<br>

## Field notes

| **01 · Verify the code, not the changelog.** | **02 · Defaults are decisions.** | **03 · Treat a great number as a bug report.** |
| :-- | :-- | :-- |
| An audit of one of my own projects showed that a round of fixes I had recorded as done was not in the code. I now check with a grep and a test before I believe a status line. | A tie-break that quietly resolves to "drivable terrain" over "dynamic object" is a safety policy, not a detail. I write those choices down. | A surprisingly good compression ratio gets reconciled against an independent run before it goes in a write-up. |

<br>

<details>
<summary><b>Stack</b></summary>

<br>

|                      |                                                                            |
| -------------------- | -------------------------------------------------------------------------- |
| **Languages**        | C++17, Python, TypeScript                                                  |
| **Frontend**         | React, Vite, Tailwind, shadcn/ui, TanStack Query, Streamlit, Plotly, PyQt6 |
| **Backend and data** | Express, PostgreSQL, Redis, BullMQ, Socket.IO, pandas, NumPy, SciPy        |
| **ML**               | scikit-learn, XGBoost, spiking neural networks                             |
| **Tooling**          | CMake, Git, Claude Code                                                    |

</details>

<!--
Add a contact line here when ready, for example:
Reach me: your-email@example.com · LinkedIn: https://www.linkedin.com/in/your-handle
-->
