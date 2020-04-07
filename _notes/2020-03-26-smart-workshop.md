---
title: 'Smart Workshop'
subtitle: 'Making a smart and safe workshop'
date: 2020-03-26 00:00:00
description:
featured_image: '/images/projects/smart-workshop/azmeI.jpg'
---

![](/images/projects/smart-workshop/azmeI.jpg)

## Xiaomi & Mi Home

Well integrated system via Mi Home app
- Temperature & Humidity Sensor
- Mi Air Purifier
- Motion detection (short range)
- Door contact sensor
- Button Switch
- 360deg Camera


+:
- Cheap

-:
- You cannot fully integrate all devices from Xiaomi to Homekit or Google Home.


## Shinobi

-> - Laggy interface and interactions + impossible to record on motion + 5/10secs delay
-> + timelapse

## Custom Software

movedetect_success.py works by image comparision
rt-motion-detection-opencv-python is advanced motion detection, use test.py

### Streaming video to browser optimized
node-rtsp-stream allow to use ffmpeg to transform images in real time and send them to browser via websocket
and display them in the browser with jsmpeg (js decoder)

-> + almost realtime in browser + low browser cpu consumption
https://github.com/kyriesent/node-rtsp-stream
using MPEG1 Video Decoder in JavaScript:
https://github.com/phoboslab/jsmpeg

### Install OpenCV

```
sudo apt install python3-opencv
python3 -c "import cv2; print(cv2.__version__)"
```

### Scan for RTSP camera in network

```
sudo nmap --open -p 554 192.168.0.1/24
```

### CC2531

```
sudo apt install dh-autoreconf libusb-1.0-0-dev libboost-all-dev
git clone https://github.com/dashesy/cc-tool.git
cd cc-tool
./bootstrap
./configure
make
make install
man cc-tool

```

### Reverse SSH behind NAT with proxy machine

On the computer behind a carrier grade NAT:
`ssh -R 19999:localhost:8089 root@<IP-OF-GATEWAY>`
8089 est le port qui va etre forwardé / listen sur l'ordi restreint
19999 est le port qui va etre exposé ce port forwardé

*Sur le proxy pour tester: wget localhost:19999*

Sur la machine locale:
ssh -L 8083:localhost:19995 root@212.47.239.82

## Manager connection wifi via ligne commande

sudo nmtui

## Connect to Foscam

sudo nmap -sP 192.168.0.1/24

```
Nmap scan report for 192.168.0.47
Host is up (-0.053s latency).
MAC Address: E8:AB:FA:64:EA:F8 (Shenzhen Reecam Tech.Ltd.)
```

Then connect to web interface on:
http://192.168.0.47:88/

Foscams URL:
```
rtsp://username:pwd@IP:port/videoMain
rtsp://username:pwd@IP:port /videoSub
rtsp://username:pwd@IP:port /audio
```

For FI9826p:
rtsp://emca:<password>@192.168.1.101:88/videoMain

## Wireguard

Add:
 ```
 deb http://ppa.launchpad.net/wireguard/wireguard/ubuntu bionic main
deb-src http://ppa.launchpad.net/wireguard/wireguard/ubuntu bionic main

```
To /etc/apt/sources.list

Then

run

sudo apt -o Acquire::AllowInsecureRepositories=true -o Acquire::AllowDowngradeToInsecureRepositories=true update

sudo apt install wireguard





## Old previous research before finding zigbee2mqtt


### Solution

*HomeKit support for the impatient*:
https://github.com/homebridge/homebridge

Homebridge is a lightweight NodeJS server you can run on your home network that emulates the iOS HomeKit API. It supports Plugins, which are community-contributed modules that provide a basic bridge from HomeKit to various 3rd-party APIs provided by manufacturers of "smart home" devices.

List of plugins: https://www.npmjs.com/search?q=homebridge-plugin

### For Xiaomi

Homebridge/Homekit:
- Temperature & Humidity sensor: https://www.npmjs.com/package/homebridge-mi-hygrothermograph
- Air Purifier: https://github.com/clauzewitz/homebridge-xiaomi-purifier (not working with PRO cf Issues)
- Door contact sensor: Nope

---------------- NEED TO WAIT TO BUY ANOTHER KIT -----------------

https://github.com/aholstenson/miio
MQTT Xiaomi:

1- Reset your Mi home base
2- Connect to his WIFI (the device will go in AP mode when not configured)
3- Run `./cli/index.js discover --sync
4- Retrieve the token:

```
unitech@zion:~/emca/xiaomi/miio$ ./cli/index.js discover --sync
 INFO  Discovering devices. Press Ctrl+C to stop.

Device ID: 94919605
Model info: Unknown
Address: 192.168.1.1
Token: 646944546357756c473932617a536a5a via auto-token
Support: Unknown
```



Get the token and be (potentially) able to interact with Mi home:
https://github.com/aholstenson/miio/blob/master/docs/management.md#getting-the-token-of-a-device

Discover token via:
cd /home/unitech/emca/xiaomi/miio
./cli/index.js discover
-> should display socket when mi home is reseted

And then to interact:

```
const miio = require('.');

function handleErrorHere(err) {
  console.log('wtjd')
  console.log(err)
}
// Resolve a device, resolving the token automatically or from storage
// miio.device({ address: '192.168.1.101' })
//   .then(device => console.log('Connected to', device))
//   .catch(err => handleErrorHere);

// Resolve a device, specifying the token (see below for how to get the token)
miio.device({ address: '192.168.1.101', token: 'token-as-hex' })
  .then(device => console.log('Connected to', device))
  .catch(err => handleErrorHere);

```
