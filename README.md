**SB Stability Tracker (SBST)** 

Is a Windows diagnostic and performance-analysis utility developed by ShrimpBrime for PC gamers, hardware enthusiasts, overclockers, and competitive benchmarkers.

A random stutter, a WHEA warning, a sudden frame-time spike, or an unexplained restart can have several possible causes. SBST brings hardware telemetry, Windows error evidence, frame pacing, and session history together, helping you identify **what happened, what the evidence supports, and what to test next**—instead of blindly changing settings or replacing hardware.

**Current release:** Build 519 · Windows x64 · Digitally signed and timestamped

## Why use SBST?

Traditional monitoring tools show numbers. SBST is designed to put those numbers **in context**.

Rather than treating one temperature, clock, or error message as a definitive diagnosis, SBST correlates multiple sources of evidence and recommends practical next steps. Its goal is to make intermittent gaming and PC stability problems easier to investigate, reproduce, and compare.

### Built for

- **PC gamers** investigating stutter, hitches, frame pacing, freezes, and inconsistent performance.
- **Overclockers and undervolters** checking stability evidence after hardware or BIOS changes.
- **Hardware enthusiasts** tracking CPU, GPU, storage, power, and Windows device health.
- **Benchmarkers and system tuners** comparing performance sessions and isolating background interference.
- **PC troubleshooters** investigating WHEA events, unexpected restarts, driver issues, and intermittent faults.

## Standout features

### SB Diagnostic Intelligence (SDI)

SDI is SBST's **local, evidence-driven diagnostic engine**. It reviews available system data and organizes findings into an actionable diagnostic report.

- Correlates hardware telemetry, Windows events, WHEA evidence, device state, background activity, and performance data.
- Highlights the most relevant suspected **component or failure path** without claiming a confirmed defect.
- Explains the reasoning, supporting evidence, uncertainty, and **Best Next Test**.
- Offers **Simplified** and **Technical** report views.
- Supports optional guided questions, controlled verification, and **before/after retest comparisons**.
- Keeps local **Case History** and an incident timeline, with exportable reports for later review.

**SDI is diagnostic reasoning, not a cloud AI service.** It helps narrow the investigation; it does not guarantee a root cause.

### Frame Performance — powered by PresentMon

Go beyond average FPS and look at the consistency of the actual gaming experience.

- FPS, frame times, **1% lows**, and **0.1% lows**.
- Frame pacing, hitches, severe stalls, and frame-time trends.
- Automatic or manual capture of supported rendering processes.
- Local session history, reports, and comparison between captures.
- On-screen performance overlay and correlation with available system evidence.

SBST uses an external **PresentMon 2.5.1** collector. It does **not inject code into games**, hook game renderers, or modify game memory for frame capture.

### Live CPU, GPU, and power telemetry

Monitor supported hardware in one dashboard, with additional detail in the dedicated sensor views.

- CPU load, clock speeds, temperature, logical-processor activity, and package power when available.
- **Core VID** (CPU-requested voltage) kept distinct from **Vcore** (measured/reported voltage rail).
- GPU load, clocks, temperatures, VRAM usage and temperature, power, and cooling readings when exposed by the hardware/driver.
- Active-display GPU selection to avoid confusing an integrated or disabled adapter with the GPU driving the primary display.
- Power Sensor Map with discovered sensor names, sources, values, and access diagnostics.

Sensor coverage depends on the CPU, motherboard, firmware, drivers, and telemetry provider. Unsupported or unavailable values are shown as **N/A** rather than fabricated.

### WHEA, DPC/IRQ, and stability evidence

- Windows **WHEA-Logger** monitoring and hardware-error history.
- DPC and interrupt activity with relevant background-process context.
- Evidence from device status, Windows events, and recent system instability.
- Post-crash investigation, saved diagnostic reports, and optional deeper crash analysis when the required Microsoft debugging tools are available.

A corrected WHEA event or elevated interrupt sample is a clue—not automatic proof of a defective part.

### SSD and storage analysis

- Physical-drive inventory and matched Windows device status.
- Available NVMe/SATA temperature and SMART/health information.
- Wear, power-on time, error indicators, and reported latency where supported.
- Live drive-temperature history and SDI storage interpretation.

### Game Session Guard

SBST automatically recognizes sustained game/render workloads and adjusts its own behavior to reduce unnecessary interference.

- Keeps frame-performance and other supported Windows-based diagnostics active during gameplay.
- **Pauses selected low-level LibreHardwareMonitor/PawnIO sensor refreshes** during protected game sessions.
- Labels suspended readings **PAUSED** instead of presenting old measurements as live.
- Blocks SBST-controlled hardware, driver-profile, and system-setting writes during protected sessions.
- Resumes low-level telemetry after the game ends and the release-grace period completes.

