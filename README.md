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

| Component | Model  	|
| --------- | --------- |
| OpenCore  | 0.9.6		|
| macOS     | 13.6.1	|
| BIOS      | 1654   	|

## Setup Notes
Generate your own serial using GenSMBIOS for MacPro7,1 and add it to config.plist before connecting to iCloud. Adjust the GPU and CPU if you have a different setup. I dualboot to Windows 10 on a different drive. If your time is always off check out [Fix Windows and macOS Showing Different Times When Dual Booting](https://www.applegazette.com/mac/fix-windows-and-macos-showing-different-times-dual-booting/). 
### Performance
I'm running Eco Mode 105W TDP which gives me 98% of the stock performance while generating much less heat while using less electricity. I'm also running Curve Optimizer with -25 on all cores. Run Ryzen Master in Windows to figure out the correct curves for your specific CPU.

![Geekbench 6.01 Benchmark - Single-Core: 2594, Multi-Core: 16942](https://raw.githubusercontent.com/ryanilano/hackintosh-asus-b650ef-amd/master/benchmarks/benchmark-2023-0822-geekbench6.png "Geekbench 6.01 Benchmark")

### Known Issues
Virtualization is a pain to get working in Ventura. You can [run Docker on AMD OpenCore using `docker-machine` and an older version of VirtualBox](https://gist.github.com/slykar/e92732be9bf81a71e08068245656d70e?permalink_comment_id=4105556#gistcomment-4105556) but I haven't personally gotten it to work. If you can help me please reach out!

## To Do
Upgrading to Bios 1807 throws a bunch of errors. The issue seems to be related to ACPI/SSDT/DSDT errors that the new BIOS may have introduced. Reverting back to 1654 immediately fixed boot issues. I'll look into this later

Edhawk was kind enough to point out a USB issue and explain how Apple handles USB limits per controller. Intel systems typically have one USB controller while its not unusual for AMD systems to have 2-3.

> You should be aware that the 15 port USB limit is not the same when using an Intel or AMD build. The most important thing to remember is that the 15 port limit is per controller. This makes a huge difference on an AMD system.

> On an AMD system the motherboard may have two or three USB controllers (XHC0, XHC1, PTXH, PXSX etc.), where each controller has a 15 port limit ... So you could have 30+ USB ports active within a single system where each USB Controller activates 15 ports or less.

> I have seen AMD motherboards with the XHC0 controller activating 14 ports, the XHC1 controller activating 9 ports and the PTXH controller activating 9 ports, giving a total of 32 active USB ports, but none of the three USB controllers are activating more than 15 ports, so they all stay within the limit imposed by Apple for each USB Controller.

The USB mapping kext included in the repo DOES work but it could be better! I'll update that soon! ~~macOS has a 15 port limit so I've disabled USB 2.0 ports on the rear IO~~ Inspect [USBMap.kext](https://github.com/ryanilano/hackintosh-asus-b650ef-amd/blob/master/EFI/OC/Kexts/USBMap.kext/Contents/Info.plist) for labels and notes.

## Shout Outs!
Thank you to everyone at [AMD-OSX](https://amd-osx.com) for being so helpful!