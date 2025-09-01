

🖥️ X870E BIOS — Must Settings 
31/08/2025
This profile is focused on:

✅ Performance (PBO undervolt, XMP/EXPO RAM)

✅ Efficiency (reduced power waste from unused devices)

✅ Clean boot (no auto-installer, no RGB)

🚫 No security features (Windows 10, TPM/Secure Boot disabled)

⚡ CPU & Memory

PBO → -20 Negative Curve All Cores
Uses Precision Boost Overdrive with negative curve (undervolts all cores for efficiency/performance balance).

DRAM Profile Setting → EXPO/XMP Profile
Enables pre-tuned memory timings for higher frequency RAM.

🔒 Security (Disabled for latency/perf gain)

fTPM → Disabled
Disables firmware TPM (used for Windows BitLocker & Secure Boot).

Trusted Platform Module → Disabled
Ensures TPM is fully disabled.

Pluton Security Processor → Disabled
Disables Microsoft Pluton (security co-processor).

Security Device Support → Disabled
Turns off TPM/Pluton enumeration.

Secure Boot → Disabled
Disables UEFI Secure Boot, allowing unsigned OS boot.

CSM → Disabled
Keeps system in pure UEFI mode (no legacy boot).

TSME → Disabled
Turns off Transparent Secure Memory Encryption.

SMEE → Disabled
Disables Speculative Memory Encryption Extensions.

🎮 GPU / PCIe

Re-Size BAR → Enabled
Lets CPU access full GPU VRAM (helps gaming).

dGPU Only Mode → Enabled
Disables iGPU, forces discrete GPU.

📡 Connectivity (Disabled if unused)

Bluetooth → Disabled

Wi-Fi → Disabled

WAN Radio → Disabled

Thunderbolt Support → Disabled

HDMI 2.0 Support → Disabled

🚀 Boot & System

Fast Boot → Disabled
Forces full POST for reliability (slower boot).

Setup Prompt Timeout → 3
BIOS boot menu waits 3 sec before OS loads.

Onboard Debug Port LED → Off
Turns off onboard POST LEDs.

Auto Driver Installer → Disabled
Prevents BIOS from auto-installing vendor drivers.

🎨 Aesthetics

RGB LED → Off
Disables motherboard RGB lighting.



🧪 OPTIONAL Tweaks (Latency/Performance Tuning)

These are not required but can be enabled for further optimization. They may increase idle power draw or affect stability.

⚡ CPU & Power Management

Global C-State Control → Disabled
Prevents CPU from entering deep sleep states → improves latency but higher idle watts.

ACPI _CST C1 Declaration → Disabled
Disables C1 reporting → helps reduce micro-latencies.

DF Cstates → Disabled
Disables Data Fabric low-power states.

Power Supply Idle Control → Typical Current Idle
Prevents “low current idle” PSU issues.

PSS Support → Disabled
Disables CPU power states (locks frequency scaling).

CPPC Dynamic Preferred Cores → Auto
Lets OS decide best cores for scheduling.

SoC/Uncore OC Mode → Enabled
Unlocks SoC OC for more memory/PCIe bandwidth.

💾 Memory

DRAM Performance Mode → Aggressive
Tighter timings for lower latency.

Memory Context Restore → Disabled
Forces full RAM training (slower boot, more stable).

Power Down Mode → Disabled
Keeps memory awake → lower latency.

Data Scramble → Disabled
Slight latency benefit.

🎮 PCIe / Bus Tuning

Spread Spectrum (CPU/PCIe/FCH) → Disabled
Disables clock modulation → cleaner signals for OC/latency (may increase EMI).

PCIe ARI Support → Auto

PCIe ARI Enumeration → Auto





# 🧠 ASRock X870E Nova WiFi + Ryzen 7800X3D BIOS Tweak Guide
**OS:** Windows 10  
**Goal:** Max performance, no security features, minimal latency, no bloat  
**Updated:** 2025-07-09  

---

## ✅ CPU & Virtualization
| Location | Setting | Value | Explanation |
|---------|---------|-------|-------------|
| Advanced > CPU Configuration | `PSS Support` | Disabled | Disables CPU power state switching; reduces latency for gaming. |
| Advanced > CPU Configuration | `SVM Mode (Virtualization)` | Disabled | Needed only for VMs (Hyper-V, VirtualBox). |
| Advanced > CPU Configuration | `AMD fTPM switch` | Disabled | Disables TPM, reducing stutters in some games. |
| AMD CBS > SMU Common Options | `CPPC Dynamic Preferred Cores` | Auto / Frequency | Leave on *Auto*, or set to *Frequency* if managing process priority manually (e.g., via Process Lasso). |

---

## 🔋 Power Management
| Location | Setting | Value | Explanation |
|---------|---------|-------|-------------|
| AMD CBS > CPU Common Options | `Global C-State Control` | Disabled | Prevents the CPU from entering low-power idle states. Reduces latency. |
| AMD CBS > CPU Common Options | `ACPI _CST C1 Declaration` | Disabled | Stops OS from using deep idle states. |
| AMD CBS > CPU Common Options | `Power Supply Idle Control` | Typical Current Idle | Avoids instability/black screens with some PSUs. |
| AMD CBS > DF Common Options | `DF Cstates` | Disabled | Further disables deep idle states in memory subsystem. |
| AMD CBS > SMU Common Options | `ECO Mode` | Disabled | Prevents CPU power-down throttling. |
| AMD CBS > FCH Common Options | `FCH Spread Spectrum` | Disabled | Avoids clock signal modulation; improves overclocking stability. |

