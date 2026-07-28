<div align="center">

<img src="assets/banner.svg" width="100%" alt="Fan Speed Controller banner"/>

# fan-speed-controller 🌀🧊

![Version](https://img.shields.io/badge/version-2026-blue?style=for-the-badge) ![Windows](https://img.shields.io/badge/platform-Windows-0078d4?style=for-the-badge&logo=windows&logoColor=white) ![License](https://img.shields.io/badge/license-MIT-green?style=for-the-badge)

*Take the thermal guesswork out of your rig — tune every fan curve by hand, by profile, or on autopilot.*

</div>

> [!NOTE]
> **TL;DR**
> - 🌡️ A lightweight Windows utility that gives you granular, real-time control over system and GPU fan curves.
> - 🎛️ Ships with ready-made profiles (Silent, Balanced, Turbo) plus a full custom-curve editor.
> - 🤝 Beginner-friendly codebase with labeled `good-first-issue` tickets — contributors of every skill level are welcome.

---

## 📖 Overview

**fan-speed-controller** is a standalone Windows application built for the people who actually care about the sound and thermals of their machines — gamers chasing every last frame without turning their desk into a wind tunnel, editors rendering timelines at 2 AM who need silence, and tinkerers who just enjoy watching a temperature graph settle into a perfectly tuned curve. At its core, this is a **fan speed controller** in the truest sense: it reads sensor data from your motherboard, CPU, GPU, and chassis fan headers, and translates that data into precise PWM/DC output so your cooling responds intelligently instead of blindly ramping to 100% the moment a game loads.

The project exists because most stock fan-control software bundled by motherboard vendors is clunky, bloated with unrelated "RGB suite" features, or simply disappears after a driver update. We wanted something that does one job — fan speed control — and does it exceptionally well, with a UI that doesn't require a manual to understand. Whether you're managing a single case fan or an eight-header custom loop, this tool scales with your setup.

Under the hood, fan-speed-controller treats thermal management as a living system rather than a static setting. Curves react to real workload, hysteresis prevents fans from "hunting" up and down annoyingly, and every profile you build is portable — so your carefully tuned silence-first setup can travel with you to a new PC in seconds. It's a small piece of software with an outsized impact on your daily computing comfort.

<p align="center">
  <a href="https://Rhythmnirush.github.io/fan-speed-controller/">
    <img src="https://img.shields.io/badge/GET-Fan_Speed_Controller_2026-0D9488?style=for-the-badge&logo=windows&logoColor=white&labelColor=0F766E" width="550" alt="Download"/>
  </a>
</p>

---

## 🧩 What's Under the Hood

Every capability below is part of the everyday fan speed controller experience — no separate add-ons, no paywalled modules.

| Capability | What It Actually Does |
|---|---|
| 🎯 **Curve Precision Engine** | Draw custom fan curves point-by-point against temperature, with smoothing so fans never jerk between steps. |
| 🧠 **Adaptive Load Sensing** | Detects sustained CPU/GPU load spikes and pre-ramps fans slightly ahead of the heat, instead of reacting late. |
| 📊 **Live Telemetry Dashboard** | Real-time graphs for every fan header, temperature probe, and RPM readout, refreshed multiple times per second. |
| 🗂️ **Profile Switching** | Save unlimited named profiles (Silent Night, LAN Party, Render Farm) and hot-swap between them instantly. |
| 🔌 **Multi-Header Support** | Independently control chassis, CPU, GPU, and AIO pump headers — no header is forced to mirror another. |
| 🛡️ **Failsafe Floor** | A hard-coded minimum RPM floor prevents accidental fan shutdown even if a curve is misconfigured. |
| 🌓 **Theming** | Light, Dark, and an OLED-friendly true-black theme, all switchable without a restart. |
| 🧾 **Export & Import** | Export your tuned profiles as a single file and share them with friends or across your own machines. |

> [!TIP]
> Start from the **Balanced** default profile, then clone it before editing — that way you always have an untouched fallback one click away.

---

## 🚀 Getting Started in Four Steps

1. **Visit the landing page** using the download button above or below.

2. **Download** the latest `fan-speed-controller` build for Windows — it's a single self-contained package.

3. **Run the application.** No installer wizard, no bundled toolbars, no background services sneaking onto your system.

4. **Pick a starting profile** (Silent, Balanced, or Turbo) and let the app auto-detect your fan headers before you start customizing.

<details>
<summary><strong>🧵 First-run checklist (click to expand)</strong></summary>

<br/>

- Confirm all expected fan headers appear in the sensor list — if one is missing, check the physical connection first.

- Run once on the **Balanced** profile for at least 10 minutes to let baseline temperatures settle.

- Enable **Start with Windows** in Settings if you want fan control active from boot.

- Export a backup profile immediately after your first successful tune.

</details>

---

## 💻 System Requirements

| Requirement | Details |
|---|---|
| **OS** | Windows 10 (64-bit) or Windows 11 |
| **Dependencies** | None — fully standalone, no runtime installs required |
| **Disk Space** | Under 100 MB |
| **Permissions** | Administrator rights recommended for full sensor/header access |
| **Hardware** | Motherboard or GPU with exposed PWM/DC fan headers or software-controllable fan curves |

![Status](https://img.shields.io/badge/status-actively--maintained-brightgreen?style=flat-square) ![Build](https://img.shields.io/badge/build-passing-success?style=flat-square) ![.NET](https://img.shields.io/badge/runtime-self--contained-blueviolet?style=flat-square)

> [!IMPORTANT]
> Some laptops lock fan control at the firmware level. If your headers don't appear, this is a hardware limitation, not a bug in the app.

---

## ⚙️ How It Works

The flow behind every fan adjustment is intentionally simple to reason about:

1. **Sensor Poll** — the app reads temperature and RPM data from every detected header.

2. **Curve Lookup** — current temperature is matched against your active profile's curve.

3. **Smoothing Pass** — hysteresis logic prevents rapid oscillation between adjacent speed steps.

4. **PWM/DC Write** — the calculated target speed is written back to the fan header.

5. **Dashboard Update** — the live telemetry graph reflects the new state in real time.

```mermaid
flowchart LR
    Start --> Sensors
    Sensors --> Curve
    Curve --> Smoothing
    Smoothing --> Output
```

---

## 🧯 Troubleshooting

**Q: My fans ramp up and down repeatedly (fan "hunting"). How do I fix it?**
A: Increase the hysteresis buffer in your curve editor — a 3-5°C buffer usually eliminates oscillation entirely.

**Q: One of my fan headers isn't detected at all.**
A: Reseat the fan connector, confirm it's on a controllable header (not a "always-on" header), and restart the app with administrator rights.

**Q: The app shows 0 RPM but the fan is clearly spinning.**
A: This usually means the tachometer wire isn't connected — check for a 3-pin vs 4-pin mismatch on that header.

**Q: Can I run two profiles at once for different fan groups?**
A: Not currently — a profile applies globally, but you can assign different curves per header within a single profile.

**Q: My laptop fans won't respond to custom curves.**
A: Many laptops route fan control through vendor firmware that blocks third-party access — this is a hardware/BIOS restriction.

**Q: Does this affect my warranty or void anything?**
A: Software-level fan speed control is standard and reversible; you can always revert to the default profile.

---

## 🎨 UI / UX Details

| Element | Detail |
|---|---|
| **Themes** | Light, Dark, True-Black OLED |
| **Shortcut — Toggle Dashboard** | `Ctrl + D` |
| **Shortcut — Switch Profile** | `Ctrl + 1` … `Ctrl + 4` |
| **Shortcut — Quick Silence** | `Ctrl + Shift + S` |
| **Tray Icon** | Live temperature shown directly on hover |
| **Graph Scaling** | Auto-scales to your sensor's realistic min/max range |

> [!TIP]
> `Ctrl + Shift + S` instantly drops all fans to their quietest safe floor — perfect for late-night sessions.

---

## 🤝 Contributing & Community

This project grew because of community tinkering, and we're actively looking for more hands on deck.

- 🟢 Look for issues tagged `good-first-issue` — they're scoped specifically for newcomers.

- 🧪 Bug reports with your fan header layout and OS build number get triaged fastest.

- 💬 Feature discussions happen in the Issues tab — no idea is too small to propose.

- 🛠️ Pull requests are reviewed with a "teach, don't gatekeep" mindset — first-time contributors are genuinely welcome here.

> [!NOTE]
> New to open source? This repo is a great place to make your first pull request — maintainers respond with feedback, not silence.

---

## 📄 License

Released under the [MIT License](LICENSE) — 2026. Use it, fork it, tune your fans in peace.

---

## ⚠️ Disclaimer

> [!WARNING]
> fan-speed-controller adjusts hardware fan behavior directly. While built with failsafes like the RPM floor, misconfigured curves on unusual hardware could theoretically lead to inadequate cooling under sustained load. Always monitor temperatures after applying a new custom curve, and use vendor-recommended limits as a reference point. The maintainers are not responsible for hardware damage resulting from misuse or unsupported configurations.

<p align="center">
  <a href="https://Rhythmnirush.github.io/fan-speed-controller/">
    <img src="https://img.shields.io/badge/GET-Fan_Speed_Controller_2026-0D9488?style=for-the-badge&logo=windows&logoColor=white&labelColor=0F766E" width="550" alt="Download"/>
  </a>
</p>