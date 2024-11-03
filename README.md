## Configuration
### Hardware

| Component        | Model                         			|
| ---------------- | --------------------------------------	|
| Motherboard      | Asus ROG Strix B650E-F        			|
| CPU              | AMD Ryzen 9 7900X             			|
| Memory           | G.Skill Flare X5 32GB 6000MHz 			|
| GPU              | Sapphire Nitro+ Radeon RX 6950 XT		|
| WLAN & Bluetooth | Fenvi T919 							|
| Chassis          | Fractal North							|
| Storage NVMe     | SK hynix Platinum P41 2TB				|
| Storage NVMe     | Inland Performance Plus 2TB			|
| Storage NVMe     | Crucial P3 Plus 2TB					|
| Storage SSD      | Samsung 870 EVO 1TB					|
| Storage NVMe     | Samsung 860 EVO 1TB					|
### Software

| Software  | Version  	|
| --------- | --------- |
| OpenCore  | 1.0.2		|
| macOS     | 13.7.1	|
| BIOS      | 2613   	|

## Updates and Notes
- I'm stayng on Ventura until wifi fixes for Broadcom and Intel wifi cards are clearer and less of a pain.
- **This config is tested and works on BIOS v1654.** Future BIOS updates (like the 9000 series support) may cause the boot sequence to hang. Shoutouts to Lorys89 for the fix: [DSDT fix](https://macos86.it/topic/6542-bug-fix-for-am5-new-firmware-motherboards-dsdt-fix/)
- Here's a current list of available BIOS [Asus B650E-F BIOS updates](https://rog.asus.com/motherboards/rog-strix/rog-strix-b650e-f-gaming-wifi-model/helpdesk_bios/) 

## Before Copy Paste the entire repo...
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
Virtualization is a pain to get working on AMD hackintoshes. You can [run Docker on AMD OpenCore using `docker-machine` and an older version of VirtualBox](https://macos86.it/topic/6535-guidevirtualbox-on-sonoma-and-amd-hackintosh/) but I haven't personally gotten it to work. If you can help me please reach out!

## Shout Outs!
Thank you to everyone at [AMD-OSX](https://amd-osx.com) for being so helpful!