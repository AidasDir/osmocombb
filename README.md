==========================
OSMOCOM GSM security tools
==========================

These tools allows you to analize gsm security, crack and decript raw GSM
bursts.

It consists of several additional tools i wrote for analyzing GSM:

- gsmcrack.py: allows you to crack raw gsm data using predictions. Has also 
several automatic tools for deciphering gsm data from phones from which we
can't get KC directly.
- decocde_burst: allows you to decode raw bursts using key or not.
- encode_burst: allows you to encode raw frame data and get raw bursts.

Usage examples:
---------------

Installation:
This tools require several dependencies, besides those of osmocom. There is a list of dependencies used in ubuntu, if you are using another distro it shouldn't be hard to find equivalents, because they are all python dependencies, so you can use easy_install or pip.

```bash
apt-get install pcscd python-mechanize python-jinja2 python-pyscard 
python-lxml python-serial
```
Ubuntu preparation guide:
Install git.
Add support for reading serial devices and disks as non superuser:
```bash
sudo apt-get install git
sudo usermod -a -G dialout <your_username>
sudo usermod -a -G disk <your_username>
```
Install wireshark and add support for running it as user:
```bash
sudo apt-get install wireshark
sudo apt-get install libcap2-bin
sudo groupadd wireshark
sudo usermod -a -G wireshark <your_username>
newgrp wireshark
sudo chgrp wireshark /usr/bin/dumpcap
sudo chmod 750 /usr/bin/dumpcap
sudo setcap cap_net_raw,cap_net_admin=eip /usr/bin/dumpcap
```
Install osmocom deps:
```bash
sudo apt-get install libtool shtool autoconf git-core pkg-config make gcc
```
Install arm toolchain:
```bash
sudo apt-get install python-software-properties
sudo add-apt-repository ppa:bdrung/bsprak
sudo apt-get update
sudo apt-get install arm-elf-toolchain
```
If you have precise(12.04) you will have to change from precise to oneiric in "/etc/apt/sources.list.d/bdrung-bsprak-precise.list".

Install deps for gsmcrack.py:
```bash
apt-get install pcscd python-mechanize python-jinja2 python-pyscard 
python-lxml python-serial
```
Install sniffer:
```bash
git clone git://github.com/offlinehacker/osmocom-bb.git
cd osmocom-bb/src
make
```
Install spoofer:
```bash
git clone git://github.com/offlinehacker/osmocom-bb.git osmocom-bb-identity
cd osmocom-bb-identity
git checkout identity
cd src
make
```
You are ready to go...

Usage:
