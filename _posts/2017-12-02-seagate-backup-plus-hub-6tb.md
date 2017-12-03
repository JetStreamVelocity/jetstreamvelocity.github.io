---
published: true
layout: post
title: Seagate Backup Plus Hub 6TB
excerpt: Seagate Backup Plus Hub 6TB
categories: Articles
tags:
  - Seagate
  - 6TB
comments: true
---

* Table of Contents
{:toc}

# Introduction

I purchased this from [Amazon](https://www.amazon.co.uk/gp/product/B01IAD5ZEE) over Black Friday. I was keen to check the details of the hard disk inside this case.

_smartctl_ needed the _-d_ option to be provided. Google led me to [smartmontools page](https://www.smartmontools.org/wiki/Supported_USB-Devices) where I found _-d sat_ being reported to work for Seagate USB drives. I tried the same.

```
[jetstream@dellgx620 ~]$ sudo smartctl -a -d sat /dev/sdb
smartctl 6.5 2016-05-07 r4318 [x86_64-linux-4.13.13-200.fc26.x86_64] (local build)
Copyright (C) 2002-16, Bruce Allen, Christian Franke, www.smartmontools.org

=== START OF INFORMATION SECTION ===
Device Model:     ST6000DM003-2CY186
Serial Number:    XXXXXXXX
LU WWN Device Id: 5 000c50 0aa1257da
Firmware Version: 0001
User Capacity:    6,001,175,126,016 bytes [6.00 TB]
Sector Sizes:     512 bytes logical, 4096 bytes physical
Rotation Rate:    5425 rpm
Device is:        Not in smartctl database [for details use: -P showall]
ATA Version is:   ACS-3 T13/2161-D revision 5
SATA Version is:  SATA 3.1, 6.0 Gb/s (current: 3.0 Gb/s)
Local Time is:    Sat Dec  2 21:51:34 2017 GMT
SMART support is: Available - device has SMART capability.
SMART support is: Enabled

=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: PASSED

General SMART Values:
Offline data collection status:  (0x82) Offline data collection activity
                                        was completed without error.
                                        Auto Offline Data Collection: Enabled.
Self-test execution status:      (   0) The previous self-test routine completed
                                        without error or no self-test has ever
                                        been run.
Total time to complete Offline
data collection:                (    0) seconds.
Offline data collection
capabilities:                    (0x7b) SMART execute Offline immediate.
                                        Auto Offline data collection on/off support.
                                        Suspend Offline collection upon new
                                        command.
                                        Offline surface scan supported.
                                        Self-test supported.
                                        Conveyance Self-test supported.
                                        Selective Self-test supported.
SMART capabilities:            (0x0003) Saves SMART data before entering
                                        power-saving mode.
                                        Supports SMART auto save timer.
Error logging capability:        (0x01) Error logging supported.
                                        General Purpose Logging supported.
Short self-test routine
recommended polling time:        (   1) minutes.
Extended self-test routine
recommended polling time:        ( 737) minutes.
Conveyance self-test routine
recommended polling time:        (   2) minutes.
SCT capabilities:              (0x30a5) SCT Status supported.
                                        SCT Data Table supported.

SMART Attributes Data Structure revision number: 10
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x000f   081   064   006    Pre-fail  Always       -       122962415
  3 Spin_Up_Time            0x0003   092   092   000    Pre-fail  Always       -       0
  4 Start_Stop_Count        0x0032   100   100   020    Old_age   Always       -       12
  5 Reallocated_Sector_Ct   0x0033   100   100   010    Pre-fail  Always       -       0
  7 Seek_Error_Rate         0x000f   067   060   045    Pre-fail  Always       -       5123291
  9 Power_On_Hours          0x0032   100   100   000    Old_age   Always       -       100 (158 143 0)
 10 Spin_Retry_Count        0x0013   100   100   097    Pre-fail  Always       -       0
 12 Power_Cycle_Count       0x0032   100   100   020    Old_age   Always       -       11
183 Runtime_Bad_Block       0x0032   100   100   000    Old_age   Always       -       0
184 End-to-End_Error        0x0032   100   100   099    Old_age   Always       -       0
187 Reported_Uncorrect      0x0032   100   100   000    Old_age   Always       -       0
188 Command_Timeout         0x0032   100   100   000    Old_age   Always       -       0
189 High_Fly_Writes         0x003a   100   100   000    Old_age   Always       -       0
190 Airflow_Temperature_Cel 0x0022   073   051   040    Old_age   Always       -       27 (Min/Max 19/27)
191 G-Sense_Error_Rate      0x0032   100   100   000    Old_age   Always       -       0
192 Power-Off_Retract_Count 0x0032   100   100   000    Old_age   Always       -       11
193 Load_Cycle_Count        0x0032   100   100   000    Old_age   Always       -       15
194 Temperature_Celsius     0x0022   027   049   000    Old_age   Always       -       27 (0 18 0 0 0)
195 Hardware_ECC_Recovered  0x001a   081   064   000    Old_age   Always       -       122962415
197 Current_Pending_Sector  0x0012   100   100   000    Old_age   Always       -       0
198 Offline_Uncorrectable   0x0010   100   100   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x003e   200   200   000    Old_age   Always       -       0
240 Head_Flying_Hours       0x0000   100   253   000    Old_age   Offline      -       36 (72 220 0)
241 Total_LBAs_Written      0x0000   100   253   000    Old_age   Offline      -       11721965094
242 Total_LBAs_Read         0x0000   100   253   000    Old_age   Offline      -       1176845705

SMART Error Log Version: 1
No Errors Logged

SMART Self-test log structure revision number 1
No self-tests have been logged.  [To run self-tests, use: smartctl -t]

SMART Selective self-test log data structure revision number 1
 SPAN  MIN_LBA  MAX_LBA  CURRENT_TEST_STATUS
    1        0        0  Not_testing
    2        0        0  Not_testing
    3        0        0  Not_testing
    4        0        0  Not_testing
    5        0        0  Not_testing
Selective self-test flags (0x0):
  After scanning selected spans, do NOT read-scan remainder of disk.
If Selective self-test is pending on power-up, resume after 0 minute delay.
```

Next, I checked what power mode it is staying in. The following command will not wake up the drive during the interrogation, if it was sleeping.
```
[jetstream@dellgx620 ~]$ sudo smartctl -d sat -i -n standby /dev/sdb
smartctl 6.5 2016-05-07 r4318 [x86_64-linux-4.13.13-200.fc26.x86_64] (local build)
Copyright (C) 2002-16, Bruce Allen, Christian Franke, www.smartmontools.org

=== START OF INFORMATION SECTION ===
Device Model:     ST6000DM003-2CY186
Serial Number:    XXXXXXXX
LU WWN Device Id: 5 000c50 0aa1257da
Firmware Version: 0001
User Capacity:    6,001,175,126,016 bytes [6.00 TB]
Sector Sizes:     512 bytes logical, 4096 bytes physical
Rotation Rate:    5425 rpm
Device is:        Not in smartctl database [for details use: -P showall]
ATA Version is:   ACS-3 T13/2161-D revision 5
SATA Version is:  SATA 3.1, 6.0 Gb/s (current: 3.0 Gb/s)
Local Time is:    Sun Dec  3 04:22:31 2017 GMT
SMART support is: Available - device has SMART capability.
SMART support is: Enabled
Power mode was:   IDLE_A
```
