# linux-hid-magicmouse
Add support to change click pressure and haptic feedback for magic trackpad 2

## DKMS

Install with:

    sudo ./scripts/install.sh

Remove with:

    sudo ./scripts/remove.sh


## Configuration

By default, it works the same as before. To change click pressure, it need to get into host click mode:

    sudo modprobe -r hid_magicmouse
    sudo modprobe hid-magicmouse host_click=on button_down_param=0x503f0606 button_up_param=0x35110404

The first byte means the pressure to trigger the button. And three latest bytes means how the trackpad vibrates. Set latest two bytes 0x00 to get silent mode

By default when `host_click=on`, button_down_param=0x40170606 button_up_param=0x26140000, which is the same as medium pressure on macOS

## Thanks

* https://github.com/mwyborski/Linux-Magic-Trackpad-2-Driver
* https://github.com/ponyfleisch/hid-magictrackpad2
* https://github.com/dos1/Linux-Magic-Trackpad-2-Driver
* My friend helps to capture packets on mac
