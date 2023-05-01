## Hardware

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
## Software

| Component | Model  |
| --------- | ------ |
| OpenCore  | 0.9.1  |
| macOS     | 12.6.5 |
| BIOS      | 1224   |

## Notes
Generate your own serial using GenSMBIOS for MacPro7,1 and add it to config.plist before
macOS has a 15 port limit so I've disabled USB 2.0 ports on the rear IO. Inspect [USBMap.kext](https://github.com/ryanilano/hackintosh-asus-b650ef-amd/blob/master/EFI/OC/Kexts/USBMap.kext/Contents/Info.plist) for labels and notes  
Thank you to everyone at [AMD-OSX](https://amd-osx.com) for being so helpful!