This is a risk-reduction design, **not a guarantee of compatibility with every anti-cheat system**.

### Optional gaming and Windows tools

SBST includes user-controlled utilities alongside its diagnostic features:

- **OS Tweaker:** review and, where supported, adjust selected reversible Windows gaming settings.
- **SDI Driver Neuro Tuner:** examine supported per-game driver controls and apply approved changes with undo/restore paths for SBST-managed settings.
- **Power controls:** inspect Windows power plans and advanced power-policy settings.
- **Internet Gaming / Net Tuner:** examine latency, jitter, packet loss, and selected Windows networking settings.
- **KB + Mouse:** local input timing tests and common Windows input checks.
- **Hardware Library and Support:** view compatibility information, telemetry sources, and diagnostic status.

Availability varies by hardware, driver, and Windows version. **SBST does not automatically overclock or undervolt your PC.** Changes are intentional, and privileged actions may require separate confirmation.

### Customizable interface

- Clean **Obsidian** styling with additional appearance options.
- Optional custom SDI background image.
- Custom-image brightness control from **15% to 100%**, defaulting to **60%**.
- Compact performance information, hardware views, local screenshots, and diagnostic reports.

## Download and installation

1. Open this repository's **Releases** page.
2. Download the latest **signed Windows x64 release ZIP**.
3. Extract the **entire ZIP** to a folder of your choice; keep the included runtime files and `Tools/PresentMon` directory together.
4. Run **`SBStabilityTracker.exe`** from the extracted folder.
5. Review and accept the included end-user license agreement to use the application.

Build 519 is published as a **self-contained .NET 8 Windows x64 application**, so a separate .NET runtime installation should not be required for the packaged release.

**Administrator rights are not required for ordinary startup.** SBST may offer **Full Hardware Telemetry** after launch. Approving the Windows UAC prompt starts an optional elevated telemetry session for additional supported low-level sensors. Some user-requested Windows configuration changes may also require elevation.

> **Get the application from the official release package.** Windows SmartScreen reputation warnings may still appear for newly distributed signed applications. Check the publisher, signature, and published hashes before running a downloaded executable.

## Quick start: diagnose a stutter or crash

1. **Launch SBST** before starting your game or other problem workload.
2. **Enable SDI** so the application can begin collecting local diagnostic context.
3. **Reproduce the issue** under your usual conditions, if practical and safe.
4. Open **DIAGNOSE** and review **What SBST Found** and the **Best Next Test**.
5. Change **one variable at a time** when following a suggested troubleshooting step.
6. Use **BEGIN RETEST NOW** and **COMPARE RETEST NOW** to examine the same diagnostic path after the change.
7. Save or export the report if you want to keep the evidence or request help.

For frame pacing, open **FRAME PERF** to capture and compare a gaming session. For temperatures and power, use the dashboard and **POWER** sensor views.

**A clean retest is useful evidence, not proof of a permanent fix.**

## Optional PawnIO and advanced telemetry

SBST uses **LibreHardwareMonitor** for many supported hardware sensors. Some Ryzen, Intel, motherboard, MSR/SMN/SMU, and other low-level readings require additional hardware access. **PawnIO** is an optional third-party component that can provide this access on compatible systems.

- PawnIO is **not the SBST application** and is not silently installed by SBST.
- The official standard signed PawnIO installation can be used; a developer/unrestricted install is not a general requirement.
- With suitable hardware, drivers, and permissions, **Full Hardware Telemetry** can expose additional CPU temperature, package-power, voltage, and motherboard readings.
- If a sensor is unavailable, SBST reports **N/A**; a driver being installed does not guarantee that a specific sensor exists or can be read.
- During protected game sessions, PawnIO-backed low-level refreshes may show **PAUSED** by design.

Official PawnIO project: https://pawnio.eu/

## Compatibility and requirements

- **Operating system:** Modern 64-bit Windows (Windows 10/11).
- **Architecture:** x64.
- **Distribution:** Portable-style, self-contained .NET 8 release ZIP.
- **CPU support:** Intel Core and AMD Ryzen telemetry paths; supported fields depend on platform and access.
- **GPU support:** Supported NVIDIA GeForce, AMD Radeon, and Intel graphics through available telemetry sources.
- **Storage:** Supported NVMe and SATA devices with available Windows/SMART data.
- **Frame capture:** PresentMon availability and supported Windows graphics/ETW paths.

Not every feature is available on every PC. Some values depend on hardware sensor exposure, firmware, user permissions, Windows services, or installed graphics drivers.

## Privacy and safety

**Local-first diagnostics are a core design principle.**

