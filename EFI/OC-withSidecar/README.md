
# Unstable EFI with (theoretically) Full Sidecar Support

In short, there are three things to do in order to make Sidecar working on such machine equipped with dGPUs only:

1. Set your SMBIOS to either **iMac19,1** or **iMac18,3**
2. add `shiki-id=Mac-7BA5B2D9E42DDD94 shikigva=40` into your boot-args
3. Replace existing `WhateverGreen.kext` with the one I provided

Re-login iCloud account then reboot, you should be able to get full Sidecar functionality working.

Remember, you are supposed to generate **YOUR OWN SMBIOS INFORMATION** and select the correct `USBPorts.kext` corresponding to your SMBIOS choice.

I could have tested whether this approach indeed work or not, but my dGPU, `HD7700` only has `1GB` vRAM, which make it impossible to drive an extra screen aside from the main `4K UHD` one.

![20211026120157](https://cdn.jsdelivr.net/gh/KirisameR/KirisameR.github.io/img/blogpost_images/20211026120157.png)

When you set SMBIOS to `iMac19,1` or `iMac18,3`, CPU power management will behave oddly: you will get drastically performance DECREASE, and the processor will be locked at its base freq until it revive from hibernation. Current there's no way of fixing it, therefore I strongly suggest you to stick with `MacPro7,1`.

Reference:<br>

[!Chinese! Sidecar for AMD Processors without iGPU](https://www.bilibili.com/video/av714387450/)

[!Chinese! Another way of enabling Sidecar on Platforms without iGPU](http://bugprogrammer.me/2019/11/24/fix-sidecar-without-igpu.html)