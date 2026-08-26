# Cisco Packet Tracer – Network Cabling Lab

## Overview

This project demonstrates the physical cabling of routers and switches network using Cisco Packet Tracer.

The main objective is to demonstrate an understanding of:

* Ethernet cable types
* MDI and MDI-X
* Copper straight-through cables
* Copper crossover cables
* Fiber-optic connections
* Router-to-router connections
* Router-to-switch connections
* Switch-to-switch connections
* Switch-to-end-device connections
* Physical link distances and appropriate media selection

## For this exercise, Auto MDI-X is assumed to be disabled or unsupported**. Therefore, traditional MDI/MDI-X cabling rules are used.

# Cabling Plan

## 1. Router-to-Router Connections

| Connection | Interfaces                | Distance | Cable            | Reason                                |
| ---------- | ------------------------- | -------: | ---------------- | ------------------------------------- |
| R1 ↔ R2    | R1 Fa0/0 ↔ R2 Fa0/0   |     50 m | Copper crossover | MDI ↔ MDI                             |
| R1 ↔ R3    | R1 Gig3/0 ↔ R3 Gig2/0 |     3 km | Fiber            | Long-distance connection              |
| R3 ↔ R4    | R3 Fa0/0 ↔ R4 Fa0/0   |    250 m | Fiber            | Appropriate for the required distance |

### R1 ↔ R2

Both ends are router Ethernet interfaces.

The R1–R2 connection uses a copper crossover cable.

## 2. Router-to-Switch Connections

| Connection | Interfaces               | Cable            | Reason      |
| ---------- | ------------------------ | ---------------- | ----------- |
| R2 ↔ SW1   | R2 Fa2/1 ↔ SW1 Fa0/1 | Straight-through | MDI ↔ MDI-X |
| R2 ↔ SW2   | R2 Fa1/0 ↔ SW2 Fa2/1 | Straight-through | MDI ↔ MDI-X |
| R4 ↔ SW5   | R4 Fa1/0 ↔ SW5 Fa2/1 | Straight-through | MDI ↔ MDI-X |
| R4 ↔ SW6   | R4 Fa2/0 ↔ SW6 Fa0/1 | Straight-through | MDI ↔ MDI-X |


## 3. Switch-to-Switch Connections

Because Auto MDI-X is disabled, switch-to-switch connections require crossover cables.

| Connection | Interfaces        | Cable     | Reason        |
| ---------- | ----------------- | --------- | ------------- |
| SW1 ↔ SW2  | Fa1/1 ↔ Fa1/1 | Crossover | MDI-X ↔ MDI-X |
| SW5 ↔ SW6  | Fa1/1 ↔ Fa1/1 | Crossover | MDI-X ↔ MDI-X |
| SW1 ↔ SW3  | Fa0/1 ↔ Fa0/1 | Crossover | MDI-X ↔ MDI-X |
| SW2 ↔ SW4  | Fa0/1 ↔ Fa0/1 | Crossover | MDI-X ↔ MDI-X |
| SW5 ↔ SW7  | Fa2/1 ↔ Fa0/1 | Crossover | MDI-X ↔ MDI-X |
| SW6 ↔ SW8  | Fa0/1 ↔ Fa0/1 | Crossover | MDI-X ↔ MDI-X |


## 4. Switch-to-End-Device Connections

| Connection | Cable            | Reason      |
| ---------- | ---------------- | ----------- |
| SW3 ↔ PC1  | Straight-through | MDI-X ↔ MDI |
| SW4 ↔ PC2  | Straight-through | MDI-X ↔ MDI |
| SW7 ↔ PC3  | Straight-through | MDI-X ↔ MDI |
| SW8 ↔ SRV1 | Straight-through | MDI-X ↔ MDI |


# Complete Cable Summary