---

## 🧠 Memory / DRAM
| Location | Setting | Value | Explanation |
|---------|---------|-------|-------------|
| OC Tweaker | `DRAM Profile Setting` | EXPO/XMP Profile | Enables rated memory speed & timings. |
| OC Tweaker | `DRAM Performance Mode` | Aggressive | Boosts memory performance, test for stability. |
| OC Tweaker | `Memory Context Restore` | Disabled | Prevents memory training resume; helps with stability on cold boot. |
| OC Tweaker | `Power Down Mode` | Disabled | Keeps memory powered fully active; improves responsiveness. |

---

## 🔒 Security & Encryption
| Location | Setting | Value | Explanation |
|---------|---------|-------|-------------|
| AMD CBS > AMD Common Platform Module | `Trusted Platform Module` | Disabled | Not needed unless using BitLocker or Windows 11. |
| AMD CBS > AMD Common Platform Module | `Pluton Security Processor` | Disabled | Used for Windows 11 security; disables background tasks. |
| Advanced > CPU Configuration | `Security Device Support` | Disabled | Blanket setting for TPM/Pluton etc. |
| AMD CBS > AMD Common Platform Module | `TSME` | Disabled | Transparent memory encryption, not needed. |
| AMD CBS > AMD Common Platform Module | `SMEE` | Disabled | Secure memory encryption, reduces performance. |
| Boot | `Secure Boot` | Disabled | Only required by certain anti-cheat/OS setups. Not needed on Win10. |

---

## 🔌 USB / Onboard I/O
| Location | Setting | Value | Explanation |
|---------|---------|-------|-------------|
| Advanced > USB Configuration | `XHCI Hand-off` | Disabled | For compatibility with older OSes only. |
| Advanced > USB Configuration | `Legacy USB Support` | Disabled | Allows USB in DOS; not needed for modern installs. |
| Advanced > USB Configuration | `USB Mass Storage Driver Support` | Disabled | Disables internal BIOS USB drivers for storage. |
| Advanced > ACPI Configuration | `USB Power Delivery in S5` | ⚠️ Optional | Enable if you want to charge devices while PC is off. |

---

## 🌐 Connectivity
| Location | Setting | Value | Explanation |
|---------|---------|-------|-------------|
| Advanced > Onboard Devices | `Bluetooth` | Disabled | Disables Bluetooth adapter. |
| Advanced > Onboard Devices | `Wi-Fi` | Disabled | Disables wireless LAN. |
| Advanced > Onboard Devices | `WAN Radio` | Disabled | Disables Wi-Fi radio transmit entirely. |
| Advanced > Onboard Devices | `Thunderbolt Support` | Disabled | Disable unless using Thunderbolt dock/peripherals. |
| Advanced > Onboard Devices | `HDMI 2.0 Support` | Disabled | Disable if using a discrete GPU (dGPU). |

---

## 🎮 PCIe / GPU / OC
| Location | Setting | Value | Explanation |
|---------|---------|-------|-------------|
| AMD CBS > NBIO Common Options | `PCIe ARI Support` | Auto | Auto-detects ARI (multi-function GPU support). |
| AMD CBS > NBIO Common Options | `PCIe ARI Enumeration` | Auto | Leave on Auto unless troubleshooting GPU passthrough. |
| AMD CBS > NBIO > GFX Configuration | `iGPU Configuration` | Disabled | Disables onboard graphics. |
| AMD CBS > Common Options | `Base Clock Control Mode` | CPU Clock Overclocking | Needed if BCLK tweaking. Leave default otherwise. |
| AMD CBS > Common Options | `PCIE/CPU Spread Spectrum` | Disabled | Disables clock modulation on PCIe/CPU buses. |
| AMD CBS > Common Options | `Re-Size BAR Support` | Enabled | Enables GPU access to more VRAM — performance boost in modern games. |
| AMD CBS > Common Options | `SoC/Uncore OC Mode` | Enabled | Needed for high memory OC and FCLK tuning. |

---

## 🚀 Boot
| Location | Setting | Value | Explanation |
|---------|---------|-------|-------------|
| Boot | `Fast Boot` | Disabled | Disables Windows quick boot — more stable POST. |
| Boot | `CSM` | Disabled | Enables UEFI mode for Re-Size BAR & faster boot. |
| Boot | `Setup Prompt Timeout` | 1 | Reduces boot delay; shows BIOS prompt briefly. |
| Boot | `Full Screen Logo` | Disabled | Cosmetic; disables splash screen during boot. |

---

## 💡 Cosmetic / Misc
| Location | Setting | Value | Explanation |
|---------|---------|-------|-------------|
| Tool > RGB LED | `LED Mode` | Disabled / Off | Disables RGB lighting. |
| Advanced > Onboard Devices | `Onboard Debug Port LED` | Enabled | Shows boot/post codes — helpful for troubleshooting. |

---

## 📌 Notes
- Most settings here aim to improve performance or eliminate latency sources.
- **No settings here are required for Windows 10 to function** unless you're doing memory OC or virtualization.
- If you’re NOT doing memory OC, leave `SoC/Uncore OC Mode` on Auto.
- Always test memory with `MemTest86+` after enabling EXPO/XMP.
- Save BIOS profiles before major changes!

---

## ✅ Quick Profile Summary (for printing or checklists)
