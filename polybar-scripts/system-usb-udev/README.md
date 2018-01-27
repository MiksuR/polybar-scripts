# Script: system-usb-mount

A small script that shows your mounted and not mounted removable devices. This is an extended version of [system-usb-udev](../system-usb-udev).

Click left to mount all removable devices. Click right to unmount the devices. The removable devices are then turned off with `udisksctl power-off`.

The mount option has a feature: You can also start a file manager and open the device when you mount it. Look at the example in the code: `terminal -e "bash -lc 'filemanager $mountpoint'" &`

This script is able to display device changes in real time. For this udev is being used.

![system-usb-mount](screenshots/1.png)

![system-usb-mount](screenshots/2.png)


## Dependencies

* `jq`
* `udisks2`

Copy `95-usb.rules` to `/etc/udev/rules.d/95-usb.rules`. Make sure that the paths in the file have been modified properly.

Also change the file path in line `#23`.


## Module

```ini
[module/system-usb-mount]
type = custom/script
exec = ~/polybar-scripts/system-usb-udev.sh
tail = true
click-left = ~/polybar-scripts/system-usb-udev.sh --mount
click-right = ~/polybar-scripts/system-usb-udev.sh --unmount
```