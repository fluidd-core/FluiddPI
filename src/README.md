Build FluiddPI From within FluiddPI / OctoPi / Raspbian / Debian / Ubuntu
FluiddPI can be built from Debian, Ubuntu, Raspbian, OctoPi, or even FluiddPI. Build requires about 5 GB of free space available. You can build it by issuing the following commands:

sudo apt-get install gawk util-linux qemu-user-static git p7zip-full python3

git clone https://github.com/guysoft/CustomPiOS.git
git clone https://github.com/cadriel/FluiddPI.git
cd FluiddPI/src/image
wget -c --trust-server-names 'https://downloads.raspberrypi.org/raspios_lite_armhf_latest'
cd ..
../../CustomPiOS/src/update-custompios-paths
sudo modprobe loop
sudo bash -x ./build_dist
