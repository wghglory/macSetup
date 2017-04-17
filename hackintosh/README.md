# Hackintosh

Please refer [hackintosh](hackintosh.md). My EFI is stored at baidu disk named "EFI-10.15.1.rar".

## Machine Configuration

- Motherboard: gigabyte Z370 hd3
- Audio: Realtek alc892
- LAN: INTER GBE 10/100/1000
- CPU: I7 8th 8700
- Graphics: Radeon RX 560
- WIFI and bluetooth: 博通 BCM943602CS 4 天线

## Installation Step

1. <https://www.tonymacx86.com/threads/unibeast-install-macos-mojave-on-any-supported-intel-based-pc.259381/>

   - BIOS settings:
     - To access BIOS/UEFI Setup, press and hold Delete on a USB Keyboard while the system is booting up
     - Load Optimized Defaults
     - If your CPU supports VT-d, disable it
     - If your system has CFG-Lock, disable it
     - If your system has Secure Boot Mode, disable it
     - Set OS Type to Other OS
     - If your system has IO Serial Port, disable it
     - Set XHCI Handoff to Enabled
     - If you have a 6 series or x58 system with AWARD BIOS, disable USB 3.0
     - Save and exit.

1. Note after installation, need copy USB EFI to machine's hard drive and create its EFI via multi-beast. Hence the machine doesn't need USB driver to start the system. Otherwise, i'm seeing the black screen due to missing of EFI.
1. Post installation of drivers: refer Mac-drivers.mb

## Command

```bash
diskutil list
```

```
/dev/disk0 (internal):
   #:                       TYPE NAME                    SIZE       IDENTIFIER
   0:      GUID_partition_scheme                         250.1 GB   disk0
   1:                        EFI EFI                     209.7 MB   disk0s1
   2:                 Apple_APFS Container disk1         249.8 GB   disk0s2

/dev/disk1 (synthesized):
   #:                       TYPE NAME                    SIZE       IDENTIFIER
   0:      APFS Container Scheme -                      +249.8 GB   disk1
                                 Physical Store disk0s2
   1:                APFS Volume Mojave                  11.7 GB    disk1s1
   2:                APFS Volume Preboot                 45.0 MB    disk1s2
   3:                APFS Volume Recovery                517.0 MB   disk1s3
   4:                APFS Volume VM                      20.5 KB    disk1s4

/dev/disk2 (internal, physical):
   #:                       TYPE NAME                    SIZE       IDENTIFIER
   0:      GUID_partition_scheme                        *1.0 TB     disk2
   1:                        EFI EFI                     209.7 MB   disk2s1
   2:       Microsoft Basic Data SOFTWARE                314.4 GB   disk2s2
   3:       Microsoft Basic Data LIFE                    371.0 GB   disk2s3
   4:       Microsoft Basic Data WORK                    314.6 GB   disk2s4

/dev/disk3 (internal, physical):
   #:                       TYPE NAME                    SIZE       IDENTIFIER
   0:      GUID_partition_scheme                        *250.1 GB   disk3
   1:           Windows Recovery                         523.2 MB   disk3s1
   2:                        EFI NO NAME                 104.9 MB   disk3s2
   3:         Microsoft Reserved                         16.8 MB    disk3s3
   4:       Microsoft Basic Data                         249.4 GB   disk3s4
```

## Mount EFI

Better to use `clover configurator`.

```bash
Guanghuis-iMac:~ derek$ sudo mkdir /Volumes/efi
Guanghuis-iMac:~ derek$ sudo mount -t msdos /dev/disk0s1 /Volumes/efi
```

## Disable SIP due to xtraFinder installation

<https://www.tonymacx86.com/threads/how-to-disable-sip.244637>

## Other

图片不能显示：<http://bbs.pcbeta.com/viewthread-1802194-1-1.html>
