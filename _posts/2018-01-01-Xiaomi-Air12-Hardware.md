---
published: true
layout: post
title: Xiaomi Air 12 Hardware
excerpt: Hardware of Xiaomi Air 12 reported by Fedora 26
categories: Articles
tags:
  - XiaomiAir12
  - Fedora26
comments: true
---

* Table of Contents
{:toc}

# Hardware Information reported by Fedora

## _lspci_ output

```bash
[jetstream@Air12 ~]$ lspci
00:00.0 Host bridge: Intel Corporation Device 590c (rev 02)
00:02.0 VGA compatible controller: Intel Corporation Device 591e (rev 02)
00:04.0 Signal processing controller: Intel Corporation Xeon E3-1200 v5/E3-1500 v5/6th Gen Core Processor Thermal Subsystem (rev 02)
00:08.0 System peripheral: Intel Corporation Xeon E3-1200 v5/v6 / E3-1500 v5 / 6th/7th Gen Core Processor Gaussian Mixture Model
00:14.0 USB controller: Intel Corporation Sunrise Point-LP USB 3.0 xHCI Controller (rev 21)
00:15.0 Signal processing controller: Intel Corporation Sunrise Point-LP Serial IO I2C Controller #0 (rev 21)
00:16.0 Communication controller: Intel Corporation Sunrise Point-LP CSME HECI #1 (rev 21)
00:17.0 SATA controller: Intel Corporation Sunrise Point-LP SATA Controller [AHCI mode] (rev 21)
00:1d.0 PCI bridge: Intel Corporation Sunrise Point-LP PCI Express Root Port #9 (rev f1)
00:1f.0 ISA bridge: Intel Corporation Sunrise Point-LP LPC Controller (rev 21)
00:1f.2 Memory controller: Intel Corporation Sunrise Point-LP PMC (rev 21)
00:1f.3 Audio device: Intel Corporation Sunrise Point-LP HD Audio (rev 21)
00:1f.4 SMBus: Intel Corporation Sunrise Point-LP SMBus (rev 21)
01:00.0 Network controller: Intel Corporation Wireless 8265 / 8275 (rev 78)
```


## _lsusb_ output
```bash
[jetstream@Air12 ~]$ lsusb
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 003: ID 04f2:b59a Chicony Electronics Co., Ltd
Bus 001 Device 002: ID 8087:0a2b Intel Corp.
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```

