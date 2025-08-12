## MMORPG (Work in progress)

**This is a personal exploration into building a modern, scalable, and robust backend for a massively multiplayer online game, written from the ground up in Rust.**

This repository is the master project that consolidates the three core components: the **game server**, the **game client**, and the **Kubernetes deployment manifests**. It demonstrates a full-stack, end-to-end approach to building and deploying a real-time, distributed system.

---

## Technical Architecture at a Glance

The entire system is designed around principles of decoupling, performance, and data-oriented design.

*   **Language of Choice:** **Rust**, for its performance, memory safety, and fearless concurrency, which are critical for building stable, high-throughput servers.
*   **Engine & ECS:** The server leverages the **Bevy** engine as a headless, data-oriented **Entity Component System** for clean and highly performant state management.
*   **Networking Protocol:** A dual-protocol approach is used for optimal efficiency:
    *   **UDP (`netcode.io`):** For high-frequency, low-latency game state (player movement, animations).
    *   **WebSockets:** For reliable, out-of-band social features like chat.
*   **Serialization:** **FlatBuffers** is used for its zero-copy deserialization, minimizing CPU overhead and memory allocations on the server.
*   **Deployment:** The entire backend is containerized with **Docker** and orchestrated with **Kubernetes (K3s)** on a bare-metal homelab, demonstrating a full infrastructure-as-code pipeline.
*   **Client:** A **Godot** client with a **Rust GDExtension** core for high-performance communication with the server.

---

## Core Components (as Git Submodules)

This project is organized into three distinct components. Click into any directory to see its specific codebase and detailed README.

*   **`/server`**: The heart of the project. A multi-threaded, asynchronous Rust application built on Bevy that manages all game logic, state, and networking.
*   **`/client`**: A demonstration game client built in Godot. It interfaces with a "headless" Rust networking library via GDExtension, creating a clean separation between game UI (GDScript) and core logic (Rust).
*   **`/deployment`**: Declarative, production-ready infra as code for deploying the entire server stack (game server, social server, and PostgreSQL database) to a Kubernetes cluster.

