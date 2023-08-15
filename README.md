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

| Component | Model  	|
| --------- | --------- |
| OpenCore  | 0.9.1		|
| macOS     | 13.4.1(c)	|
| BIOS      | 1636   	|

## Notes
Generate your own serial using GenSMBIOS for MacPro7,1 and add it to config.plist before connecting to iCloud

##Shout Outs!
Thank you to everyone at [AMD-OSX](https://amd-osx.com) for being so helpful!
## Known Issues
The USB mapping kext included in the repo works but could be better. I'll update that soon! ~~macOS has a 15 port limit so I've disabled USB 2.0 ports on the rear IO~~ Inspect [USBMap.kext](https://github.com/ryanilano/hackintosh-asus-b650ef-amd/blob/master/EFI/OC/Kexts/USBMap.kext/Contents/Info.plist) for labels and notes.

Edhawk over at AMD-OSX was kind enough to point out the issue and misunderstanding about how Apple handles USB. 

> You should be aware that the 15 port USB limit is not the same when using an Intel or AMD build. The most important thing to remember is that the 15 port limit is per controller. This makes a huge difference on an AMD system.

> On an AMD system the motherboard may have two or three USB controllers (XHC0, XHC1, PTXH, PXSX etc.), where each controller has a 15 port limit ... So you could have 30+ USB ports active within a single system where each USB Controller activates 15 ports or less.

> I have seen AMD motherboards with the XHC0 controller activating 14 ports, the XHC1 controller activating 9 ports and the PTXH controller activating 9 ports, giving a total of 32 active USB ports, but none of the three USB controllers are activating more than 15 ports, so they all stay within the limit imposed by Apple for each USB Controller.