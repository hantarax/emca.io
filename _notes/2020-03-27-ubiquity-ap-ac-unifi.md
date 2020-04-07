---
title: 'Smart Workshop'
subtitle: 'Making a smart and safe workshop'
date: 2020-03-26 00:00:00
description:
featured_image: '/images/projects/smart-workshop/azmeI.jpg'
---

On Ubuntu 18.04 you must install MongoDB first. BUT you MUST install a version < 3.6.0 else it will fail:

```bash
# Add MongoRepo
wget -qO - https://www.mongodb.org/static/pgp/server-3.4.asc | sudo apt-key add -
echo "deb https://repo.mongodb.org/apt/ubuntu xenial/mongodb-org/3.4 multiverse" | sudo tee /etc/apt/sources\
.list.d/mongodb-org-3.4.list
sudo apt update
# Install
sudo apt-install mongodb-server
```

Then run this script (and answer NO to installing Mongo):

```bash
wget https://get.glennr.nl/unifi/install/unifi-5.12.66.sh
sudo bash unifi-5.12.66.sh
```
*Details about this script: https://community.ui.com/questions/UniFi-Installation-Scripts-or-UniFi-Easy-Update-Script-or-UniFi-Lets-Encrypt-or-Ubuntu-16-04-18-04-/ccbc7530-dd61-40a7-82ec-22b17f027776*

Then connect your Ubiquity AP-AC via RJ45 to your computer.

Now open http://localhost:8443, then login (default is ubnt/ubnt).

Now you can configure your AP.
