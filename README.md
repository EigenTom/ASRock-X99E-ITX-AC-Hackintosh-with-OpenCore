# ASRock-X99E-ITX/AC-Hackintosh-with-OpenCore

[![macOS](https://img.shields.io/badge/macOS-Catalina-yellow.svg)](https://www.apple.com/macos/catalina/)
[![version](https://img.shields.io/badge/10.15.6-yellow)](https://support.apple.com/en-us/HT210642)
[![BIOS](https://img.shields.io/badge/BIOS-3.60-blue)]()
[![MODEL](https://img.shields.io/badge/X99E-ITX_A/C-blue)](http://www.asrock.com/MB/Intel/X99E-ITXac)
[![OpenCore](https://img.shields.io/badge/OpenCore-0.6.6-green)](https://github.com/acidanthera/OpenCorePkg)
[![LICENSE](https://img.shields.io/badge/license-MIT-green)]()

OpenCore 0.6.6 Configurations for ASRock X99E-ITX/AC MotherBoard macOS Catalina Hackintosh


![](./readme.png)

<center>

 [The result of this patch (Without E5 V3 Boost Patch):](https://browser.geekbench.com/v5/cpu/10608364)

GeekBench5 Score: Single `847`, Multi-Core `6439`. 

`10/14` Cores, Discarded E5 V3 Boost Patch, Multiplier `Auto`, Undervolt `0.100v`

</center>

<br>

> ## SUMMARY:

**`This Patch is stable on macOS 10.15.6, with most of the functions run smoothly. `**


| Fully functional | Non-functional | Semi-functional |
| ---------------- | -------------- | ------------------------------------------------------ |
| Native Power Management & Hibernation | - | - |
| Wi-Fi, Bluetooth, Apple Continuity Functions, iCloud Suite(Generate your own SMBIOS information) <br> **!!A compatible network card is needed!!**               |  SideCar (Semi functional, see "misc")   | -  |
| USB-A 3.1/3.0/2.0 Ports, Ethernet, On-board Audio, SATA Drives               | -  | - | - |

<br>

>## Update History
- Ver 0.0.1 Initial Release, 26/10/21

<br>

> ## SPECIFICATIONS

My X99 Workstation configurations:

| Processor Number                                                                                                                   | # of Cores | # of Threads | Base Frequency | Max Turbo Frequency | Cache | Memory Types | Graphics      |
| :--------------------------------------------------------------------------------------------------------------------------------- | :--------- | :----------- | :------------- | :------------------ | :---- | :----------- | :------------ |
| [Xeon E5 2695 v3 ES (QFQG)](https://ark.intel.com/content/www/us/en/ark/products/81057/intel-xeon-processor-e5-2695-v3-35m-cache-2-30-ghz.html) | `14`          | `28`            | `2.3 GHz`        | `3.5 GHz`             | `35 MB`  | `DDR4-2133`  | `XFX HD7770 Black 2GB` |

Note: Older dGPUs like HD7xxx Series may needs vBIOS with UEFI Support to work with OpenCore. 

**Peripherals:**

- Wireless Card: `BCM943602CS` (3 Antennas)<br>
- Ethernet: On Board Intel Ethernet Controllers
- SSD: WD Black `SN720` NVMe SSD 
- Memory: 2x `Samsung 16G M393A2G40DB0-CPB(RDIMM) (ECC)` 32G in total, dual channel

<br>

>## BIOS Settings Modifications
```
+ Advanced
- CPU Configuration
* Intel Virtualization Technology: ENABLED
* CPU C3 State Support: ENANBLED
* CPU C6 State Support: ENANBED
- Chipset Configuration
* VT-d: ENABLED
* Above 4G Decoding: ENABLED
* Above 4G Decoding Patch: ENABLED

```


<br>

>## PROCEDURES

1. Download `.dmg` installation file of macOS 10.15.6 Catalina. 

2. Use [Balena Etcher](https://www.balena.io/etcher/) to flash the `.dmg` file into your USB disk. 


3. Mount the EFI partition of the USB disk, replace the entire `EFI` Folder with `EFI-Install`. 

4. Enter BIOS, and change BIOS settings according to the instructions above.

5. Reboot and install macOS 10.15.6 Catalina. 

6. Put `/EFI-Opencore/OC` to `"Your SSD's EFI Partition"/EFI`. 

7. Inject your SMBIOS info, do further implementations to the hardware which is different than mine. 


<br>

>## Contact Me

- Luyi1720839132@Gmail.com
- https://t.me/Kirisame_Marisa

<br>

>## Misc

After some investigations, I found a way to use iPad as your secondary display by performing some "dark magic":

Normally, hackintosh without iGPU cannot output image through sidecar, that's why even if you can connect to the iPad, you will 100% get black screen. The basic idea is to combine sidecar and a tool called [Deskscreen](https://deskreen.com). <br>We will use sidecar to mock up a secondary display and let the graphics card to output the display signal, and use Deskscreen to stream it to the iPad. 

Although you can stream your desktop to the iPad theoretically, the quality is limited by the Wi-Fi bandwith and network condition. Usually there is noticeable lagging and low resolution. To solve this issue, we connect the iPad to the desktop, to let them establish a direct network connection firmly. 

To use your iPad as a secondary display on hackintoshes based on X99 platform: 

- Make sure you patched SMBIOS and Wi-Fi card correctly and you are able to connect your iPad through sidecar
- Download [Deskscreen](https://deskreen.com) and install
- Link your iPad to the desktop with charging cable
- Open Deskscreen, stream the sidecar screen to the device



<br>

>## Additional used resources: 

- [dortania's Hackintosh guides](https://github.com/dortania)
- [dortania/ Getting Started with ACPI](https://dortania.github.io/Getting-Started-With-ACPI/)
- [dortania/ opencore `desktop` guide](https://dortania.github.io/OpenCore-Desktop-Guide/)
- [dortania/ opencore `multiboot`](https://github.com/dortania/OpenCore-Multiboot)
- [dortania/ `USB map` guide](https://github.com/dortania/USB-Map-Guide)
- [Daliansky's `Hackintool tutorial`](https://translate.google.com/translate?js=n&sl=auto&tl=en&u=https://blog.daliansky.net/Intel-FB-Patcher-tutorial-and-insertion-pose.html).
- [OpenCore Sanity Checker](opencore.slowgeek.com)
- [Basic UEFI Patch Reference](https://www.tonymacx86.com/threads/x99-catalina-pci-cards-not-working.309236/)
- [`AppleUSBXHCI` Error Fix](https://www.tonymacx86.com/threads/how-to-extend-the-imac-pro-to-x99-successful-build-extended-guide.227001/page-86)
- [X99 Platform Hackintosh Guide (!Chinese)](https://www.chiphell.com/thread-2174588-1-1.html)
- [AMD dGPU vBIOS Patch Guide](http://forum.netkas.org/index.php/topic,5619.0.html)
- [`HD7xxx` UEFI vBIOS Patch Guide (!Chinese)](https://bbs.nga.cn/read.php?tid=18588213&rand=628)
- [AMD dGPU vBIOS Flash Guide (!Chinese)](https://www.chiphell.com/thread-347172-1-1.html)
- [Hibernation Fix (1)](https://pikeralpha.wordpress.com/2017/01/12/debugging-sleep-issues/)
- [Hibernation Fix (2)](https://www.tonymacx86.com/threads/how-to-extend-the-imac-pro-to-x99-successful-build-extended-guide.227001/)
- [XCPM Fix for X99](https://www.tonymacx86.com/threads/x99-macos-catalina-10-15-2-kernel-patches.288451/)
- [Deskscreen](https://github.com/pavlobu/deskreen)
