---
title: "μAtlas"
author: "httperry"
description: "A custom carrier board designed to squeeze every ounce of performance out of the LattePanda Mu. Standard motherboards were holding me back, so I built this to be the ultimate micro-server. It’s hardwired to host file and video servers with zero tick-lag and act as a high-speed NAS so I can scrub massive video files directly over the network in DaVinci Resolve. I’ve packed it with dedicated PCIe lanes for an NVMe drive, rock-solid 5GbE networking, and 10Gbps USB 3.2 ports for instant media ingestion. It’s basically a hardcore, custom-built powerhouse packed onto a tiny green square"
created_at: "2026-06-19"
---

# 2026-06-19: Board Research and Resources gathering - #1

**Total time spent: 5 hours**

Hola Amigos,
This is the first journal of this project so I will give you a brief about it first. I am building a carrier board for the new `LattePanda Mu` that utilize the Intel's new chip - `Intel N100` and I am using that to create a home server for storing files and hosting

The `LattePanda Mu` is a SoM (System on Module) board that contains all the required components like RAM, storage, and importantly beautiful implementation of the Intel chip and uses a SO-DIMM form factor to provide us access to it and also exposes upto 9x PCIe lanes

I have been researching a lot and I have 2 Laptop HDDs lying around so I am going to use them, and use ethernet mainly to connect to my network and later if I wish, add a WiFi + Bluetooth card. Till now I have estimated that the whole board will require about 75W of power and to keep a safe margin I assumed that the board requires 90W and I found an AC-DC adapter on Mouser - `GST90A19-P1M`

