# 🛡️ ClipShield (v1.1.0)

**Proactive ClickFix defense & protection**  
Stop malicious clipboard payloads before they are pasted/executed.

Client-side only. Zero telemetry. Open source.  
[![License: GPL-3.0](https://img.shields.io/badge/License-GPL_3.0-blue.svg)](https://www.gnu.org/licenses/gpl-3.0) 
[![Manifest V3](https://img.shields.io/badge/Manifest-V3-blue.svg)](#) 
[![Privacy](https://img.shields.io/badge/Privacy-Zero_Telemetry-mintgreen.svg)](#)
---

## What ClipShield Does

ClipShield is a Chrome/Edge Manifest V3 extension focused on blocking clipboard-driven social engineering (including ClickFix-style flows).

It combines:

- **Clipboard write interception** in the page’s main world (`navigator.clipboard.writeText`, `navigator.clipboard.write`, and synthetic clipboard event abuse paths)
- **Background detection engine** with rule-based and heuristic analysis
- **DOM threat scanning** for fake verification/update/error lures
- **Warning + logging UX** (popup + warning page + alert history)

---

## Verified Detection Coverage (Current Codebase)

These numbers are derived from the current source:

- **240 rule-based detection patterns** in `background.js` (`DETECTION_RULES_MAP`)
- **142 lure phrases** in shared signals (`119 ClickFix-focused + 23 generic`)
- Additional heuristic signals for:
- command obfuscation and normalization (homoglyph/zero-width/caret/backtick variants)
- multi-stage download/decode/write/execute chains
- fragmented/padded payload evasion
- synthetic clipboard-event abuse
- fake CAPTCHA/update/error page behaviors

This means the project is better described as:

- **240+ detection rules**
- **140+ lure/SE phrases**
- **Layered heuristic and behavioral signals**

---

## Key Features

- **Pre-write clipboard protection**
- Intercepts and evaluates programmatic clipboard writes before malicious content is committed.
- **Main-world API patching**
- Runs at `document_start` in `MAIN` world to see real page clipboard calls.
- **ClickFix/LOLBAS-oriented detection**
- Includes PowerShell, cmd/LOLBAS, ms-appinstaller, UNC staging, obfuscated loaders, and macOS abuse patterns.
- **DOM threat hunting**
- MutationObserver-driven scans detect suspicious overlays/lures/scripted copy chains.
- **User allow-list**
- Domain allow-list is user-editable via options and respected by runtime checks.
- **Protection toggle**
- Popup includes on/off control (`protectionEnabled`) with live state sync.
- **Local alert history**
- Stores recent alerts locally (`chrome.storage.local`, capped history) for in-extension review.
- **Privacy-first**
- No telemetry or analytics code paths in the extension logic.

---

## Architecture (MV3)

- **`background.js`**: service worker; core analysis engine, alerting, storage, allow-list/protection state.
- **`content.js`**: DOM scanning, in-page warning modal, bridge between page and background.
- **`page_inject.js`**: main-world clipboard interception and synthetic event hardening.
- **`offscreen.js`**: offscreen clipboard utility + alert audio handling.
- **`shared_signals.js`**: shared lure phrase sets/regex.
- **`popup.* / options.* / warning.*`**: UI, settings, and warning surfaces.

---

## Permissions Used

From `manifest.json`:

- `clipboardRead`, `clipboardWrite`: clipboard inspection/clearing flows
- `storage`: settings + local alert history
- `offscreen`: offscreen document for clipboard/audio operations
- `notifications`: desktop threat notifications
- `scripting`, `activeTab`: runtime scripting helpers
- `host_permissions: <all_urls>`: protection across visited pages

---

## Privacy

ClipShield is designed for local-first operation:

- No analytics/telemetry pipelines
- No remote logging backend
- Data stays in extension storage (`chrome.storage.local` / `chrome.storage.sync`)

---

## Install

- Chrome Web Store: pending
- Edge Add-ons: pending

---

## Known Scope

ClipShield is strong against clipboard/social-engineering delivery chains, but no client-side extension can guarantee 100% prevention. It should be used as a protective layer alongside endpoint/browser security controls.

---

## Contributing

If you find new lure text, bypasses, or LOLBAS tradecraft:

- Open an issue
- Submit a PR

Project: [https://github.com/xorjosh/ClipShield](https://github.com/xorjosh/ClipShield)

---

## Showcase

<img width="1536" height="1024" alt="image" src="https://github.com/user-attachments/assets/985c5491-3c79-4dd1-976d-17f58938a4ef" />


Built by **Josh Allman**: [https://joshallman.co.uk](https://joshallman.co.uk)