|  # | Connection                | Cable                       |
| -: | ------------------------- | --------------------------- |
|  1 | R1 Fa0/0 ↔ R2 Fa0/0       | Copper Crossover**        |
|  2 | R1 Gig3/0 ↔ R3 Gig2/0     | **Fiber**                   |
|  3 | R3 Fa0/0 ↔ R4 Fa0/0       | **Fiber**                   |
|  4 | R2 Fa2/1 ↔ SW1 Fa0/1      | **Copper Straight-through** |
|  5 | R2 Fa1/0 ↔ SW2 Fa2/1      | **Copper Straight-through** |
|  6 | R4 Fa1/0 ↔ SW5 Fa2/1      | **Copper Straight-through** |
|  7 | R4 Fa2/0 ↔ SW6 Fa0/1      | **Copper Straight-through** |
|  8 | SW1 Fa1/1 ↔ SW2 Fa1/1     | **Copper Crossover**        |
|  9 | SW5 Fa1/1 ↔ SW6 Fa1/1     | **Copper Crossover**        |
| 10 | SW1 Fa0/1 ↔ SW3 Fa0/1     | **Copper Crossover**        |
| 11 | SW2 Fa0/1 ↔ SW4 Fa0/1     | **Copper Crossover**        |
| 12 | SW5 Fa2/1 ↔ SW7 Fa0/1     | **Copper Crossover**        |
| 13 | SW6 Fa0/1 ↔ SW8 Fa0/1     | **Copper Crossover**        |
| 14 | SW3 ↔ PC1                 | **Copper Straight-through** |
| 15 | SW4 ↔ PC2                 | **Copper Straight-through** |
| 16 | SW7 ↔ PC3                 | **Copper Straight-through** |
| 17 | SW8 ↔ SRV1                | **Copper Straight-through** |

---

# MDI / MDI-X Cheat Sheet

The traditional rule used in this lab is:

MDI ↔ MDI       = Crossover
MDI-X ↔ MDI-X   = Crossover
MDI ↔ MDI-X     = Straight-through

Typical device classification:

Router        = MDI
PC            = MDI
Server        = MDI

Switch        = MDI-X

Therefore:

Router ↔ Router       → Crossover
Router ↔ Switch       → Straight-through
Switch ↔ Switch       → Crossover
PC ↔ Switch           → Straight-through
Server ↔ Switch       → Straight-through


---

# Why Auto MDI-X Matters

Modern Ethernet devices commonly support Auto MDI-X.

Auto MDI-X allows the interface to automatically detect the transmit and receive pairs and adjust accordingly.

As a result, modern devices can often work with either a straight-through or crossover cable.

However, this lab explicitly states:

 Auto MDI-X is disabled or not supported.

Therefore, the cable must be selected correctly according to the traditional MDI/MDI-X rules.

This makes the exercise useful for understanding what happens at the physical Ethernet layer rather than relying on automatic cable detection.

---

# Fiber Connections

Two long-distance router connections use fiber:

### R1 ↔ R3
Distance: 3 km
Cable: Fiber


A 3 km connection is beyond what would normally be appropriate for a basic copper Ethernet connection, so fiber is the appropriate physical medium.

### R3 ↔ R4

Distance: 250 m
Cable: Fiber
The topology specifies a fiber connection for this link as well.

Packet Tracer does not differentiate between single-mode and multimode fiber for this exercise, but in a real network the choice would depend on the required distance, transceivers, and network design.

---

# Troubleshooting

If a link is down, I would troubleshoot it in this order:

## 1. Check the physical cable

Confirm that the cable matches the device types.

For example:

Router ↔ Switch = Straight-through

Switch ↔ Switch = Crossover

when Auto MDI-X is disabled.

## 2. Check the interfaces

On a router:

show ip interface brief

If an interface shows:

administratively down
enable it:

configure terminal
interface <interface>
no shutdown

## 3. Check the switch interface

Use:

show interfaces status

or:

show ip interface brief

## 4. Check the correct ports

Make sure the cable is connected to the interfaces specified by the topology.

## 5. Check the physical layer before troubleshooting IP configuration

A useful troubleshooting sequence is:

Physical cable
      ↓
Correct interface
      ↓
Interface status
      ↓
Data-link configuration
      ↓
IP configuration
      ↓
Routing

---

# What I Learned

This topology demonstrates that choosing a cable is not simply about whether a switch is an access switch or a core switch.

The important question is:
 **What two types of interfaces are being connected?**

For this lab, because Auto MDI-X is disabled:

* Router-to-router requires crossover.
* Router-to-switch requires straight-through.
* Switch-to-switch requires crossover.
* Switch-to-PC requires straight-through.
* Switch-to-server requires straight-through.
* Long-distance links may require fiber.

This distinction helped me understand the relationship between MDI, MDI-X, transmit/receive pairs, and Ethernet cable selection**.


## Skills Demonstrated

* [x] Ethernet cable selection
* [x] MDI/MDI-X understanding
* [x] Straight-through cable identification
* [x] Crossover cable identification
* [x] Fiber selection for long-distance links
* [x] Router-to-router cabling
* [x] Router-to-switch cabling
* [x] Switch-to-switch cabling
* [x] Switch-to-end-device cabling
* [x] Basic physical-layer troubleshooting
* [x] Network topology documentation

