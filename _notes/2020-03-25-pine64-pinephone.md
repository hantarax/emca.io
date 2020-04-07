---
title: 'Pin64 Pinephone'
subtitle: A Linux compatible modern smartphone
date: 2020-03-26 00:00:00
description:
featured_image: '/images/projects/smart-workshop/azmeI.jpg'
---

## Unpacking & Installation

Enable battery: Remove back cover and remove sticker next to battery connectors.

Get a fast micro SD card (Sandisk Extreme 64gb for instance).

Download a distro listed listed here https://wiki.pine64.org/index.php/PinePhone_Software_Release#Software_Releases

Unzip and flash SD card from your laptop.

Expand partition size

```
sudo su

apt update
apt-cache search growpart
# Then install one version available in your repo

growpart /dev/sdX 1
resize2fs /dev/sdX 1
```

Will be autobooted.

*here stop From article https://wiki.pine64.org/index.php/PinePhone_Software_Release#Software_Releases*
