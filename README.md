# Novetta bleee

<p align="center">
  <img src="https://github.com/SegFaultPR/Novetta_bleee/blob/master/img/novetta-logo.png"  height="100">
</p>

## Disclaimer
These scripts are experimental PoCs that show what an attacker may be able to collect from Apple devices if they sniff Bluetooth traffic.

***We have removed parts of the this code from the origional repo***
***That includes: Airdrop, hashing/phone number and message***  

***This project is created only for educational purposes and cannot be used for law violation or personal gain.<br/>The author of this project is not responsible for any possible harm caused by the materials of this project***


## Requirements
To use these scripts you will need a Bluetooth adapter for sending `BLE` messages and WiFi card supporting active monitor mode with frame injection we recommend the Atheros AR9280 chip (IEEE 802.11n) we used to develop and test this code.
We have tested these PoCs on **Kali Linux**

## Features Added

### Geo Tags
  As this will be for demonstration purposes the new code base will contain the ability to tag 
  We will be adding tags for all the conferences our collection rig will be traveling to.

### limits on displayed devices
  Screen realestate is key within the terminal.  While the origional code allows you to scroll down and onto another "screen", we will be limiting the ativity on the screen to the devices nearby.

### White Listing
  No one wants to see their own devices on the screen and devices will also be white listed per request.


## Installation

```
# clone main repo
git clone https://github.com/SegFaultPR/Novetta_bleee.git && cd ./Novetta_bleee
# install dependencies
sudo apt update && sudo apt install -y bluez libpcap-dev libev-dev libnl-3-dev libnl-genl-3-dev libnl-route-3-dev cmake libbluetooth-dev
sudo pip3 install -r requirements.txt
# clone and install owl for AWDL interface
git clone https://github.com/seemoo-lab/owl.git && cd ./owl && git submodule update --init && mkdir build && cd build && cmake .. && make && sudo make install && cd ../..
```

## How to use

Before using the tool, check that your Bluetooth adapter is connected

```
hcitool dev
Devices:
    hci0    00:1A:7D:DA:71:13
```


### Script: [ble_read_state.py](https://github.com/SegFaultPR/Novetta_bleee.git/blob/master/ble_read_state.py)

This script sniffs `BLE` traffic and displays status messages from Apple devices.

![dev_status](img/dev_status.png)

```bash
python3 ble_read_state.py -h
usage: ble_read_state.py [-h] [-s] [-t TTL]

Apple bleee. Apple device sniffer
---chipik

optional arguments:
  -h, --help          show this help message and exit
  -s, --ssid          Get SSID from requests
  -t TTL, --ttl TTL   ttl
```

For monitoring you can just run the script without any parameters

```bash
sudo python3 ble_read_state.py
```

press `Ctrl+q` to exit

If you want to get phone numbers from a WiFi password request, you have to prepare the hashtable (please find scripts below), setup a web server and specify `base_url` inside this script and run it with  `-c` parameter

```bash
sudo python3 ble_read_state.py -с
```


## Contacts
[Novetta](https://Novetta.com)


SegFaultPR<br>
[GITHUB](https://github.com/SegFaultPR/)<br>

Wasabi<br>
[GITHUB thewasabiguy](https://github.com/thewasabiguy)<br>
[GITHUB tallmon-novetta](https://github.com/tallmon-novetta)<br>
[TWITTER @FrustratedITGuy](https://twitter.com/FrustratedITGuy)
