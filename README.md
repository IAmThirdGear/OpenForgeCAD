# OpenForgeCAD

**Status: Planning / research. Active development is intentionally on hold.**

OpenForgeCAD is a proposed Linux-first, open-source parametric CAD application inspired by the workflows people value in professional mechanical CAD tools. The goal is to combine dependable engineering geometry, a responsive GPU-aware viewport, an extensible plugin system, and optional local generative AI.

> This project is independent and is not affiliated with or endorsed by Autodesk. “Fusion 360” is referenced only to describe the class of workflows that inspired the project.

## Project principles

- **Linux-first:** treat Linux as a primary platform, not an afterthought.
- **GPU-aware by design:** prioritize responsive graphics and benchmark compute acceleration where it is technically beneficial.
- **AI is optional:** the core CAD application must remain useful when AI plugins are disabled or absent.
- **Open and portable:** favor documented interfaces and interoperable formats such as STEP, STL, and 3MF where appropriate.
- **Build on proven foundations:** evaluate established geometry kernels before considering custom replacements.
- **Deterministic engineering:** AI may propose operations, but the CAD engine must validate geometry and constraints.
- **Security-conscious extensions:** treat third-party plugins as untrusted until reviewed and granted permissions.
- **Measured progress:** milestones should have tests and clear acceptance criteria.

## Proposed technology directions

These are hypotheses to validate, not final decisions:

- **Geometry kernel:** evaluate Open CASCADE Technology and alternatives.
- **Viewport:** evaluate Vulkan and suitable UI/rendering frameworks.
- **Desktop UI:** evaluate Qt.
- **Scripting and automation:** Python is a strong candidate for the first plugin interface.
- **Systems components:** consider C++ for direct integration with C++ geometry libraries; evaluate Rust for isolated components where it provides clear benefits.
- **GPU compute:** benchmark Vulkan compute and appropriate AMD-supported compute options for specific workloads.
- **Local AI:** design provider adapters for local inference runtimes; avoid hard-coding the application to one model vendor.

## Initial milestones

1. Feasibility research and technology decision records.
2. Minimal native viewport and geometry-kernel proof of concept.
3. Basic solid creation, selection, and STEP/STL export.
4. Parametric feature history and sketch constraints.
5. Stable plugin API and example plugin.
6. Optional local-AI plugin using validated CAD commands.
7. Community contribution and extension-distribution workflow.

See the [roadmap](docs/ROADMAP.md), [architecture notes](docs/ARCHITECTURE.md), and [plugin proposal](docs/PLUGIN_SYSTEM.md).

## Current state

No application code has been started in this repository. The immediate goal is to preserve the vision and make careful, evidence-based architecture decisions before implementation begins.

## Contributing

Early feedback on feasibility, CAD kernels, GPU rendering, plugin architecture, licensing, and test strategy is welcome. Read [CONTRIBUTING.md](CONTRIBUTING.md) before proposing implementation work.
