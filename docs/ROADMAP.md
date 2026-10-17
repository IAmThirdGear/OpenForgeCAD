# Roadmap

**Project status: Planning / research. Active implementation is on hold.**

This roadmap is milestone-based. Dates will be added only when scope and feasibility are better understood.

## Milestone 0: Feasibility research

- [ ] Compare candidate geometry kernels and licensing.
- [ ] Review Vulkan and Qt options for a Linux desktop application.
- [ ] Define initial target hardware and supported operating systems.
- [ ] Test the smallest possible GPU viewport on target AMD hardware.
- [ ] Compare local AI runtime options for AMD/Linux compatibility.
- [ ] Record decisions and unresolved risks.
- [ ] Define a repeatable build and test environment.

**Exit criteria:** a documented architecture proposal with evidence, tradeoffs, and a minimal prototype plan.

## Milestone 1: Viewport and geometry proof of concept

- [ ] Open a native desktop window.
- [ ] Render a basic 3D scene.
- [ ] Create or load a simple solid through the chosen geometry kernel.
- [ ] Support camera navigation and basic object selection.
- [ ] Export a valid STEP or STL file.
- [ ] Record performance and correctness tests.

**Exit criteria:** a reproducible demo that can create or load a solid and export it.

## Milestone 2: Foundational CAD workflow

- [ ] Add document save/load.
- [ ] Add basic sketch and feature concepts.
- [ ] Add a small set of parametric operations.
- [ ] Implement undo/redo and validation.
- [ ] Test model regeneration after dimension changes.

**Exit criteria:** a small part can be edited predictably and reopened without data loss.

## Milestone 3: Plugin API

- [ ] Define a versioned plugin manifest.
- [ ] Add one example plugin.
- [ ] Define command registration and UI extension points.
- [ ] Document permissions and failure handling.
- [ ] Add compatibility tests.

**Exit criteria:** an independently developed example plugin can be installed, disabled, and tested.

## Milestone 4: Optional local AI plugin

- [ ] Define a provider adapter.
- [ ] Connect one local inference backend.
- [ ] Translate a narrow set of natural-language requests into structured commands.
- [ ] Validate proposed operations before execution.
- [ ] Provide preview, confirmation, error reporting, and undo.
- [ ] Benchmark VRAM use alongside the viewport.

**Exit criteria:** a local model can propose and safely execute a limited set of validated CAD operations.

## Later research areas

- Assemblies and joints.
- Engineering drawings.
- STEP/3MF workflow improvements.
- CAM and manufacturing extensions.
- Mesh generation and image-to-3D workflows.
- Simulation and topology optimization.
- Community plugin registry and signing.
- Additional GPU compute paths where benchmarks justify them.

## Scope control

Each milestone should produce a useful, testable result. Avoid starting multiple major subsystems simultaneously. Revisit this roadmap when active work resumes.
