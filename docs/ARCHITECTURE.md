# Architecture Notes

**Status:** Draft for feasibility research. No architecture decision is final.

## High-level boundaries

### 1. Core CAD application

Owns the document model, geometry operations, feature history, constraints, undo/redo, selection, and application lifecycle. It must not require AI to start or perform ordinary CAD tasks.

### 2. Geometry kernel adapter

Provide a narrow internal interface around the selected geometry kernel. Evaluate Open CASCADE Technology first, while documenting licensing, platform, API, and packaging implications. Avoid spreading kernel-specific types through every subsystem.

### 3. Viewport and GPU services

The viewport should support responsive navigation, shading, selection, and large-model visualization. Vulkan is a candidate for rendering and compute, but should be validated with a small prototype on the target AMD/Linux hardware.

Do not assume every CAD operation belongs on the GPU. Exact boundary-representation operations and topology updates can be difficult to parallelize and may remain CPU-based. Move work to the GPU only when benchmarks demonstrate a worthwhile benefit.

### 4. Plugin host

Plugins extend the application through versioned APIs rather than depending on private internals. Begin with a small, documented interface. Python is a candidate for the first scripting/plugin language.

Third-party plugins must not automatically receive unrestricted access to files, processes, network connections, or credentials. Explore subprocess isolation and explicit capability/permission declarations. A Python API by itself is not a security sandbox.

### 5. Optional AI integration

AI belongs in optional plugins, not the core runtime. A provider adapter should make it possible to swap local inference engines or add optional remote providers without rewriting the CAD engine.

Proposed AI workflow:
1. Receive the user's request and permission-approved document context.
2. Produce a structured proposal using documented CAD commands.
3. Validate parameters and requested operations.
4. Preview changes and request confirmation when appropriate.
5. Execute through the CAD transaction system.
6. Report errors and allow undo.

AI is not the authority for geometric correctness. The geometry kernel and constraint system remain authoritative.

### 6. GPU resource coordination

Rendering and AI inference may compete for VRAM. Investigate memory budgets, model loading/unloading, workload scheduling, CPU fallback, and clear status reporting. Do not promise that a 24 GB GPU can run every model and every CAD workload concurrently.

## Initial architecture questions

- Which geometry kernel best fits licensing, platform support, STEP fidelity, and long-term maintenance?
- Can a minimal Vulkan viewport be reliable on the target Linux/AMD setup?
- Which workloads materially benefit from GPU compute?
- Which UI framework best balances native integration and maintainability?
- What is the smallest stable plugin API that supports useful extensions?
- How should document transactions, undo/redo, and plugin failures interact?
- What plugin permissions and isolation are practical for the first release?

## Non-goals for the first prototype

- Reimplementing a full geometry kernel from scratch.
- Feature parity with a mature commercial CAD suite.
- Built-in cloud accounts or mandatory cloud AI.
- Running every AI model simultaneously with the viewport.
- Claiming GPU acceleration without repeatable benchmarks.
