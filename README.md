# M.2 SATA Port Reclaimer

![image](https://user-images.githubusercontent.com/540874/198851059-e040aa39-de31-48e6-ac12-ef1f7b898460.png)

This M.2 2280 M-key card allows you to reclaim SATA ports that your motherboard may have as part of the chipset, but are not broken out to SATA connectors since the chipset shares their pins with the M.2 slot's PCI Express lanes.

Each SATA port is connected to a data lane of the M.2 card, although not all motherboards and M.2 slots support more than one SATA port; if you just want one port, there are off-the-shelf M.2 to SATA adapters that will do the job. Read on for compatibility information.

## Motherboard support

This adapter is expected to work (i.e. provide access to more than one SATA port) on **SATA+NVMe M.2 slots** on the following motherboard platforms. Note that actual compatibility is **at your own risk**, since the board or BIOS might not enable normally-unused SATA ports; in my limited testing with the ASUS H170-PLUS D3 (2 SATA ports routed to a single M.2), a drive attached to the second port was not visible in BIOS menus, but it was still initialized by the BIOS and detected by the operating system.

* **Chipsets:**
  * **AMD B550:** Up to 2 ports (0 and 1) from a slot connected to the chipset ("Group 2" - second set of PCIe lanes).
  * **AMD X570, 600 series:** Up to 4 ports from a slot connected to the chipset (combo lanes: [X570](https://www.gamersnexus.net/images/media/2020/amd-chipsets-b550/amd-x570-pcie-lanes.png), [B650](https://images.anandtech.com/doci/17585/SoC_26.png), [X670](https://images.anandtech.com/doci/17585/SoC_25.png)\).
  * **Intel 300/400 series:** Up to 4 ports from a slot connected to the chipset ([HSIO lanes 14-17, 28-21 or 22-25](https://www.intel.com/content/dam/www/public/us/en/documents/datasheets/300-series-chipset-pch-datasheet-vol-1.pdf#page=30)\).
  * **Intel 500/600/700 series:** Up to 4 ports from a slot connected to the chipset ([HSIO lanes 22-25, 26-29](https://edc.intel.com/content/www/us/en/design/ipla/software-development-platforms/client/platforms/alder-lake-desktop/intel-600-series-chipset-family-platform-controller-hub-pch-datasheet-volume/004/intel-600-series-chipset-family-pch/) or (500 only) [30-33](https://cdrdv2.intel.com/v1/dl/getContent/635218)\).
  * **Older stuff:** Some older motherboards which hijack multiple chipset SATA ports for M.2 can make use of this adapter. One example is the aforementioned ASUS H170-PLUS D3, which only exposes 4 of the 6 SATA ports provided by the H170 chipset, with the remaining 2 routed to M.2 slot lanes 0 and 1.
* **CPUs:**
  * **AMD AM4:** Up to 2 ports (0 and 1) from a slot connected to the CPU. Note that most motherboards already expose these (2 SATA ports shared with the CPU M.2 slot), making this adapter redundant.
