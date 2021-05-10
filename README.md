# Hackintosh-Thinkpad-L14-Gen-1

Attempt at running macOS Big Sur on a Thinkpad L14 Gen 1 (Intel). Specs are as follows:

| Opencore |  macOS |
| ---------| ------ |
| 0.6.9    | 11.2.2 |


| Category    | Component                                            | Note                                                         |
| ----------- | ---------------------------------------------------- | ------------------------------------------------------------ |
| Type        | 20U1, 20U2                                           |                                                              |
| CPU         | Intel Core i5-10210U                                 |                                                              |
| GPU         | Intel UHD 630                                        |                                                              |
| SSD         | Kingston A2000 512GB                                 | Replaced default 256GB SSD with a larger one                 |
| Screen      | 14" FHD 1920x1080                                    | My model has no touch or pen input                           |
| Memory      | 16GB / 2666MHz DDR4                                  |                                                              |
| Battery     | Integrated Li-Polymer 43Wh                           | Single battery                                               |
| Camera      | 720p                                                 |                                                              |
| Wifi & BT   | Intel AX200                                          |                                                              |
| Input       | PS2 Keyboard & SMBUS Synaptics TrackPad              | Not all media keys working                                   |
| Audio       | ALC257                                               |                                                              |
| SD Card     | O2 Micro (1217:8621)                                 |                                                              |
| UEFI Chip   | Winbond 25Q256JVEQ + (EC?) Winbond 25Q80DVSIG        | Useful if someone wants to disable CFG-Lock                  |
| Fingerprint | Goodix Fingerprint Sensor                            | No driver exists for this model neither in macOS nor Linux   |

## Status

<summary><strong>What's working ✅</strong></summary>

- [x] Battery percentage
- [x] Bluetooth - Intel AX200 `Works flawlessly with IntelBluetooth`.
- [x] Wifi - Intel AX200  `Using itlwm + Heliport. Not as native as Airportitlwm, but much more stable.`
- [x] CPU power management
- [x] GPU UHD hardware acceleration / performance 
- [x] iMessage, FaceTime, App Store, iTunes Store. `Generate your own SMBIOS`
- [x] Keyboard `Not all media keys work. Volume buttons do.`
- [x]  Audio -`"alcid=86"`
- [x] Microphone
- [x] Sleep/Wake `Sleep light gets stuck at breathing mode after waking up. Need SSDT Fix for this.`
- [x] TrackPoint  `Works perfectly. Just like on Windows or Linux.`
- [x] USB Ports `USB map created.`
- [x] Webcam
- [x] TouchPad `Works using a debug version of VoodooRMI with palm rejection disabled. Needs fixing.`

<summary><strong>What's NOT working</strong></summary>

- Brightness keys and special keys (Brightness can be changed through settings)
- Sidecar or Handoff
- HDMI (fix coming soon)
- Micro SD Card Reader
- Fingerprint Reader

<details>
<summary><strong>ACPI Files</strong></summary>
<br>

| Component                   |
| --------------------------- |
| SSDT-AWAC.aml               |
| SSDT-BAT.aml                |
| SSDT-EC-USBX-LAPTOP.aml     |
| SSDT-GPRW.aml               |
| SSDT-HPET.aml               |
| SSDT-Keyboard.aml           |
| SSDT-OCBAT1-lenovoPRO13.aml |
| SSDT-PLUG-DRTNIA.aml        |
| SSDT-PNLF-CFL.aml           |
| SSDT-RHUB.aml               |
| SSDT-Thinkpad_Clickpad.aml  |
| SSDT-XOSI                   |

</details>

<details>
<summary><strong>Kernel extensions</strong></summary>
<br>

| Kext                   | Version |
| :--------------------- | ------- |
| AppleALC               | 1.5.9   |
| CPUFriend              | 1.2.3   |
| IntelBluetoothFirmware | 1.1.2   |
| IntelBluetoothInjector | 1.1.2   |
| IntelMausi             | 1.0.5   |
| itlwm                  | 1.3.0   |
| Lilu                   | 1.5.2   |
| NVMeFix                | 1.0.6   |
| SMCBatteryManager      | 1.2.2   |
| SMCProcessor           | 1.2.2   |
| SMCSuperIO             | 1.2.2   |
| USBMap                 | N/A     |
| VirtualSMC             | 1.2.2   |
| VoodooPS2Controller    | 2.2.3   |
| VoodooRMI              | 1.3.2   |
| VoodooSMBUS            | 2.2     |
| WhateverGreen          | 1.4.9   |

</details>


<summary><strong>Notes</strong></summary>

- The SSDT patch related to the keyboard comes from an E14, so it needs to be replaced with a custom patch to make special keys work.
- Sleep and Wake needs extended testing. From closing the lid to actual sleeping it takes around 45 seconds. I had no problems with waking from sleep or hibernation for now
- A Broadcom Wi-Fi card is recommended.
- Battery life isn't quite up to spec. I suspect it is because of the CFG Lock, which cannot be disabled without BIOS modding (requires hardware). Also, the DSDT patch for the battery comes from a Lenovo L13.
- I haven't tested USB-C adapters or displays yet.
- DSDT Patches need cleanup.
- Touchpad is flaky, sometimes the Trackpoint stops working, or high palm rejection kicks in. Usually, sleeping and waking up fixes this.

# Initial setup
I used AniKulkarn's repo (https://github.com/AniKulkarn/Hackintosh-ThinkPad-E14) as its specs are quite similar, then appended my changes to kexts and DSDT Patches.
