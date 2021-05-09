# Hackintosh-Thinkpad-L14-Gen-1

Attempt at running macOS Big Sur (11.2.2) on a Thinkpad L14 Gen 1 (Intel). Specs are as follows:


| Category  | Component                                            | Note                                                         |
| --------- | ---------------------------------------------------- | ------------------------------------------------------------ |
| Type      | 20U1, 20U2                                           |                                                              |
| CPU       | Intel Core i5-10210U                                 |                                                              |
| GPU       | Intel UHD                                            |                                                              |
| SSD       | Kingston A2000 512GB                                 | Replaced default 256GB SSD with a larger one                 |
| Screen    | 14" FHD 1920x1080                                    | My model has no touch or pen input                           |
| Memory    | 16GB / 2666MHz DDR4                                  |                                                              |
| Battery   | Integrated Li-Polymer 43Wh                           | Single battery                                               |
| Camera    | 720p                                                 |                                                              |
| Wifi & BT | Intel AX200                                          | Using AirportItlwm for Wi-Fi, planning on getting a Broadcom |
| Input     | PS2 Keyboard & SMBUS Synaptics TrackPad              | Not all media keys working                                   |

## Status

<summary><strong>What's working ✅</strong></summary>

- [x] Battery percentage
- [x] Bluetooth - Intel AX200
- [x] Wifi - Intel AX200
- [x] CPU power management
- [x] GPU UHD hardware acceleration / performance 
- [x] iMessage, FaceTime, App Store, iTunes Store. `Generate your own SMBIOS`
- [x] Keyboard `Not all media keys are workinhg. Brightness and Volume buttons do.`
- [x]  Audio -`"alcid=11" - or see setup above`
- [x] Microphone
- [x] Sleep/Wake `Sleep light gets stuck at breathing mode after waking up. Need SSDT Fix for this.`
- [x] TrackPoint  `Works perfectly. Just like on Windows or Linux.`
- [x] USB Ports `USB map created.`
- [x] Webcam
- [ ] TouchPad `Works but is very jumpy, especially when you slide your finger too fast.`
- [x] HDMI

<summary><strong>What's NOT working</strong></summary>

- Some media keys

# Initial setup
I used seven-of-eleven's very helpful guide for a Lenovo L13 Yoga, since specs are quite similar. You can check out his repo at https://github.com/seven-of-eleven/Lenovo-ThinkPad-L13-Yoga-Hackintosh

I encountered many problems that kept my device from working fine:
- System would reboot instantly (had to remove YogaSMC to get it to start properly)
- System would reboot before sleeping
- Touchpad gestures would work erratically (L14 uses SMBUS to interface with the touchpad, unlike L13's I2C)
- Battery wouldn't show up
- Power management broken
- Wi-Fi wouldn't work after sleep