- Core SDI analysis runs **on your PC**, not through a cloud AI model.
- SBST does not operate a mandatory telemetry-upload or diagnostic-log collection service in this release.
- Settings, history, reports, screenshots, and recovery information may be stored locally.
- Reports and screenshots are shared **only when you choose to export or send them**; review them before public posting.
- Optional crash forensics using Microsoft debugging tools may download symbols from Microsoft's public symbol server.
- Buttons that open official third-party resources can launch your web browser.
- Optional tweaks are distinct from read-only diagnostics, and Game Session Guard restricts supported changes during protected gameplay.

See the included **`Legal/PRIVACY_POLICY.txt`** and **`EULA.txt`** for the applicable release terms and data-handling details.

## Troubleshooting

| Symptom | What to check |
| --- | --- |
| CPU temperature, package power, or Vcore shows **N/A** | Open **POWER** and **SUPPORT** to inspect sensor discovery, PawnIO state, and Full Hardware Telemetry availability. |
| A sensor changes to **PAUSED** during gameplay | This can be expected while **Game Session Guard** protects a detected game. |
| The wrong GPU appears | Confirm the primary display connection, GPU driver/device status, and hardware discovery information. |
| Frame Performance cannot start | Keep `Tools/PresentMon/PresentMon.exe` with the extracted release and check application diagnostics. |
| A Windows change is unavailable | Some operations require an explicit UAC approval or are blocked while a game is protected. |
| A reading seems implausible | Cross-check it with the motherboard vendor's tooling or another trusted sensor application before drawing conclusions. |

If you report an issue, include your **SBST build number**, Windows version, CPU/GPU/motherboard models, relevant steps to reproduce, and a **reviewed, share-safe** diagnostic export when appropriate. Never share passwords, signing credentials, or private files.

## Build 519 highlights

- Improved AMD Ryzen CPU temperature, package-power, VID, and Vcore mapping.
- Corrected a misleading **1.550 V** Ryzen VID decoding case without treating VID as measured Vcore.
- Improved Full Hardware Telemetry prompting when key low-level CPU sensors are missing.
- Expanded PawnIO installation/driver-state and privilege diagnostics.
- Retained active-display dGPU selection, Obsidian appearance, and custom-image brightness settings.
- Release executable digitally signed via Microsoft Azure Artifact Signing and timestamped.

### Build 519 SHA-256 checksums

**Signed executable — `SBStabilityTracker.exe`**

```
FBB7EEDB28931C6F7A22D5A2FA6050F4405849F3CB34D9C2491A831702391AED
```

**Signed release archive — `SBST_519_SIGNED_win-x64.zip`**

```
90B1A98827A6C24AD3D9EF1B923C0A39B21D0E3382C934C68E9DAEB2BC00CB16
```

To check a downloaded file using PowerShell:

```powershell
Get-FileHash .\SBST_519_SIGNED_win-x64.zip -Algorithm SHA256
Get-AuthenticodeSignature .\SBStabilityTracker.exe
```

The second command applies to the executable after extraction. The verified Build 519 signed publisher is **Jon Bauer**.

## Third-party acknowledgments

SBST relies on or interoperates with third-party software and APIs, including:

- [LibreHardwareMonitor](https://github.com/LibreHardwareMonitor/LibreHardwareMonitor) — hardware telemetry.
- [PresentMon](https://github.com/GameTechDev/PresentMon) — external frame-performance capture.
- [PawnIO](https://pawnio.eu/) — optional low-level hardware access.
- [WPF UI](https://github.com/lepoco/wpfui) — Windows interface components.
- Microsoft .NET / Windows diagnostic interfaces, and supported AMD/NVIDIA driver interfaces.

Each component remains subject to its own license and terms. See **`Legal/THIRD_PARTY_NOTICES.txt`** and the accompanying license texts for versions, attribution, and rights.

## License and ownership

**SB Stability Tracker is proprietary software; this repository or its release downloads should not be interpreted as an open-source license for SBST's application code or SDI logic.** Third-party open-source components retain their respective license rights.

Copyright © 2026 **ShrimpBrime Tech**. All rights reserved in SBST proprietary materials.

**ShrimpBrime™**, **SB Stability Tracker™**, and **SB Diagnostic Intelligence™** are claimed trademarks. Third-party marks belong to their respective owners.

For complete terms, read the distributed **`EULA.txt`**, **`Legal/SBST_PROPRIETARY_NOTICE.txt`**, and **`Legal/THIRD_PARTY_NOTICES.txt`**.

---

**SBST isn't about chasing a better-looking number. It's about understanding your PC, isolating problems with evidence, and making informed changes for a smoother, more stable gaming experience.**
