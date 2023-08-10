# DualSense Control [DualSenseCTL]
- _Latest version 0.4_

DualSense Control [DualSenseCTL] is a tool for controlling Sony PlayStation 5 DualSense controllers on Linux.

    Usage: dualsensectl [--option] [command] [ARGUMENT/S] ([command]) [PARAMETER/S]

    Options:
      -l --list                                                                                List available devices [xx:xx:xx:xx:xx:xx] (USB/Bluetooth)
      -d --device [DEVICE]                                                                     Specify which device to use [xx:xx:xx:xx:xx:xx] (USB/Bluetooth) and show help message
      -w --wait                                                                                Wait for shell command to complete (Monitor only)
      -h --help                                                                                Show this help message and exit
      -v --version                                                                             Show version and exit
    Commands:
      power-off                                                                                Turn off the controller (Bluetooth only)
      battery                                                                                  Get the controller battery level and charging/discharging information
      info                                                                                     Get the controller firmware information
      lightbar [STATE]                                                                         Enable [ON] or disable [OFF] lightbar
      lightbar [RED] [GREEN] [BLUE] [BRIGHTNESS]                                               Set lightbar color and brightness [0-255] [0-255] [0-255] [0-255]
      player-leds [NUMBER]                                                                     Set player LEDs [1-5] or disabled [0]
      microphone [STATE]                                                                       Enable [ON] or disable [OFF] microphone
      microphone-led [STATE]                                                                   Enable [ON] or disable [OFF] microphone orange LED
      speaker [STATE]                                                                          Toggle to '[INTERNAL] speaker', [HEADPHONE], [MONOHEADPHONE] or [BOTH] outputs
      volume [VOLUME]                                                                          Set audio volume [0-255] of internal speaker and headphone
      attenuation [RUMBLE] [TRIGGER]                                                           Set the attenuation [0-7] [0-7] of rumble/haptic motors and trigger vibration
      trigger [TRIGGER] off                                                                    Remove all trigger [LEFT], [RIGHT] or [BOTH] effects
      trigger [TRIGGER] feedback [POSITION] [STRENGTH]                                         Set trigger(s) [LEFT], [RIGHT] or [BOTH] 'feedback'/'resistance' starting at position with a defined strength
      trigger [TRIGGER] weapon [START] [STOP] [STRENGTH]                                       Emulate trigger(s) [LEFT], [RIGHT] or [BOTH] as weapon like 'gun trigger'
      trigger [TRIGGER] bow [START] [STOP] [STRENGTH] [SNAP_FORCE]                             Emulate trigger(s) [LEFT], [RIGHT] or [BOTH] as weapon like 'bow'
      trigger [TRIGGER] galloping [START] [STOP] [FIRST_FOOT] [SECOND_FOOT] [FREQUENCY]        Emulate trigger [LEFT], [RIGHT] or [BOTH] 'galloping'
      trigger [TRIGGER] machine [START] [STOP] [STRENGTH_A] [STRENGTH_B] [FREQUENCY] [PERIOD]  Switch trigger [LEFT], [RIGHT] or [BOTH] vibration between to strength at a specified period
      trigger [TRIGGER] vibration [POSITION] [AMPLITUDE] [FREQUENCY]                           Vibrates trigger [LEFT], [RIGHT] or [BOTH] motor arm around specified position
      trigger [TRIGGER] feedback-raw [STRENGTH(10)]                                            Set trigger [LEFT], [RIGHT] or [BOTH] 'feedback'/'resistance' starting using array of strength (Requires 10 parameters)
      trigger [TRIGGER] vibration-raw [AMPLITUDE(10)] [FREQUENCY]                              Vibrates trigger [LEFT], [RIGHT] or [BOTH] motor arm at position and strength specified by an array of amplitude (Requires 10 parameters)
      trigger [TRIGGER] mode [PARAMETERS(1-9)]                                                 Set the trigger [LEFT], [RIGHT] or [BOTH] mode with parameters [1-9]
      monitor [add 'command'] / [remove 'command']                                             Run Monitor shell [add/remove 'command'] on add/remove events


## Building & Installing from SOURCE (gcc/glibc):

`./`
`sudo make && sudo make install all`
## Uninstall from SOURCE:
`./`
`sudo make uninstall all`

## Download sources:
- Arch Linux - AUR: [dualsensectl] (https://aur.archlinux.org/packages/dualsensectl) -- Not Updated
- Arch Linux - AUR: [dualsensectl-git] (https://aur.archlinux.org/packages/dualsensectl-git/) -- GIT version
- Debian/Ubuntu - DEB: [dualsensectl] ---
- openSUSE - RPM: [dualsensectl] (https://build.opensuse.org/package/show/home:MartinVonReichenberg:hardware/dualsensectl)
- Fedora - RPM: [dualsensectl] (https://copr.fedorainfracloud.org/coprs/birkch/dualsensectl/)
- Mageia - RPM: ---
## Make Dependencies

### GENERIC (Gcc/PkgConf)
* gcc/musl | systemd-dev/systemd-devel

### Arch Linux
* gcc | dbus | systemd | systemd-libs

### Debian/Ubuntu
* gcc | dbus | libdbus-1-dev | libhidapi-dev | libudev-dev

### openSUSE
* gcc-devel | gcc-c++ | dbus-1-devel | libdbus-c++-devel | libhidapi-devel | libudev-devel

### Fedora
* gcc | gcc-c++ | dbus-devel | hidapi-devel | systemd-devel | systemd-udev

### Mageia
* gcc | gcc-c++ | lib64dbus-devel | lib64dbus-c++-devel | lib64hidapi-devel | lib64udev-devel

### KaOS
* gcc | dbus | systemd

## Dependencies

### GENERIC (Gcc/PkgConf)
* gcc/musl | dbus | hidapi/hidapi-hidraw | udev/libudev

### Arch Linux
* gcc | dbus | dbus-c++ | systemd-libs | hidapi | libudev0-shim

### Debian/Ubuntu
* gcc | dbus | libdbus-1-3 | libhidapi-hidraw0 | libudev0 | libudev1

### openSUSE
* gcc | gcc-c++ | dbus-1 | libhidapi-hidraw0 | libhidapi-libusb0 | udev | libudev1

### Fedora
* gcc | gcc-c++ | dbus | systemd | hidapi | libhid | libusb1 | systemd-udev

### Mageia
* gcc | gcc-c++ | lib64dbus1_3 | lib64hidapi0 | lib64udev1

### KaOS
* gcc-libs | dbus | systemd

## udev rules (Optional)
#### _No longer neccessary to set manually; Included in installation_ . . .

Also installed by Steam, so you may already have it configured. If not, create file `/etc/udev/rules.d/70-dualsensectl.rules`:

    # PS5 DualSense controller over USB hidraw
    KERNEL=="hidraw*", ATTRS{idVendor}=="054c", ATTRS{idProduct}=="0ce6", MODE="0660", TAG+="uaccess"

    # PS5 DualSense controller over bluetooth hidraw
    KERNEL=="hidraw*", KERNELS=="*054C:0CE6*", MODE="0660", TAG+="uaccess"
