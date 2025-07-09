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
