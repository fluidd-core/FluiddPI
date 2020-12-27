Build FluiddPI From within FluiddPI / Raspbian / Debian / Ubuntu
FluiddPI can be built from Debian, Ubuntu, Raspbian, or even FluiddPI.

Build requires about 2.5 GB of free space available. You can build it by issuing the following commands:

```bash
sudo apt-get install gawk util-linux qemu-user-static git p7zip-full python3
```

```bash
git clone https://github.com/guysoft/CustomPiOS.git
git clone https://github.com/cadriel/FluiddPI.git
cd FluiddPI/src/image
wget -c --trust-server-names 'https://downloads.raspberrypi.org/raspios_lite_armhf_latest'
cd ..
../../CustomPiOS/src/update-custompios-paths
sudo modprobe loop
sudo bash -x ./build_dist
```
