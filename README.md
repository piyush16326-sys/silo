# Silo - Hybrid AI Coding Assistant (HTML/CSS/JS GUI)

A lightweight, high-performance web-based graphical user interface (GUI) designed to interact with the **Qwen2.5-Coder** model family via **Ollama**.

This project showcases a creative **hybrid infrastructure** designed to bypass local hardware limitations. It runs an ultra-lightweight AI model locally on legacy consumer hardware, while bursting to a larger, high-capacity model running in the cloud via Google Colab—all managed seamlessly through a custom vanilla web interface.

---

## 🎨 The GUI Interface

The front-end is built using pure web technologies (**HTML5, CSS3, and Vanilla JavaScript**). By avoiding heavy frameworks like React, Vue, or Electron, the interface maintains a near-zero memory footprint, reserving 100% of the local machine's computational power for local AI inference.

### Key GUI Features:

* **Token Streaming:** Real-time, chunk-by-chunk markdown rendering using the browser's Streams API.
* **Code Sandbox Blocks:** Auto-detects programming languages, applies syntax highlighting via `Prism.js`, and adds quick-copy clipboard shortcuts.
* **Smart Context Persistence:** Retains chat history locally using browser `localStorage` so your data survives page reloads.
* **Tailored Prompting:** Automatically detects when you are asking for design/style help and enforces class and tag boundaries dynamically behind the scenes.

---

## 📐 Architecture Overview

The system operates across two computing nodes depending on the complexity of the task:

### 1. Local Edge Node (Low Latency)

* **Hardware:** **HP Notebook 15-ba001ax** (AMD A8-7410 APU, AMD Radeon R5 Graphics, legacy architecture).
* **Engine:** Local Ollama instance.
* **Model:** `qwen2.5-coder:0.5b`
* **Purpose:** Quick scripts, quick syntax debugging, and offline automation tasks.

### 2. Cloud Burst Node (Deep Logic)

* **Hardware:** Google Colab Backend (NVIDIA T4 / A100 GPU compute environments).
* **Engine:** Remote Ollama instance bridged via an unrestricted **Cloudflare Tunnel** (`cloudflared`).
* **Model:** `qwen2.5-coder:3b` (or `7b`)
* **Purpose:** Advanced frontend application scaffolding, algorithm refactoring, and multi-file debugging.

---

## 📁 Project Structure

```text
├── index.html              # Main GUI structure & UI elements
├── colab_tunnel.ipynb   # Jupyter Notebook script to deploy on Google Colab

```

---

## 🛠️ Quick Start

### 1. Local Node Setup

1. Download and install [Ollama](https://ollama.com/).
2. Pull the lightweight engine model in your terminal:
```bash
ollama pull qwen2.5-coder:0.5b

```


3. Launch your `index.html` file using an extension like VS Code Live Server (`http://127.0.0.1:5500`).

### 2. Cloud Node Setup

1. Upload `colab_tunnel.ipynb` to Google Colab and execute the cell.
2. Copy the active public execution link printed at the bottom (e.g., `https://xxxx.trycloudflare.com/api/chat`).
3. Open `index.html`, locate the script tag, `OLLAMA_TUNNEL_URL` constant, paste your link inside it, and save the file.

---

## 💖 Hardware Sponsorship & Compute Support

Optimizing and building modern AI applications on a **2016-era HP Notebook 15-ba001ax** introduces aggressive hardware constraints—particularly around VRAM limitations, memory bus bandwidth, and CPU processing cycles. While software architecture choices (like choosing vanilla JS over heavy compilation frameworks) can mitigate some load, engineering complex workflows is fundamentally restricted without modern hardware.

If you are a hardware manufacturer, cloud compute vendor, or an individual passionate about making local AI accessible to developers in lower-compute regions, **I am actively seeking hardware sponsorships.**

### 🎯 How Your Support Helps:

* Scaled benchmarking of local `7B`, `14B`, and `32B` parameter models on newer consumer chips.
* Developing optimization documentation and tutorials for developers running legacy hardware configurations globally.
* Refining low-bit quantization testing layers for tiny web wrappers.
* Building AI agents that solve problems.

### 🤝 Strategic Opportunities:

* **Hardware Partnerships:** Provisioning modern development laptops, mini-PCs, or consumer GPUs to expand on-device compilation capacity.
* **Cloud Infrastructure Credits:** API or server access keys for managed runtime instances (RunPod, Vast.ai, AWS, etc.).

*To discuss setup integrations, collaborations, or hardware sponsorships, please contact me directly via **[LinkedIn](https://www.linkedin.com/in/piyush-agarwal-8801903ba/)** or open a formal issue in this repository.*

---

## 📄 License

Distributed under the MIT License. See `LICENSE` for more information.
