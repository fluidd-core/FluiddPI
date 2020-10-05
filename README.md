# fluiddpi
A pi image with Klipper, Moonraker and Fluidd pre-installed.

This repository contains the necessary code to generate the distribution from an existing Raspbian lite distro image.

## Where to download?
You can download the latest release [here](https://github.com/cadriel/FluiddPI/releases/latest).

Older releases can be found [here](https://github.com/cadriel/FluiddPI/releases).

## How to use?
1. Download the image as per above and install on an sdcard like you would any other Raspberry pi image.
2. Optionally, if you require WiFi, configure by editing the `fluiddpi-wpa-supplicant.txt` on the root of the sd card - whilst it is still connected to your computer.
3. Boot your Pi from the new sd card.
4. Log into your Pi via SSH (located at fluidd.local). Default username is `pi` and password is `raspberry`.
5. Best practice would have you;
    - `sudo apt-get update`
    - `sudo apt-get upgrade`
    - `sudo raspi-config`
        - Change your password
        - Define your timezone via 'Localization Options'
        - Optionally Change your hostname
6. Reboot.

Fluidd will be available at `http://fluidd.local` - and will present an error about a missing `printer.cfg` file.
You should now progress with standard klipper setup, upon which time Fluidd will begin working correctly.

## Compiling / Developing Quick Start
Regular users of FluiddPI should **not** need to follow any of these steps. This is
for those that wish to compile their own image and / or help in the development
of this project.

### Requirements
Recommended environment is Ubuntu or similar, with docker and docker-compose installed.

- bash
- git
- [docker](https://docs.docker.com/engine/install/ubuntu/)
- [docker-compose](https://docs.docker.com/compose/install/)
- [qemu-arm-static](http://packages.debian.org/sid/qemu-user-static)
- QEMU for emulation
- around ~5gb free space

```bash
# Packages for Ubuntu 18.04/20.04
sudo apt-get install gawk make build-essential util-linux \
qemu-user-static qemu-system-arm \
git p7zip-full python3 curl
```

To build;
```bash
git clone https://github.com/cadriel/FluiddPI.git
cd fluiddpi
make build
```

To test;
```bash
# To exit emulation - Ctrl-a x
./run.sh
```

Other make options
```bash
# Clean all previous build items except the source raspian image
make clean

# Clean up the source image and trigger a new download
make distclean
```

### Build layout
```
fluiddpi/
  /emulation - Dependencies for emulation testing
  /src/image - Base raspbian image
  /src/workspace - Created during build
```