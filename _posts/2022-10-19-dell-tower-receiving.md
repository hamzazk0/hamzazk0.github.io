---
layout: post
title: "Dell T620 Server Receiving"
date: 2022-10-19 20:00:00 -0500
categories: Homelab
tags: homelab dell server hardware
---

## Summary

The Dell T620 was purchased on Ebay as refurbished. So some questions need to be answered before the server software is setup. Below is the process I will follow and some questions to verify everything arrived as expected.

## To Do List

1. Add Barebones chassis (mobo, cpu (x2), memory) combo to inventory
2. Add Power Supplies to inventory
3. Add 120GB PNY SSD (x2) drives to inventory
4. Add 8x2TB hard drives to inventory (document position of each drive in chassis)
5. Listen to noise to for acceptable levels

## Question, Hypothesis, and Answers

Q: Hardware CPU configuration

H: 2x Xeon E5-2960

A: 2x Xeon E5-2960

Q: Hardware memory configuration

H: 64GB between two CPUs

A: 64GB between two CPUs mixed sticks (6 slots per CPU).

Q: Hardware storage configuration

H: 8x2TB (Note: Pictures look like its a 12 bay chassis)

A: All present, all working

Q: Noise Level when running

H: Loud at PSU at startup and then slows down

A: Matches expectation, usuable in the same room. There are 6 fans (4 front, 2 rear) in the case all 92mm (probably) custom brackets and shroud

Q: What is the CPU upgrade path?

H: no known upgrade path

A: unknown, check motherboard chipset.

Q: What is the Memory upgrade path?

H: Fill extra slots up to 768GB

A: The ideal upgrade configuration is 96GB at (6x16GB) for the triple channel memory configuration of the Xeon CPUs.

Q: Add extra expansion through PCIE

H: 10GB networking, GPU for extra processing

A: Upgrade for PCIE drives (separation from raid card)

## Notes

1. Damn that chassis is heavy
    * Needed extra hands to move at 85 lbs
2. Its also very dusty
3. Loaded up two bays with some 3.5" 500 GB WD drives i had lying around
4. Bay 1,2 (from top left) has the surround bezel coming off that makes it hard to pull the sled
5. Ordered some 2.5" to 3.5" Adapters and sata relocators for putting boot disks in drive sleds