![image](https://cdn.hackclub.com/019ee07d-f5ae-7a16-817c-81b6c4a0ae67/Screenshot%202026-06-19%20at%208.51.54%E2%80%AFPM.png)

It provides an output of 19V and 4.74A of current. Then I will use a buck converter to efficiently downscale the voltage to 5V for HDDs

I am currently working more on it, and you’ll hear from me soon!

Adíos!

# 2026-06-19: Board Research and Resource Gathering - #2

**Total time spent: 1.5 hours**

It's not been a much of time but I guess I have finalized my IO that I am aiming for the carrier board

The carrier board will have:
1. `1x` M.2 NVMe M-Key Slot (For Additional SSD storage space)
2. `1x` M.2 E-Key Slot (For WiFi and Bluetooth adapters)
3. `2x` 22-Pin SATA Ports (For the Hard Drives)
4. `4x` USB-A 3.2
5. `4x` USB-A 2.0
6. `1x` HDMI-A

Earlier I had landed on a way more advanced configuration (including USB-C ports) but when I referred the LattePanda Mu Website, I saw that it only allows certain configurations to utilize the 9x PCIe Lanes. So according to that I chose 2x Lanes for SATA 3.0 and the rest as PCIe which will be utilized using chips or directly

![image](https://cdn.hackclub.com/019ee0a8-1c3c-7863-b68e-89818b673eb5/Screenshot%202026-06-19%20at%209.42.48%E2%80%AFPM.png)

That's it for today

Adíos

# 2026-06-21: Schematic Diagrams - PWR Management

**Total time spent: 5 hours**

Hola everyone!

Yesterday I was deep into research and went ahead and chose a good buck converter (`AP64500SP-13`) and started with the Power Management Circuitry. It took me quite a while to first figure out the actual power needed by the board and finding the right buck converter to produce as less heat as possible (I just slept over it yesterday)


I used the 19V mains power to feed power to `2x` buck converters to safely convert the voltage from 19V to a 5V rail and a 3.3V rail


I have also added decoupling capacitors to stabilize the voltage and I will be moving onto adding the SATA Connectors first


Here is the schematic drawing of the `PWR Management` circuit
![image](https://cdn.hackclub.com/019ee84b-7e27-7a77-85ca-3f292ed8a411/Schematic_%CE%BCAtlas_2026-06-21.png)

Adíos

# 2026-06-21: Updated and initialized GitHub repository

**Total time spent: 2 hours**

I just initialized and set up the GitHub Repository:
https://github.com/httperry/muAtlas

![image](https://cdn.hackclub.com/019ee916-7fda-7a9c-823c-fd7db6c15d4b/Screenshot%202026-06-21%20at%201.00.19%E2%80%AFPM.png)

That's it

# 2026-06-21: SATA Connectors Schematic Finished & More Exported Formats added on GitHub

**Total time spent: 7 hours**

Hello everyone (whoever is checking the journals),

So today I started with the schematics of the SATA ports which there are going to be 2x on board. I chose a standard `22-Pin` variant port from LCSC - `LD2122F-S0PL6H`

![image](https://cdn.hackclub.com/019eeaa6-ee2c-74f3-b3b1-6c88905e1a37/1.png)

I researched online for the connections I required for the SATA port, then I realized the reference image that I was using was for Mechanical Big Hard-drives (Yes, there are big ones) which included an additional unnecessary 12V rail which wasted a buck converter and needed a 3.3V input too, I then found the correct reference circuit connections and finish it soon

![image](https://cdn.hackclub.com/019eeaa7-074c-750d-be66-0f13ff7b3341/2.jpg)

Hopefully the capacitors I added were sufficient and would work properly with the SATA hard drives and of they caused any issues I can later just yoink them out and bridge the gaps but I am highly skeptical of the capacitors I added on the Data Lines, the reference guide I was following said that they were AC decoupling capacitors, hopefully they do not smooth out the signal even though I used small magnitude ones. Anyways, here is the schematic that I finished today:

![image](https://cdn.hackclub.com/019eeaa7-2fac-7ef7-827a-184737af83a0/3.png)

Welp that drained me for the whole day, I will be updating the GitHub to add more exported file formats for the schematic and hittin the bed

Adíos

# 2026-06-22: NVMe E-Key Port Added

**Total time spent: 7 hours**

Hello everyone,
So today I worked on the M.2 E-Key Slot which I will be using to connect WiFi/Bluetooth cards or Coral TPUs or 4G Networking cards in the future

I chose a normal M.2 E-key port on LCSC but I was a bit confused when I tried to find M.2 Ports because why are there so many types of M.2 ports but a little research revealed that each one is made with different task in mind and the ports are for general use and not assigned for any task. At the end I chose `APCI01083-P001A` cause it just works

![image](https://cdn.hackclub.com/019eee49-5dd1-7ed4-a5a8-14a1f83efa61/1.png)

I am going to start on the M.2 M-key slots next and here is the schematic that I made today:

![image](https://cdn.hackclub.com/019eee49-85a3-7c44-88b4-e17a7e1b3683/2.png)

Welp back I go working

Adíos

# 2026-06-22: Nearly Finished M.2 M-key port and thoughts on I/O

**Total time spent: 7.5 hours**

Hey guys!
So I was working on the M.2 M-key port, for which I chose `APCI0081-P002A` from LCSC. The M.2 M-Key is capable of carrying up to 4x PCIe Gen 3.0 Lanes, but wait does the LattePanda Mu have enough PCIe Lanes for all that?

The LattePanda Mu has 9x PCIe Lanes:
1. 2x PCIe Lanes for SATA (SATA 0 & SATA 1)
2. 1x PCIe Lane for 5G Ethernet Port (RTL8126-CG)
3. 1x PCIe Lane for M.2 E-Key Port
4. 4x PCIe Lanes for M.2 M-Key Port

I am left with 1x PCIe Lane remaining. I also have to add 4x USB 3.0 ports which require USB 3.0 or PCIe lanes, which LattePanda Mu doesn't provide enough. It only provides 2x USB 3.0 ports. For that I can use a PCIe to USB 3.0 Controller chip like `VL805` from VIA Labs which converts 1x PCIe Lane into 4x USB 3.0 Ports! Isn't that cool!?

Here are the schematics that I have done so far for the M.2 M-Key Port:
![image](https://cdn.hackclub.com/019ef06f-1ee4-71cf-8a7e-1a0690060938/Screenshot%202026-06-22%20at%209.38.30%E2%80%AFPM.png)

Adíos!

# 2026-06-23: Finished M.2 M-key Ports

**Total time spent: 3 hours**

Hey there,
I just wrapped up with the M.2 M-key Ports and ready to move onto the next parts of the circuit, which includes:
1. 5G Ethernet Port (Using RTL8126-CG)
2. HDMI Port
3. USB 3.0 Ports (4x USB 3.0 using VL805)
4. USB 2.0 Ports (4x USB 2.0 using FE1.1s)
5. SO-DIMM Connector for the LattePanda Mu

Here is the finished schematic for the M.2 M-Key Port:
![image](https://cdn.hackclub.com/019ef2a2-e64e-72c1-be56-0775a7df427e/Screenshot%202026-06-23%20at%207.08.06%E2%80%AFAM.png)

Adios!

# 2026-06-23: Started Schematics for IO and finished a part of it (Ethernet)

**Total time spent: 10 hours**

Hey there,
So today I started with the Ethernet port and completed its schematic. I was skeptical about what I should use first, so I decided to use `RTL8125BG-CG` which is a 2.5G Ethernet Controller chip, and later I can upgrade it to `RTL8126-CG` which is a 5G Ethernet Controller chip if required.

I will also be using `DG48001 G` as the RJ45 Ethernet Jack with integrated magnetics for simplicity and ease of routing. I found the reference design online and followed it, and here is what I have made till now:

![image](https://cdn.hackclub.com/019ef586-cfdf-74f4-9b3d-1a896f7c32b5/Screenshot%202026-06-23%20at%208.23.00%E2%80%AFPM.png)

Adios!

# 2026-06-24: Research, Research and... Research

**Total time spent: 4 hours**

Hey there,
So today I was mostly researching about the HDMI and USB ports that I have to implement. I have to implement 4x USB 3.0 ports, 4x USB 2.0 ports and 1x HDMI Port.

For the USB 3.0 ports, I will be using `VL805` from VIA Labs which will convert 1x PCIe Lane into 4x USB 3.0 Ports. For the USB 2.0 ports, I will be using `FE1.1s` which will convert 1x USB 2.0 Port into 4x USB 2.0 Ports.

I was also looking into the HDMI Port implementation and I found that I can directly route the HDMI signals from the LattePanda Mu to the HDMI Port with proper ESD Protection and Level Shifters.

Adios!

# 2026-06-26: Finished all USB Connectors

**Total time spent: 14 hours**

Hey there,
Today was a very productive day as I spent 14 hours and finished all the USB Connectors and their schematics!

I finished:
1. `4x` USB 3.0 Ports using `VL805-Q6`
2. `4x` USB 2.0 Ports using `FE1.1s`

I also added proper ESD Protection for all the USB ports and power switches to provide up to 2A per port safely without frying the board if something shorts out.

Here are the schematics:

![image](https://cdn.hackclub.com/019f03c4-4bf8-71e1-9ea6-848e3e4a3aa8/Screenshot%202026-06-26%20at%208.54.49%E2%80%AFPM.png)

![image](https://cdn.hackclub.com/019f03c4-a035-777e-a0bf-650a3cf128ec/Screenshot%202026-06-26%20at%208.55.12%E2%80%AFPM.png)

Adios!

# 2026-06-27: Finished Schematics for HDMI Port

**Total time spent: 8 hours**

Hey there,
Today I finished the HDMI Port schematics. The LattePanda Mu provides DDI (Digital Display Interface) signals which can be directly converted into HDMI 2.0 signals using proper level shifting and ESD protection.

I chose `AZ1065-06F` for high-speed ESD protection on TMDS lines and a standard HDMI Type-A connector.

Here is the completed schematic for the HDMI Port:

![image](https://cdn.hackclub.com/019f0907-8850-7f28-9759-4556488d575c/Screenshot%202026-06-27%20at%208.12.01%E2%80%AFPM.png)

Adios!

# 2026-06-27: Started Schematic for SO-DIMM Connector

**Total time spent: 8 hours**

Hey there,
Today I started working on the most crucial part of the whole board: the 260-Pin SO-DIMM connector for the LattePanda Mu SoM itself!

It took hours just to map all the pins, group them by interfaces (PCIe, Power, DDI, SATA, USB, GPIOs, Control Signals), and verify them against the LattePanda Mu pinout documentation.

Here is the progress on the SO-DIMM connector:

![image](https://cdn.hackclub.com/019f09ad-16df-7f9a-9e12-d81238479e82/Screenshot%202026-06-27%20at%2011.11.45%E2%80%AFPM.png)

Adios!

# 2026-06-28: Finished Schematics for the SO-DIMM Connector

**Total time spent: 6 hours**

Hey there,
Today I have been working continuously and I managed to finish the SO-DIMM Connector Schematics and I am currently working on the PCB now! (*Yay!*). I also updated the rest of the schematics a bit and polished them and I will be updating the GitHub later

My next Journal will include the list of schematics I updated and also a sneek peek of the PCB board midway completed!

![image](https://cdn.hackclub.com/019f0e22-8a64-7c93-8d5d-79234b494eab/Schematic_Atlas_2026-06-28.png)

![image](https://cdn.hackclub.com/019f0e22-bc14-7985-bec9-bf2ba7521c16/Screenshot%202026-06-28%20at%205.39.37%E2%80%AFPM.png)

Adios!

# 2026-06-29: Finished Power Connection Rails on PCB

**Total time spent: 11.5 hours**

Hey there,
I have been working the whole day as today was my holiday and I managed to connect together all the power lines properly, and I am discovering how to make sure there is proper tolerance for the SATA, PCIe, HDMI lines. I also managed to channel the input power into the respective converters and created power rails on the board for 19V for the LattePanda Mu and other 5V and 3.3V rails too

I have also made a few revisions in the schematics as there are few locations where I had accidentally placed capacitors in series where it should have been in parallel (You can see those in the SATA Schematics below, I have capacitors in series for power input)

This is how the PCB looks now:

![image](https://cdn.hackclub.com/019f1433-0171-7e84-9b71-7db8cc76d285/Screenshot%202026-06-29%20at%209.52.05%E2%80%AFPM.png)

![image](https://cdn.hackclub.com/019f1433-7f42-7c2e-8f3a-4d25a4750791/Screenshot%202026-06-29%20at%209.55.43%E2%80%AFPM.png)

![image](https://cdn.hackclub.com/019f1433-c383-77c8-ad88-af2a721c8e4c/Screenshot%202026-06-29%20at%209.56.00%E2%80%AFPM.png)

The PCB is also going to be of 6 Layers at minimum, I will see if I need more layers, and most probably I may need to upgrade it to 8 layers, like I can manage somehow to make it possible in 6 layers but that will be micromanaging

That's it for today and I may not be able to post any entries as my school exams are coming close, I will try my best to balance the work but ggs

Adios!

# 2026-10-12: Finished Ethernet Controller Connections and started work on HDMI port

**Total time spent: 6 hours**

Yallo!

I picked up this project back after soo many months atp :cryin:

So today I started my work by completing the left over connections of the Ethernet controller, and even managed to route back the PCIe transmit and receive differential pairs back to the LattePanda Mu SODIMM connector, while making sure to place the 0.1μF AC coupling capacitors right next to the driver to prevent DC offsets, I haven't done the differential pair length tuning part but I'll do that at the end :oke:

Moving on I started routing the HDMI port and it's controller chip (I heard this is the hardest thing to do in the PCB :prayer:) and managed to connect the TMDS/FRL clock and data pairs (D0, D1, D2) between the controller and the connector. The only problem I had over there was that there wasn’t enough space to place the pull up resistors and the decoupling capacitors… but sumhow I managed to cram it together (That’ll come to bite me back soon…) :uuh:

I then dared to even open up the DRC… Let’s just say…. goddayum. THERE WERE 1200+ ERRORS, most of which were due to incorrectly setting the DRC rules, which I then fixed by putting the correct values allowed for manufacturing by JLCPCB and it reduced by half but still about 500 issues :ok-cry:

I’ll get down to fix those first thing tomorrow, that’s it for today

Also I shifted my project to EasyEDA Pro from the standard edition because it was so bad at differential pair routing for advanced boards, so basically an upgrade of tools :oke: (Man slack emojis should be allowed to be added to journals)

Here’s how the board looks now with the changes near the Ethernet controller region

![image](https://cdn.hackclub.com/01a15902-0ad1-718d-aca5-c9bfbd3013fe/Screenshot%202026-10-20%20at%204.24.49%E2%80%AFPM.png)

![image](https://cdn.hackclub.com/01a15902-09c6-7236-9c5c-db39b7fddaed/Screenshot%202026-10-20%20at%204.25.06%E2%80%AFPM.png)

Adios!
