---
layout: post
title: "Homelab Progress with Proxmox"
date: 2022-10-23 20:00:00 -0500
categories: Homelab
tags: homelab hypervisor dell server software hardware
---

## Summary

These are the results of the process for installing Proxmox on my new to me Dell T620. There were many issues with process and many resets on throughout the weekend.

[![Craft Computing Proxmox Tutorial](https://img.youtube.com/vi/azORbxrItOo/0.jpg)](https://www.youtube.com/watch?v=azORbxrItOo "Craft Computing")

## Booting the T620

The first step was to boot into the BIOS and explore the options. It was as simple as connecting the machine to a monitor, keyboard, mouse, and network switch. The buttons you want to use when the machine is powering on are F2 (BIOS settings), F10 (Lifecycle controller and iDRAC settings) and F11 (boot options). I combed the BIOS settings to setup the hardware to my liking and configured the iDRAC to use the first LAN port (of two) to save ports on my network switch. I managed to see in the iDRAC that the two SAS Cables on the RAID card were switched. I disassembled the hardware and connected it correctly.

### Taking apart Cooling

1. Depress tab on top right and slide out CPU cooling shroud (brings fans with it)
2. Pull blue tabs at top left and bottom left and pull the fan holder (brings fans with it)

## iDRAC 7 and Lifecycle Controller

I spent about a day exploring the iDRAC 7 settings built into the machine to see if I could use anything. I am missing many licenses that are required for certain features so many Dell management features were not available. I found it not very helpful except to read the status of the machine prior to booting into the OS. The Lifecycle controller was also not very helpful since I don't have the licenses. I ended up disabling the Lifecycle controller to decrease boot times.

## Proxmox Installation Sillyness

I had two 120 GB SSDs on the slots on the front panel which I intended to be the Proxmox bootdrives. However, one of them was dead on arrival. Because I have not decided on the final configuration, I decided to just install it on just one.

Once in Proxmox, thing I tried to do was create a TrueNAS Scale VM. I configured the VM to directly pass through the Raid card as an entire device. However, when you pass your drive interface to another operating system. The hypervisor loses its reference to the boot drive. _**I managed to brick Proxmox on my first run.**_ I resolved this by just installing Proxmox on an 64GB USB drive on the internal USB port. Because of this, I decided that this version of Proxmox will just be a test until I break it again while I decide the final configuration.

## Pi-hole and Internet Pi

I followed Jeff Geerling's tutorial for installing the Internet Pi project with the goal of monitor my network performance along with adblocking. After some tinkering with ansible, errors spit out during installation. I ended up decided against continuing further because of duplicate open ports (80 and 443) on the same machine. I ended up creating an Ubuntu Server VM to run pi-hole and it worked as intended.

## Truenas Scale

I installed a test instance of Truenas core on the main server once I resolved the disk passthrough on the raid card. I began testing Plex to see how it runs for the final version. It ran well with my hardware. I began copying my media to the NAS to test read and write performance. I ended up allocating 12 cores and 24GB of RAM from 6 cores and 12GB. Upon copying, media the hard drives registered many disk write errors and ended up crashing TrueNAS. When I restarted the Truenas VM, Proxmox crashed and failed to restart. I ended up putting away the server while I wait for the new boot drives to arrive.

## Issues

1. Make sure to configure to UEFI boot. Cannot boot Proxmox OS drive without it.
2. Missing Dell Licenses and iDRAC hardware.
3. There is no good spot to mount 2.5" SSDs separate from RAID

## Future Plans

1. Use PCIE adapter with NVME disks to boot hypervisor in mirrored array
2. In spare time, spend more time comparing Proxmox vs TrueNAS Scale to determine which suits my uses better
3. Test Jeff Geerling's Internet-Pi on my Raspberry Pi 0
4. Rerun Lifecycle Controller Hardware assessment and remove/replace non-functional drives

### Hardware Purchasing

1. 2x NVME SSDs
2. 2x PCIE NVME adapters
