# 🛡️ ClipShield (v1.1.0)
### **Proactive ClickFix Defense & Protection**
### Stop Malicious Copy-Paste Before It Executes

> **Clipboard Attack Protection & ClickFix Defense**  
> *Client-side only. Zero telemetry. 100% open source.*

[![License: GPL-3.0](https://img.shields.io/badge/License-GPL_3.0-blue.svg)](https://www.gnu.org/licenses/gpl-3.0) 
[![Manifest V3](https://img.shields.io/badge/Manifest-V3-blue.svg)](#) 
[![Privacy](https://img.shields.io/badge/Privacy-Zero_Telemetry-mintgreen.svg)](#)

**ClipShield** is a specialized security layer designed to neutralize **"ClickFix"** social engineering—the fastest-growing delivery method. By monitoring DOM interactions and intercepting programmatic clipboard writes, ClipShield blocks malicious commands before they ever land on your system.

[**Install from Chrome Web Store**](#) 

---

## 🚀 Why ClipShield?
Modern attackers no longer rely solely on `.exe` downloads. They trick users into **copying** a malicious commands via fake "Verify you are human" prompts and **pasting** it into their terminal. 

* **The Threat:** Social engineering lures (fake CAPTCHAs, update prompts) that lead to user-assisted execution.
* **The Payload:** Living-off-the-land binaries (**LOLBAS**) that bypass traditional file scanners.
* **The Solution:** ClipShield acts as a **firewall for your clipboard**, analyzing payloads in real-time.

---

## 🛠️ Core Defense Features

### 🧠 Real-Time Clipboard Protection
* **Synchronous Blocking:** Intercepts `navigator.clipboard.writeText()` calls before the payload is written.
* **500+ Detection Signals:** High-fidelity analysis of patterns like `iex()`, `irm`, `Invoke-WebRequest`, and execution policy bypasses.
* **LOLBAS T1105 Coverage:** Complete monitoring for remote file copy and execution chains.

### 🔍 Proactive Threat Hunting
* **Deep DOM Scanning:** Identifies 130+ social engineering triggers, including "Press Win+R" or "Ctrl+V" instructions.
* **Obfuscated Loader Analysis:** Unpacks and scans embedded payloads and hidden scripts often missed by static filters.
* **LOLGlobs Detection:** Advanced wildcard detection for obfuscated command-line patterns.

### 🔒 Privacy by Design
* **Zero Telemetry:** 100% client-side execution. No analytics, no tracking, and no data collection.

---

## 🔍 Technical Architecture
ClipShield utilizes a **Manifest V3** architecture to provide deep inspection without compromising performance.

| Component | Function |
| :--- | :--- |
| **Main World Injection** | Injected at `document_start` to intercept API calls at the source. |
| **Offscreen API** | Handles heavy heuristic analysis off the main thread to ensure zero lag. |
| **Forensic Threat Log** | Expandable logs providing payload breakdowns and confidence scoring. |
| **Host Permissions** | Comprehensive protection across `<all_urls>`. |

---

## 🛡️ Getting Started
1.  **Install the extension** from the Chrome Web Store.
2.  **Browse normally.** ClipShield runs silently in the background.
3.  **Automatic Alerts:** If a threat is detected, execution is blocked, and you will receive a **Critical Alert**.
   
---

## 🤝 Contributing & Intel
If you find a new lure or a bypass technique, please open an issue or submit a PR or reach out to me on social media.

**Built by:** [xorjosh (Josh Allman)](https://github.com/xorjosh)  
**License:** GNU General Public License (GPL-3.0)

---
