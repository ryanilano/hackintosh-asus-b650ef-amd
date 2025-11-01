## The Intro and Bittersweet End?

Last month Apple announced that Tahoe would be the last version of macOS to support Intel processors. Other than upgrading this repo from Ventura to Tahoe I don't expect to see any future updates to the repo. In late 2025 my advice is don't go the hackintosh route unless you've already got the equipment or you really like to tinker.

I started building hackintoshes around 2009/2010 because I simply didn't have enough money to get the performance and speed I needed. Getting macOS to run on software it wasn't designed for is difficult but it works great if you put the time into it but... times have changed. I picked up the Mac Mini M4 Pro which runs as fast if not faster than the beast of a machine below. I also picked up the cheapest M4 MacBook Air and even with my insane requirements I have zero complaints with either system.

### Hardware

| Component        | Model                             |
| ---------------- | --------------------------------- |
| Motherboard      | Asus ROG Strix B650E-F            |
| CPU              | AMD Ryzen 9 7900X                 |
| Memory           | G.Skill Flare X5 32GB 6000MHz     |
| GPU              | Sapphire Nitro+ Radeon RX 6950 XT |
| WLAN & Bluetooth | Fenvi T919                        |
| Chassis          | Fractal North                     |
| Storage NVMe     | SK hynix Platinum P41 2TB         |
| Storage NVMe     | Inland Performance Plus 2TB       |
| Storage NVMe     | Crucial P3 Plus 2TB               |
| Storage SSD      | Samsung 870 EVO 1TB               |
| Storage NVMe     | Samsung 860 EVO 1TB               |

### Software

| Software | Version |
| -------- | ------- |
| OpenCore | 1.0.2   |
| macOS    | 13.7.1  |
| BIOS     | 2613    |

## Updates and Notes

- I'm staying on Ventura because i didn't want to deal with the OCLP workarounds needed for wifi... broadcom / fenvi or bust baby!
- **This config is tested and works on BIOS v1654.** Future BIOS updates (like the 9000 series support) may cause the boot sequence to hang. Shoutouts to Lorys89 for the fix: [DSDT fix](https://macos86.it/topic/6542-bug-fix-for-am5-new-firmware-motherboards-dsdt-fix/)

## Before you Copy Paste everything...

Generate your own serial using GenSMBIOS for MacPro7,1 and add it to config.plist before connecting to iCloud. Adjust the GPU and CPU if you have a different setup. I dualboot to Windows 10 on a different drive. If your time is always off check out [Fix Windows and macOS Showing Different Times When Dual Booting](https://www.applegazette.com/mac/fix-windows-and-macos-showing-different-times-dual-booting/).

### Performance

I'm running Eco Mode 105W TDP which gives me 98% of the stock performance while generating much less heat while using less electricity. I'm also running Curve Optimizer with -25 on all cores. Run Ryzen Master in Windows to figure out the correct curves for your specific CPU.

![Geekbench 6.01 Benchmark - Single-Core: 2594, Multi-Core: 16942](https://raw.githubusercontent.com/ryanilano/hackintosh-asus-b650ef-amd/master/benchmarks/benchmark-2023-0822-geekbench6.png "Geekbench 6.01 Benchmark")

## Check your Bios!

Upgrading to Bios 1807 throws a bunch of errors. The issue seems to be related to ACPI/SSDT/DSDT errors that the new microcode for BIOS for the 9000 series may have borked. Reverting back to 1654 immediately fixed boot issues. I'll update when I have more time!

## USB Map

Edhawk was kind enough to point out Intel systems typically only have one USB controller while its not unusual for AMD systems to have 2-3, which means AMD users can sometimes get 30-45 ports in since the limit is 15 ports per controller. ~~macOS has a 15 port limit so I've disabled USB 2.0 ports on the rear IO~~

The USB mapping works, is labeled, and was made to match my Fractal North. Inspect [USBMap.kext](https://github.com/ryanilano/hackintosh-asus-b650ef-amd/blob/master/EFI/OC/Kexts/USBMap.kext/Contents/Info.plist) for labels and notes.

### Known Issues

- Forget about Docker or virtualization on AMD Hackintoshes
- If you're stuck in a boot loop between OpenCore running and macOS login screen try to reset the NVRAM and reboot. The option to reset NVRAM is available by hiting the spacebar when the bootloader presents you with the option to choose which drive/OS to run (ie: Windows SSD1 or macOS SSD2)

## Shout Outs!

Thank you to everyone at [AMD-OSX](https://amd-osx.com) for being so helpful!
