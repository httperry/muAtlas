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

I added a basic ReadMe to the repo from a template that I use in all my other projects and then I added the project icon, added a good description, and all the files of the work done till now in the GitHub repo

![image](https://cdn.hackclub.com/019ee916-7fda-7a9c-823c-fd7db6c15d4b/Screenshot%202026-06-21%20at%201.00.19%E2%80%AFPM.png)

That's it for today

Adios

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

Hola again,
Today I have been working since the morning and I have finshed adding THe M.2 NVMe E-key port schematic as it is necessary to add any Networking cards in the future

I chose a normal M.2 E-key port on LCSC but I was a bit confused when I tried to find M.2 Ports because why are there so many types of M.2 ports but a little research revealed that each one is made with different task in mind and the ports are for general use and not assigned for any task. At the end I chose `APCI01083-P001A` cause it just works

![image](https://cdn.hackclub.com/019eee49-5dd1-7ed4-a5a8-14a1f83efa61/1.png)

I am going to start on the M.2 M-key slots next and here is the schematic that I made today:

![image](https://cdn.hackclub.com/019eee49-85a3-7c44-88b4-e17a7e1b3683/2.png)

Welp back I go working

Adíos

# 2026-06-22: Nearly Finished M.2 M-key port and thoughts on I/O

**Total time spent: 7.5 hours**

Hi again,
Today I worked on the M.2 M-Key ports and I have nearly finished them I just need to add a few capacitors to stabilize the currents for the NVMe drives. Other than that I also need to figure out how to use the PCIe lanes to add the fast speed USB ports to it. I chose this part for the NVMe M.2 M-Key port: `APCI0107-P001A_C7498140` (C7498140) from LCSC

![image](https://cdn.hackclub.com/019ef018-07d1-7b32-9277-fd8a94480fed/1.png)

I am thinking of using a USB Hub Chip like `UPD720201K8-701-BAC-A` (C355375) to manage the USB 3.0 Ports but I am not sure if this will work because I haven't referred to it's Datasheet yet

Anyways here is the schematic of the M.2 NVMe M-key port I added that is still incomplete:

![image](https://cdn.hackclub.com/019ef018-2473-71d4-8614-b72b921f0d35/2.png)

Back I go working

Adíos

# 2026-06-23: Finished M.2 M-key Ports

**Total time spent: 3 hours**

Buendos Dias amigos,
Today I woke up and I have finished the schematic of the M.2 M-key port I was working yesterday. I have also started researching on the USB Controller and I chose a 3.0 speed one cause LCSC doesn't have any cheap USB 3.2 ones yet

The finished schematics have been uploaded to GitHub and the repository has been updated too:

![image](https://cdn.hackclub.com/019ef221-08e9-7c41-bc83-daf499f143c7/29399.png)

Adios!

# 2026-06-23: Started Schematics for IO and finished a part of it (Ethernet)

**Total time spent: 8 hours**

Halo!
I worked the whole day and finished the schematics of the Ethernet port, I was really confused in this and spent a lot more time than I anticipated on what I thought would be simple

I chose a 2.5G Ethernet Magentics Jack (`RT7-174AAM1A`) which I paired with a Realtek 2.5G Ethernet Controller (`RTL8125BG-CG`), both of their images are provided below. Also the ethernet controller variant available on LCSC was only the one without an internal voltage regulator so I had to add another buck converter to convert 3.3V to 0.9V. LCSC has a very poor avaliability of Ethernet ports greater than 1G, either they are hard to find or they are too expensive! I checked mouser and digikey but outsourcing would be more costlier, Here are the images of the parts I chose:

![image](https://cdn.hackclub.com/019ef4fa-c0d6-74da-adb9-a9ad609317c1/1.png)

![image](https://cdn.hackclub.com/019ef4fa-d5aa-7e1a-8077-668649beab14/2.png)

It was by far the most complex schematic yet in this project and I am eager to work on that big 100+ pins SO-DIMM connector (:pepepray:). Here are the schematics of the Ethernet Connector I finished:

![image](https://cdn.hackclub.com/019ef4fa-eeab-7514-b476-191ef415ed2d/3.png)

I have updated the GitHub with the new schematics and I will probably continue working on the IO Schematics tomorrow 

Adios

# 2026-06-24: Research, Research and... Research

**Total time spent: 4 hours**

Today I dedicate my day for research as I had school in the morning too, not much work done but I figured out that I am left with about 1 PCIe Gen 3 lane that I can use with a USB controller and use USB 3.2 with USB 3.0 Speeds

![image](https://cdn.hackclub.com/019efa8d-f5f3-7bb6-8714-44946889f78b/29588.jpg)

I'm hitting the beds for the day

Adios

# 2026-06-26: Finishing USB Connections - Part 1

**Total time spent: 4 hours**

Hola!
Yesterday I had some school work that I had to finish and I couldn't work on the USB schematics. Till now you may know that we have `2x` USB 3.2 ports and `4x` USB 2.0 Ports in which the USB 2.0 connect directly to the pins of the LattePanda Mu 260-pin Connector, while for the faster speeds of USB 3.2 we need to use a PCIe Lane for the USB ports. We even had an earlier plan of using 2x USB-C ports but I thought that it may not be needed in a Server Environment and it would also save space if we removed that

![image](https://cdn.hackclub.com/019f0488-5edc-758b-837e-47e70383b050/Screenshot%202026-06-26%20at%208.54.27%E2%80%AFPM.png)

Moving forward, I started with the schematics of the USB connections, and managed to route the USB 2.0 connections along with their ESD diodes for static protection and managed to finish the schematics:

![image](https://cdn.hackclub.com/01a16c7c-5539-7b58-8e39-dd8344b28851/Screenshot%202026-10-24%20112655.png)

Imma continue working on the USB 3.2 schematic for now

Adios!

# 2026-06-26: Finishing USB Connections - Part 2

**Total time spent: 7.5 hours**

Hola!

Soo continuing from where I left off, I went ahead with creating the schematics for the USB 3.2 ports and it's controller chip (which took me ages to do :fear:), the ESD diodes for the USB 2.0 ports were a bit easy to route but it was soo confusing to work with the ESD diodes for the 3.2 ports. After that I started routing the USB 3.2 Controller (for which I had to add another buck converter to create a 1.5V rail) and managed to finish it fully. Now ig the whole schematic is done for the USB part

![image](https://cdn.hackclub.com/019f0488-b0b3-79c8-8ecb-1e360fbae0fd/1.png)

For controlling `2x` USB 3.2 Gen 2 Ports we use a single PCIe Gen 3.0 x1 Lane by using a USB Controller - `UPD720201K8-701-BAC-A` (C355375), I mean yeah it needs an external Flash memory chip and also an external voltage regulator for it's internal 1.5V power, but it is the best fit I could find on LCSC that was currently in stock and available 

![image](https://cdn.hackclub.com/019f0488-e771-71f0-b425-3f39f71e8e45/2.png)

I will be continuing on finishing the schematics of the remaining IO connectors tomorrow, which includes the HDMI port, and then we move onto the last stage of the schematics... (*Drumroll.....*) the 260-pin SO-DIMM Connector!

That's it for today, Adios!

# 2026-06-27: Finished Schematics for HDMI Port

**Total time spent: 8 hours**

Hello people,
Today I have a holiday and I am utlilizing it to the fullest, I am currently finished with the HDMI Port Connections and it was quite easier than the rest. Actually the current schematic I have uploaded on GitHub is a revised one as the earlier one was missing a MOSFET chip to control the display during sleep

The chip I chose for this was `TPD12S016RKTR` (C165140) a fair enough chip that also provides support for CEC if the hardware supports it. It is paired with `HDMI-001S` - A simple HDMI-A port that is widely available on LCSC

![image](https://cdn.hackclub.com/019f0987-e3e8-7109-aa69-fe98d35cfbff/1.png)

Now I will move onto the SO-DIMM Connector, which is the most important part of this project... (*Wish me luck*)

Anyways, here is the completed schematic

![image](https://cdn.hackclub.com/019f0987-fb1b-787e-8a59-e38ce6a65f8c/2.png)

Adios

# 2026-06-27: Started Schematic for SO-DIMM Connector

**Total time spent: 8 hours**

Hey there,
I am writing this in hurry as I have to be in bed soon, I have added power lines (19V and GND) to the SO-DIMM slot and I am following the official Pin-Out available in the [LattePanda Mu Pinout XLSX](https://github.com/LattePandaTeam/LattePanda-Mu/blob/main/Electricals/Pinouts/LattePanda_Mu_Edge_Connector_Pinout.xlsx). At first I was shocked to see such a huge pinout then I realized the pinout is divided into different sheets (Like yay for organization but :despair:)

![image](https://cdn.hackclub.com/019f0a2c-7143-770b-933e-d0461464640d/Screenshot%202026-06-27%20at%2011.11.44%E2%80%AFPM.png)

Here is what I have completed and I will be posting new updates tomorrow:

![image](https://cdn.hackclub.com/019f0a2b-f704-715d-8d55-6a6963e00852/Schematic_Atlas_2026-06-27(1).png)

*Note that the schematic is not finished yet, I have just started and thew connections are unpolished*

Adios

# 2026-06-28: Finished Schematics for the SO-DIMM Connector

**Total time spent: 6 hours**

Hey there,
Today I have been working continuously and I managed to finish the SO-DIMM Connector Schematics and I am currently working on the PCB now! (*Yay!*). I also updated the rest of the schematics a bit and polished them and I will be updating the GitHub later

My next Journal will include the list of schematics I updated and also a sneek peek of the PCB board midway completed!

![image](https://cdn.hackclub.com/019f0e22-8a64-7c93-8d5d-79234b494eab/Schematic_Atlas_2026-06-28.png)

![image](https://cdn.hackclub.com/019f0e22-bc14-7985-bec9-bf2ba7521c16/Screenshot%202026-06-28%20at%205.39.37%E2%80%AFPM.png)

Adios!

# 2026-06-29: Finished Power Connection Rails on PCB and started work on PCB

**Total time spent: 8 hours**

Hey there,
I have been working the whole day as today was my holiday and I managed to connect together all the power lines properly, and I am discovering how to make sure there is proper tolerance for the SATA, PCIe, HDMI lines. I also managed to channel the input power into the respective converters and created power rails on the board for 19V for the LattePanda Mu and other 5V and 3.3V rails too

I have also made a few revisions in the schematics as there are few locations where I had accidentally placed capacitors in series where it should have been in parallel (You can see those in the SATA Schematics below, I have capacitors in series for power input)

![image](https://cdn.hackclub.com/01a16c90-b6a3-7c3d-a1dd-832f9d1adc11/Screenshot%202026-10-24%20114915.png)

I started working on the PCB, and managed to move major components inside the board at the loacations I liked, I then started connecting the power connections on the SATA ports and ig the only thing remaining in that is the differentail pairs, moving on I started working on the Ethernet Controller and managed to connect a good chunk of it, yet I haven't connected it to the port. I then connected the switches at the top for controlling the power and reset buttons

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

# 2026-10-14: Finished HDMI connections, fixed many DRC issues, shifted many components from outside the board to inside the board outline :oke:

**Total time spent: 7.2 hours**

Yallo!

So today I started off by continuing my work on resolving the DRC issues on board and I managed to resolve most of them, most of them were the vias being too close to the board edge or connector pads and all, so now the total errors have been dropped to 300 ish ig and most of them are connection issues with unconnected traces. 

![image](https://cdn.hackclub.com/01a15df7-9e19-70b3-baf5-2243e9c37d57/Screenshot%202026-10-21%20154708.png)

Moving on I continued the development on HDMI connections and managed to finish it, routed the differential pairs back to the SODIMM connectors, placed the pull up resistors and coupling caps as near as the controller as possible and rest I moved below the HDMI connector pin :3

![image](https://cdn.hackclub.com/01a15df7-9eca-795b-b123-418ab49c466e/Screenshot%202026-10-21%20154129.png)

Then I started to move all the components from outside the board outline to within the board near their designated components (which was a pain to do with the remaining space available, actually the space is not an issue, the real issue is that below the space there are many traces running through the board so not much space left to add vias :cryin:)

That's it for today

Adios!

# 2026-10-16: Started USB Connections and finished all the power connections on board

**Total time spent: 7 hours**

Yallo!

So today I sat down and fully finished the power connections on board including all the GND pads (which were easily more than 100-200 ig :plankton_pain:) it was a tedious task to sit through and find each one of the power pins on board (I had to use ratlines, for the first time it was useful and painful at the same time)

Then I moved onto the next major thing on board which is the USB connections, amazingly I decided that I wanted to use both USB 3.2 (SuperSpeed) and USB 2.0 on board so I started first with the USB 2.0 which was easier than the rest of the differential pairs ig (hopefully), I also started with the USB 3.2 and ig a few connections are remaining atp

![image](https://cdn.hackclub.com/01a15e2f-fe68-75fb-a181-9f6e2494b6b5/Screenshot%202026-10-21%20164916.png)

That's it for today!

Adios!

# 2026-10-23: Finished work on PCB completely and removed USB 3.2 from the board

**Total time spent: 5 hours**

Yallo!

So today, I sat down and decided to remove the USB 3.2 ports cause it would have taken too much time to route and connect with all the mess on the board, I decided to remove it and continue working on the board properly (ik it's sad but I have too much load on me rn :cryin:) then I started routing the remaining SATA differentail pairs and the USB 2.0 differential pairs on board and pretty much I was done

I then continued to remove the old mounting holes from the board and added new ones of 2mm diameter so that later I can add it in an enclosure

There were a few issues with a few caps in the schematics but I fixed them (near the buttons and in the NVME caps)

Here's the final look:
![image](https://cdn.hackclub.com/01a16c9c-c8a9-70ea-bee4-26d0068c3356/Screenshot%202026-10-24%20120110.png)

![image](https://cdn.hackclub.com/01a16c9c-ca53-7e1b-8919-a65e7ba4ac6d/Screenshot%202026-10-24%20120121.png)

![image](https://cdn.hackclub.com/01a16c9c-cbae-7e75-b46e-945b4f70fdce/Screenshot%202026-10-24%20120139.png)

![image](https://cdn.hackclub.com/01a16c9c-cd64-7e2c-89d3-e2ca1fc14573/Screenshot%202026-10-24%20120157.png)

That's it for now, and I'll update the GitHub for this now

Adios

# 2026-10-26: Finalized the costing and updated GitHub

**Total time spent: 2 hours**

Yallo!

So this journal will be a short one, I just went ahead and got the costing from JLCPCB, then I went ahead and updated my GitHub for the new BOM and edited a few stuff in the ReadMe

Here are the cart screenshots

![image](https://cdn.hackclub.com/01a176a3-a641-797f-a955-7f26d4982e8e/Screenshot%202026-10-26%20104604.png)

![image](https://cdn.hackclub.com/01a176a4-590a-777c-bbe1-6149bb976320/Screenshot%202026-10-26%20104646.png)

That's it for today! signing off with the project

Adios!
