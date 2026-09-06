# Relay AI Hub

A lightning-fast, privacy-first local AI gateway and interop hub built with **Go**, **Wails**, and **Ollama**. RelayAI bridges the gap between fragmented AI models, local inference engines (such as LM Studio and Ollama), and third-party applications, providing a unified standard protocol for multi-dimensional AI traffic routing, zero-config fallbacks, and multi-model management—keeping all local data entirely on your machine.

---

## The Vision: A Standardized Protocol for AI Interoperability

As applications increasingly integrate multiple large language models, developers face severe friction: fragmented API formats, manual API key management, unpredictable rate limits, and zero unified local-to-cloud fallback mechanisms. **RelayAI** introduces a clean, open standard protocol for AI routing that acts as an OS-level background service (Daemon) and a centralized Control Plane.

Whether you are managing local development models or enterprise cloud pipelines, RelayAI ensures your apps communicate seamlessly through a single open standard:

* **Unified Protocol (`RelayAI Interop Protocol`):** Standardize all upstream and downstream AI requests behind a single open specification compatible with standard API formats.
* **Intelligent Routing & Failover:** Automatically switch between cloud flagships (GPT-4, Claude) and local inference nodes (Ollama, LM Studio) during rate limits or network disruptions.
* **Zero-Config Local Privacy:** Intercept and route sensitive prompts to local engines while passing non-sensitive payloads to cloud providers.

---

## Features

* **Unified AI Gateway Proxy:** Act as a central relay hub for all local apps, microservices, and IDE tools needing AI access without duplicating configuration code.
* **Multi-Model Load Balancing & Fallback:** Seamlessly distribute traffic across local and cloud providers with automated error recovery.
* **100% On-Device Privacy:** Route data locally through Ollama or LM Studio endpoints, ensuring your prompts never leave your hardware unless specified.
* **Blazing Fast Concurrency:** Built natively in Go for ultra-low latency, minimal memory overhead, and high-throughput streaming (SSE).
* **Cross-Platform Control Plane:** Powered by **Wails**, providing a lightweight, modern web-based dashboard and native desktop binary for macOS, Windows, and Linux.

---

## Tech Stack

* **Backend & Daemon:** Go (`1.22+`), concurrent HTTP/SSE proxy engines, Unix Domain Sockets / IPC support, local storage for routing rules and telemetry logs.
* **Frontend Control Plane:** Wails runtime bindings paired with a modern reactive web framework and Tailwind CSS for real-time traffic monitoring and configuration management.
* **AI Engine Integrations:** Native connectors for Ollama, LM Studio, OpenAI-compatible APIs, and custom local endpoints.

---

## Project Structure

```text
relay-ai/
├── build/             # App build assets, icons, and packaging config
├── frontend/          # Web UI dashboard source files (UI components, styling)
├── core/              # Go core proxy, routing engine, and protocol logic
├── app.go             # Main Wails application controller & IPC bindings
├── go.mod             # Go module dependencies
├── go.sum             # Go checksums
├── main.go            # Entry point for the Wails desktop application
└── wails.json         # Wails project configuration

```

---

## Prerequisites

Before running or building RelayAI, make sure you have the following installed on your system:

1. **Go** (version 1.22 or newer)
2. **Node.js** (version 18+ for frontend asset bundling)
3. **Wails CLI**:
```bash
go install github.com/wailsapp/wails/v2/cmd/wails@latest

```


4. **Local Model Runner** (Ollama or LM Studio):
* [Ollama](https://ollama.com) running locally on default port `11434`.



---

## Getting Started

### 1. Clone the Repository

```bash
git clone https://github.com/username/relay-ai.git
cd relay-ai

```

### 2. Run in Development Mode

Wails provides a live-reloading development server that hot-reloads both your Go daemon backend and frontend control panel UI:

```bash
wails dev

```

### 3. Build for Production

To compile a standalone, optimized native binary for your operating system:

```bash
wails build

```

The compiled binary will be located in the `build/bin` directory.

---

## Usage

1. Launch **RelayAI**.
2. Configure your upstream endpoints (e.g., connect your local Ollama/LM Studio instance and add cloud API keys if needed).
3. Point your client applications or scripts to the RelayAI local proxy endpoint (e.g., `http://localhost:8080/v1`).
4. Monitor live requests, token consumption, and routing rules dynamically through the desktop dashboard.

---

## License

This project is open-source software licensed under the [MIT License](https://www.google.com/search?q=LICENSE).
