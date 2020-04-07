---
title: 'Pin64 Pinephone'
subtitle: A Linux compatible modern smartphone
date: 2020-03-26 00:00:00
description:
featured_image: '/images/projects/smart-workshop/azmeI.jpg'
---

The router GL-X750 Spitz from GL.inet, openwrt embedded, small size factor.

Setup root password

Go to http://192.168.8.1/cgi-bin/luci/admin/system/admin

Add your SSH key

Then `ssh root@192.168.8.1` (change accordingly to your router ip)

To list all connected clients:

```
root@GL-X750:~# ip neigh
192.168.8.177 dev br-lan lladdr b4:6b:fc:3d:b6:2f REACHABLE
192.168.8.174 dev br-lan  INCOMPLETE
fe80::e646:daff:fe74:1e20 dev br-lan  FAILED
fe80::e137:b68a:bf12:db69 dev br-lan lladdr b4:6b:fc:3d:b6:2f REACHABLE
fdcf:9f8c:9e11:10:85ab:1c8d:1f2b:9188 dev br-lan lladdr b4:6b:fc:3d:b6:2f REACHABLE
fdcf:9f8c:9e11:10:4ccb:ca55:52fe:ab93 dev br-lan lladdr e4:46:da:74:1e:20 STALE
```
(all REACHABLE minus - 2 is one device) The FAILED is my phone I've disconnected from the gl-x750 router.

or run the command:

```
opkg update
opkg install arp-scan
sudo arp-scan -l -t 200
```

4G-> Wifi & BLE

Peut faire office de collecteur de device Wifi, Zigbee où PM2 runtime collecterais les

C'est un ordinateur (raspberry like) connecté à internet (SSH, routeur automatiquement connecté...)

Ca peut m'être utile pour:
- Surveillance d'un objet d'art connecté
- En autonomie à cadence d'une batterie 4200mah utilisée par jour

Permet de:
- Proposer des systèmes clés en main, des réseaux d'objet connectés pré testés en usine de production
- Déployer un système de surveillance pour des champs (cameras, capteurs hygro, temperature, acidité du sol)
pour des *modules de captage* basse bande passante (Lora sensors) que des modules à utilisation de haute bande
passante (caméras).

Équivalence au niveau de captage de donnée à une gateway lora. Trouver plus de différentiateurs avec des modules
de captage haute bande passante que les caméras seulement.
