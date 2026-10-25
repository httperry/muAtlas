---
title: "μAtlas — New Journal Entries for Macondo"
author: "httperry"
project_url: "https://macondo.hackclub.com/projects/10331"
new_entries_count: 3
new_hours: 20.2
description: "New entries ready to be exported / posted to the Macondo website."
---

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
