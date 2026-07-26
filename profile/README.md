# Thyraen Robotics

**Mission-centric autonomy for contested and degraded environments.**

Thyraen Robotics builds autonomous systems that turn commander's intent into coordinated
operational effects — across heterogeneous platforms and sensors, in environments where
communications are unreliable, spectrum is contested, and conditions change faster than
pre-planned workflows can keep up.

We treat autonomy as a *capability*, not a single vehicle or algorithm: onboard mission
reasoning, mission command and control, resilient communications, sensor exploitation, and
the simulation, data, and knowledge infrastructure required to field all of it credibly.
Our systems keep the warfighter heads-up and in the fight — compressing
decision-to-effect timelines without adding cognitive burden.

**Website:** [thyraen-robotics.github.io](https://thyraen-robotics.github.io/) ·
**Contact:** [contact@thyraen.ai](mailto:contact@thyraen.ai)

---

## The Product Ecosystem

| Product | What it is |
|---|---|
| **[Vanguard](https://thyraen-robotics.github.io/products/vanguard/)** | Onboard autonomy and mission-computer runtime for unmanned systems |
| **[Echelon](https://thyraen-robotics.github.io/products/echelon/)** | Situational awareness and tasking control plane for heterogeneous platforms |
| **[Tacit](https://thyraen-robotics.github.io/products/tacit/)** | Low-probability-of-detection datalink for contested spectrum |
| **[Dissident](https://thyraen-robotics.github.io/products/dissident/)** | Vendor-free drone video reception and redistribution to the tactical map |
| **[Simulator](https://thyraen-robotics.github.io/products/simulator/)** | Photoreal simulation and testbed environment for autonomy development |
| **[Crucible](https://thyraen-robotics.github.io/products/crucible/)** | Provenance-tracked data refinery for training-ready datasets and deployable models |
| **[Augur](https://thyraen-robotics.github.io/products/augur/)** | Doctrine knowledge graph and cited analysis thought-partner |
| **[Devstack](https://thyraen-robotics.github.io/products/devstack/)** | Shared engineering platform powering every Thyraen repository |

---

## Operate

### Vanguard — Onboard Autonomy Runtime

*An Agent when it must be. An Asset when it should be.*

**Vanguard** is the vehicle-side runtime that turns mission intent into bounded local
action on an unmanned platform: local mission reasoning, autopilot and payload command,
RF and visual sensing, and operator visibility — with a clean path from simulation to
field deployment on NVIDIA Jetson mission computers.

- Runs in two postures from one codebase: **Agent** (owns local mission reasoning onboard)
  or **Asset** (executes intent from an external mission system such as Anduril Lattice)
- Retains local **Platform Authority** in both postures — a safety and execution boundary
  no mission logic, external or onboard, can bypass
- Doctrinal F2T2EA mission spine with per-phase capability contracts
- PX4 flight integration, payload/gimbal control, GPU visual perception, RF collection,
  and onboard media presentation
- Honest, evidence-backed task reporting — admission, progress, completion, and failure
  are typed outcomes, never inferred

### Echelon — Mission C2 & Situational Awareness

**Echelon** is a contract-driven situational awareness and tasking control plane for
heterogeneous robotic and autonomy platforms, aligned with the U.S. Army's Next Generation
C2 (NGC2) architecture.

- Canonical **Entity/Task** domain model with strict, reject-only contract enforcement
- Adapter integration boundary: Vanguard vehicles over Zenoh, TAK streaming CoT,
  ADS-B, and AIS feeds
- Operator portal: React/Cesium 3D map workspace with military symbology and
  capability-gated tasking
- Deterministic media data plane fanning H.264 video out to browsers over WebRTC
- Deploys centralized, onboard, or fully distributed across peer nodes

---

## Connect

### Tacit — Quiet Datalink

**Tacit** is a low-rate, high-reliability, low-probability-of-detection datalink — the
vehicle-to-vehicle control plane for Vanguard, built for command-and-control, telemetry,
and mission-state sync in contested spectrum with no supporting infrastructure.

- Designed around the axiom that *the link is the first casualty*: hard to notice,
  hard to localize, hard to jam
- AES-CCM authenticated encryption, reliable delivery with bounded retry, and
  replay-resistant epoch handling
- Adaptive link architecture driving power, modulation, and channel selection toward the
  minimum RF footprint the moment allows
- 100% Rust, end to end — `no_std`, no-heap firmware with the same protocol core proven
  in simulation and on hardware

### Dissident — Open Video Reception

**Dissident** is an open, cross-platform receiver stack that captures encoded live drone
video without any vendor application, SDK, or firmware modification, and republishes it
to the tools operators already use.

- Vendor-free acquisition of the DJI Goggles 3 live-view stream over BLE + Wi-Fi or USB
- Hardware-validated H.264 extraction, local decode, and display on Android and Linux
- Republication as RTSP/RTP plus Cursor-on-Target video announcements for ATAK and TAKX,
  delivered as self-contained plugins
- Portable sans-I/O Rust protocol core with Android, Raspberry Pi, and Jetson targets

---

## Build

### Simulator — Fly It a Thousand Times First

**Simulator** is the shared simulation and testbed environment behind the Thyraen autonomy
stack — where thousands of controlled, repeatable flights happen before hardware is ever
on a launch rail.

- Headless PX4/JSBSim backend as the single authoritative source of flight truth
- Unreal Engine 5 + Cesium photoreal rendering as a strict visual/sensor follower,
  feeding co-boresighted EO and simulated-IR imagery into Vanguard perception
- Exact-frame, capture-correlated ground-truth annotation for perception development
- Composable, reviewable scenario registries: maps, vehicles, launchers, payloads,
  and autopilot profiles as versioned manifests
- Gated, artifact-producing validation with ULog-derived flight reports

### Crucible — Data & Model Refinery

**Crucible** is the data foundry: a provenance-tracked repository and toolchain that turns
raw source material into training-ready datasets and deployable model capability.

- Immutable sources, curated references, interpretations, and datasets in separate
  layers bound by stable IDs
- Framework-neutral dataset tooling: validation, checksummed assets, COCO/VOC
  interchange, and cross-dataset training mixtures
- Training, offline retrieval, and labeling forges launched from one selector
- Perception track carrying data through fine-tuning to hardware-specific TensorRT
  engines consumed by Vanguard

### Augur — Doctrine Knowledge Substrate

*Decompose the doctrine we have. Author the doctrine autonomous warfare needs.*

**Augur** turns paragraph-numbered military doctrine into a version-aware, provenance-stamped
knowledge graph, and puts a cited thought-partner on top of it.

- Every claim carries the literal source span it came from — zero fabrication is a build
  property, not a prompt instruction
- Answers resolve to publication, paragraph, and version, or return an explicit
  "not found in current doctrine"
- Doctrine modernization as graph authoring: derived doctrine stays permanently
  distinguishable from source doctrine, with provable lineage
- Airgap-capable by design — a single provider seam swaps hosted models for on-prem inference

### Devstack — Shared Engineering Platform

**Devstack** is the internal developer platform every Thyraen repository builds on:
one supervisor, one dashboard, one dependency policy across the fleet.

- Process-stack supervision with a live terminal dashboard for humans and a structured
  JSON event surface for coding agents
- Bootstrap, readiness, and dependency-currency gates shared by every repo —
  `cargo xtask bootstrap | doctor | run | deps` behaves identically everywhere
- Fleet-wide dependency management: one reviewable snapshot pinning toolchain, crate
  versions, and internal exports across all repositories

---

## How It Fits Together

- **Vanguard** executes missions onboard the platform; **Echelon** provides the
  operational picture and tasking layer above it
- **Tacit** keeps platforms talking when the spectrum turns hostile; **Dissident**
  brings live video from commodity hardware onto the tactical map
- **Simulator** proves behavior before flight; **Crucible** turns collected data into
  deployed perception; **Augur** grounds autonomy in doctrine
- **Devstack** binds the fleet together with shared tooling, contracts, and
  dependency policy

Integration happens through strict, versioned contracts and adapters rather than bespoke
coupling — platform specifics stay isolated from mission-level autonomy.

---

## Design Philosophy

- **Mission over platform** — autonomy exists to serve operational outcomes
- **Contracts over coupling** — typed, versioned boundaries; reject-only validation;
  integration without fragility
- **Human intent first** — operators define goals and limits; autonomy optimizes execution
- **Resilience by default** — degraded comms, contested spectrum, and denied environments
  are the design center, not the exception
- **Honest capability claims** — implemented substrate is kept explicitly distinct from
  ratified targets, in code and in documentation

---

## Working With Thyraen

Thyraen Robotics builds for the Department of War and allied defense organizations that
need autonomy transitioned from experimentation to operational reality:

- **Architecture alignment** — Echelon's domain model aligns with the Army's Next
  Generation C2 (NGC2) architecture; our systems interoperate with TAK and are designed
  to integrate with external mission systems such as Anduril Lattice
- **Interoperability first** — standards-based interfaces throughout: Cursor-on-Target,
  ADS-B, AIS, MAVLink/PX4, RTSP/H.264, and WebRTC
- **Closed-network ready** — airgap-capable deployments with native binaries and
  on-premises inference; no cloud dependency on the target
- **Simulation-validated** — capabilities are proven across thousands of repeatable
  simulated flights, with gated validation evidence, before they touch hardware

**Headquarters:** Sierra Vista, Arizona ·
**Contact:** [contact@thyraen.ai](mailto:contact@thyraen.ai)

---

<p align="center"><sub>Thyraen Robotics · From Objectives to Effects</sub></p>
