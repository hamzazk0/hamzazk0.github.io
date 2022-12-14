---
layout: post
title: "Installing Proxmox on Dell Server"
date: 2022-10-21 20:00:00 -0500
categories: Homelab
tags: homelab dell server software hardware
---

## Summary

This is a summary of the process I went through for installing Proxmox on my new to me Dell T620. I followed the guide below published by Craft Computing.

[![Craft Computing Proxmox Tutorial](https://img.youtube.com/vi/azORbxrItOo/0.jpg)](https://www.youtube.com/watch?v=azORbxrItOo "Craft Computing")

## Steps

1. Proxmox VE Installer
2. 8GB drive to install iso to flash drive (Etcher)
3. Boot to USB drive
4. Select drive to install on (raid1 if possible)
5. Select IP and hostname for system
6. Access from Web browser
7. :8006 port for proxmox UI (accept risk)
8. login as root with assigned password
9. storage configuration in proxmox
10. ZFS, create ZFS, Local-Proxmox
11. Datacenter, Storage, add, CIFS vs NFS (what is possible?)
12. Network-proxmox, ip, auth, proxmox share (disk image, iso image, container, container images)
13. Local cannot store disk or iso images

## Notes

1. (4) 2x PNY 120GB SSDs
2. (9) possibly have a network shared disk that can be used to store vms from another location as opposed to loading them via usb every time
