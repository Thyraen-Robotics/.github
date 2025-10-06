# Thyraen Robotics

> Mission-ready autonomy systems that stay reliable in contested and degraded environments.

We design, harden, and deploy modular autonomy stacks that pair ruggedized compute with resilient networking. Our teams blend embedded Linux, mesh communications, and operator tooling so mission crews can trust their robots in denied or high-tempo environments.

---

## Platform Pillars
- **Reproducible base images** powered by NixOS for deterministic upgrades across fleets.
- **Long-range mesh communications** tuned for low bandwidth and dynamic teams.
- **Operator-first interfaces** that surface telemetry, mission plans, and failsafes in one view.
- **Hardware pragmatism** spanning Raspberry Pi 5 + Navio2 through Jetson-class edge compute.

## Echelon Platform
| Layer | Repository | Focus | Status |
| --- | --- | --- | --- |
| Mission hub | [`Thyraen-Robotics/echelon`](https://github.com/Thyraen-Robotics/echelon) | Coordinates subsystem releases, integration docs, and fleet build orchestration. | Active |
| Mission system | [`Thyraen-Robotics/echelon-mission-system`](https://github.com/Thyraen-Robotics/echelon-mission-system) | Nix flake that emits mission-ready images for Raspberry Pi 5 (Navio2 today, Jetson next). | Active development |
| Mesh radio firmware | [`Thyraen-Robotics/echelon-radio-firmware`](https://github.com/Thyraen-Robotics/echelon-radio-firmware) | Tooling + build pipeline for long-range mesh stacks feeding the mission bus. | Active |
| HSI (operator UX) | [`Thyraen-Robotics/echelon-hsi`](https://github.com/Thyraen-Robotics/echelon-hsi) | Backend services and operator UI for situational awareness and command. | Active |

### R&D Tracks
- Navio2 Pi5 bring-up sandbox exploring PREEMPT_RT kernels and pi-gen stages for modern autopilots.
- Legacy Echelon mission-system experiments retained for regression analysis and migration notes.

## Current Focus
- Ship **Echelon Mission System v0.1.0** with Raspberry Pi 5 + Navio2 images and automated flashing flows.
- Finalise **mesh radio firmware migration** into the unified build + release tooling.
- Stand up **operator dashboards** that bridge ROS 2 telemetry into mission-ready UX.

## How We Work
- Version every subsystem through the `echelon` hub and pin releases with reproducible manifests.
- Treat build and flash tooling as first-class code; every repo ships scripts + docs for the full loop.
- Ground innovations in field feedback by pairing lab validation with multi-node range exercises.

## Get Involved
1. Start in [`echelon/docs/integration/full-stack.md`](https://github.com/Thyraen-Robotics/echelon/tree/main/docs/integration/full-stack.md) for local-to-field workflows.
2. Use [`AGENTS.md`](https://github.com/Thyraen-Robotics/echelon-mission-system/blob/main/AGENTS.md) to align on coding conventions and review expectations.
3. Open an issue in the [`echelon`](https://github.com/Thyraen-Robotics/echelon/issues) hub with proposals, integration feedback, or pilot requests.

## Staying In Touch
- Follow release manifests in `Echelon/manifests/` for subsystem compatibility maps.
- Watch `make` + `nix` targets in each repo for day-one build parity.
- Need a private conversation? Open a draft issue in the `Echelon` hub and flag it for the core team so we can coordinate an offline briefing.

<p align="center"><sub>Thyraen Robotics · Autonomy that respects the mission.</sub></p>
