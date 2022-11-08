# M.2 SATA Port Reclaimer

**Hello Hackaday readers! This design currently [doesn't work properly](https://media.discordapp.net/attachments/1008400899716157540/1036765121474727976/snapshot_2022.10.31_19.11.49.jpg) due to the way motherboards invert the polarity on M.2 SATA/PCIe combo lanes, something PCIe tolerates but SATA doesn't. I'll be improving the design in the near future to account for that.**

![image](https://user-images.githubusercontent.com/540874/198851059-e040aa39-de31-48e6-ac12-ef1f7b898460.png)

This M.2 2280 M-key card allows you to reclaim SATA ports that your motherboard may have as part of the chipset, but are not broken out to SATA connectors since the chipset shares their pins with the M.2 slot's PCI Express lanes.

Each SATA port is connected to a data lane of the M.2 card, although not all motherboards and M.2 slots support more than one SATA port (lane 0); if you just want one port, this adapter can work, but there are off-the-shelf ones that will also do the job. Read on for compatibility information.

## Ordering

I am not going to be offering assembled boards for the foreseeable future, since shipping from Brazil is too expensive and takes too much paperwork. You can order boards from your PCB vendor of choice (Gerber files are in the `gerbers` directory) and assemble them yourself (no SMD work is required); **make sure the PCB thickness is 0.8mm** and the total size is 22mm x 80mm, and go for ENIG finish if possible for best signal integrity (standard HASL finish is untested).

## Bill of materials

The only BOM item is a vertical through-hole SATA data connector, quantity 1 to 4 according to your needs. I've had success with [**LCSC part C2926857**](https://lcsc.com/product-detail/Card-Edge-Connectors_LOTES-ABA-SAT-010-K15_C2926857.html), though replacements can be [easily found](https://gist.github.com/CRImier/d78ff224db0d781627f211ff5cede573), or even desoldered from a donor board. When considering a replacement, make sure its **retention pins are centered** (aligned with the data pins); some parts have one of the retention pins slightly offset.

## Motherboard support

This adapter is expected to work (i.e. provide access to more than one SATA port) on a **SATA+NVMe M.2 slot** on the following motherboard platforms. Note that actual compatibility is **at your own risk**, since the board or BIOS might not enable normally-unused SATA ports; in my limited testing with the ASUS H170-PLUS D3 (2 SATA ports routed to a single M.2), a drive attached to the second port was not visible in BIOS menus, but it was still initialized by the BIOS and detected by the operating system.

* **Chipsets:**
  * **AMD B550:** Up to 2 ports (0 and 1) from a slot connected to the chipset ("Group 2" - second set of PCIe lanes).
  * **AMD X570, 600 series:** Up to 4 ports from a slot connected to the chipset (combo lanes: [X570](https://www.gamersnexus.net/images/media/2020/amd-chipsets-b550/amd-x570-pcie-lanes.png), [B650](https://images.anandtech.com/doci/17585/SoC_26.png), [X670](https://images.anandtech.com/doci/17585/SoC_25.png)\).
  * **Intel 300/400 series:** Up to 4 ports from a slot connected to the chipset ([HSIO lanes 14-17, 28-21 or 22-25](https://www.intel.com/content/dam/www/public/us/en/documents/datasheets/300-series-chipset-pch-datasheet-vol-1.pdf#page=30)\).
  * **Intel 500/600/700 series:** Up to 4 ports from a slot connected to the chipset ([HSIO lanes 22-25, 26-29](https://edc.intel.com/content/www/us/en/design/ipla/software-development-platforms/client/platforms/alder-lake-desktop/intel-600-series-chipset-family-platform-controller-hub-pch-datasheet-volume/004/intel-600-series-chipset-family-pch/) or (500 only) [30-33](https://cdrdv2.intel.com/v1/dl/getContent/635218)\).
  * **Older stuff:** Some older motherboards which hijack multiple chipset SATA ports for M.2 can make use of this adapter. One example is the aforementioned ASUS H170-PLUS D3, which only exposes 4 of the 6 SATA ports provided by the H170 chipset, with the remaining 2 routed to M.2 slot lanes 0 and 1.
* **CPUs:**
  * **AMD AM4:** Up to 2 ports (0 and 1) from a slot connected to the CPU. Note that most motherboards already expose these (2 SATA ports shared with the CPU M.2 slot), making this adapter redundant.

## Acknowledgements

Huge thanks to [Arya](https://github.com/CRImier) for helping me with the design (using their [nvme_to_dual_ssd](https://github.com/CRImier/MyKiCad/tree/master/Laptop%20mods/nvme_to_dual_ssd) card as a base) and prototyping of this project.
