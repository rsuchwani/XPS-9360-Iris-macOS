# 9360-macOS (now with Big Sur!)
macOS Big Sur (11.0) for the Dell XPS 9360 Iris (7560u)

Big thanks to @the-darkvoid and @hoanX

# Specs
|    CPU   |   GPU    |  RAM  | STORAGE |    DISPLAY    |
|:--------:|:--------:|:-----:|:-------:|:-------------:|
| i7-7560u | Iris 640 | 16 GB |  512 GB |   3200x1800   |

# Summary
| Working                          | Not Working                   | Not Sure                    |
|----------------------------------|-------------------------------|-----------------------------|
| USB A, C, Sleep, Graphics        | Fingerpint                    | Thunderbolt 3 Functionality |
| Audio*                           |                       |                             |
| Touch                            |                               |                             |
| USB-C to Displayport             |                               |                             |
| Wireless/Bluetooth (DW1560) |             |                |

\*Install @the-darkvoid's combojack for better headphone quality & support

The provided wifi card is not compatible with macOS, so I would recommend the DW1560

# BIOS Configuration
- Disable VTD
- Disable "Enable Legacy Boot"
- Change from RAID to AHCI
- Make boot mode UEFI
- Disable Fingerprint + SD Card reader

# Installation
Copy the folders to your EFI, and things should work for the most part. You may have to set ``ScanPolicy`` to 0 to boot to installer

# Troubleshooting
Some issues may occur due to hardware differences
- If you have a PM981 drive, you are unlucky and your installer will not install. You may have to wait for a future NVMEFix release, or buy a new SSD
- Make sure you are using a 7560u - the GPU is different from the 8550u and 7500u, which will cause compatability issues
- To improve CPU PM, try generating CPUFriend kexts with one-key-cpufriend
- If your opencore is freezing, did you configure the BIOS as said before (disabling enable legacy boot fixes this for some)?

## Power Management
- Even though you may or may not have the same CPU, their configuration/profiles may be different, so generate new CPUFriend kexts for better PM.
- Also, please note that the newer 2.x releases for AppleALC for some reason cause extreme power draw on my machines, leading to non-stop high core clock speeds (always stays @ 3.7 GHz), so stick with the one provided in this repo
- I've found that using HWPEnabler.kext has improved my battery life by a hour or two (now 8-10 hours of normal usage)

## Coil Whine
Yuck, we all hate coil whine. Some fixes are:
- Use voltageshift to disable turbo mode (stopped a lot of whining for me)
- Install combojack from @the-darkvoid (don't know why, but this also remove a lot of whining)
- Undervolt in voltageshift (I use -100mv CPU, -40mv GPU -40 Cache, but it may differ for different machines)
- HWPEnable - Letting the BIOS handle PM rather then OS X seems to reduce a TON of the coil whine

# Credits
I did very little work, mostly updating kexts and tinkering with configs for trackpad (now no annoying typing delay)
Credits go to @the-darkvoid, @hoanx for their fantastic configurations
