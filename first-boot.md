# First boot, ID and specs

After device arrived, I've removed a battery and checked the inner label:

![PU10 Qtek 9000](img/pu10_002.png?raw=true "PU10 Qtek 9000")

Inner label shows model number PU10, "HTC Innovation" ("Innovation" is not the model name,
it's like "Nokia Connecting People") and IMEI with TAC 35519500, belonging to HTC,
corresponding to MDA pro,Dopod 900,Universal,XDA Exec models. Battery model is PU16A.

On the inner cover there is a hologram label with "Bitė" telco operator name (MCC + MNC: 246 02),
saying "Qtek bitė edition", which could potentially mean phone can be operator-locked.

And if you wonder - stylus is inside:

![PU10 Qtek 9000](img/pu10_005.png?raw=true "PU10 Qtek 9000")

There was a mini-USB port, charhing indicator went red when connected.
But device did not boot. Fast google search showed device can not operate
solely on charger and battery must be charged for any operation, even JTAG.
Battery was not completely dead and showed ~1V checked by the tester, and charging.
After less than half an hour of charging, it did try to boot, showing a boot screen:

![PU10 Qtek 9000](img/pu10_003.png?raw=true "PU10 Qtek 9000")

But then there was a caveat - a gap, when "dumb" charging stopped, but for a "smart"
charging OS needed to be booted, and there was not enough battery to boot the OS - 
I've seen Windows logo multiple times but it did not manage to boot.  After quite a fiew iterations
I've decided to charge the battery off the device with a random charger found in a box for 10 minutes:

![PU10 Qtek 9000](img/pu10_004.png?raw=true "PU10 Qtek 9000")

It did the trick, sistem booted and started charging the battery:

![PU10 Qtek 9000](img/pu10_006.png?raw=true "PU10 Qtek 9000")

System information screens from within the OS:

![PU10 Qtek 9000](img/pu10_007.png?raw=true "PU10 Qtek 9000")
![PU10 Qtek 9000](img/pu10_008.png?raw=true "PU10 Qtek 9000")
![PU10 Qtek 9000](img/pu10_009.png?raw=true "PU10 Qtek 9000")
![PU10 Qtek 9000](img/pu10_010.png?raw=true "PU10 Qtek 9000")

And finally - there is no power-off or reboot option. To power-off you need to remove the battery.
To reboot, you need to put stylus into "Reset" hole. You'll also need a stylus to put device into BootLoader
mode - press  Light (lightbulb button under volume control) + Power + Reset (the hole between earphpone USB,
pressed by stylus):

![PU10 Qtek 9000](img/pu10_011.png?raw=true "PU10 Qtek 9000")

BootLoader mode shows "Serial" atop of the screen  and "v2.01" at the bottom. Backlit is disabled, so,
difficult to make a picture.

Linux host, while device USB connected, in dmesg in normal mode shows:
```
[   49.576167] usb 1-8: new full-speed USB device number 4 using xhci_hcd
[   49.728263] usb 1-8: New USB device found, idVendor=0bb4, idProduct=0b01, bcdDevice= 0.00
[   49.728268] usb 1-8: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[   49.728270] usb 1-8: Product: PocketPC USB Sync
[   49.728272] usb 1-8: Manufacturer: MSFT
[   49.795898] rndis_host 1-8:1.0: RNDIS init failed, -11
[   49.796009] rndis_host: probe of 1-8:1.0 failed with error -11
[   50.076164] rndis_wlan 1-8:1.0: RNDIS init failed, -110
[   50.076284] rndis_wlan: probe of 1-8:1.0 failed with error -110
```

And in BootLoader mode:
```
[  159.715313] usb 1-8: new full-speed USB device number 5 using xhci_hcd
[  159.864663] usb 1-8: New USB device found, idVendor=045e, idProduct=00ce, bcdDevice= 0.00
[  159.864668] usb 1-8: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[  159.864670] usb 1-8: Product: PocketPC SmartPhone
[  159.864673] usb 1-8: Manufacturer: Intel.
[  159.881097] usbcore: registered new interface driver usbserial_generic
[  159.881103] usbserial: USB Serial support registered for generic
[  159.882679] usbcore: registered new interface driver ipaq
[  159.882685] usbserial: USB Serial support registered for PocketPC PDA
[  159.882707] ipaq 1-8:1.0: PocketPC PDA converter detected
[  159.883483] usb 1-8: PocketPC PDA converter now attached to ttyUSB0
```
