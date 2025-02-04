# 5GC power consumption data
This respository contains power consumption measurements of open-source 5G Core Networks deployments.

## Our works
* A. Bellin, M. Centenaro and F. Granelli, "A Preliminary Study on the Power Consumption of Virtualized Edge 5G Core Networks," 2023 IEEE 9th International Conference on Network Softwarization (NetSoft), Madrid, Spain, 2023, pp. 420-425, doi: 10.1109/NetSoft57336.2023.10175489.
* A. Bellin, F. Granelli, and D. Munaretto, "A measurement-based approach to analyze the power consumption of the softwarized 5G core," Computer Networks, vol. 244, p. 110 312, 2024, doi: 10.1016/j.comnet.2024.110312.

Please cite our published papers if you intend on using the data in this repository

## Testbed
The testbed used to gather the data comprises 5 Intel NUC units, the 3 used for the 5GC deployments have the following specifications: 
- i5-7260U processor @2.20GHz
- 8GB of RAM
- 240GB SSD
- 1 Gigabit Ethernet and Dual Band Wireless connectivity
- Ubuntu 20.04 Desktop OS

<!-- end of the list -->

We also used the follwoing software:
- [Open5GS](https://open5gs.org/)
- [Free5GC](https://free5gc.org/)
- [UERANSIM](https://github.com/aligungr/UERANSIM)
- [Redis](https://redis.io/)
- [Scaphandre](https://github.com/hubblo-org/scaphandre)
- Iperf3

<!-- end of the list -->

The power consumption data is gathered using both hardware-based (Meross MSS310 smart-plugs) and software-based (Scaphandre) power meters.

<p align="center">
  <img width="600" src="https://github.com/IncludeArthur/power-consumption-data/assets/44785274/6fa210b5-d047-44c0-8432-f27085b44e5c">
</p>

## Data structure
The data is subdivided between Scaphandre measurements and smart-plug measurements.\
Each category is then subdivided between data gathered while using Open5GS and Free5GC.\
Open5GS has been tested with three alternative virtualization options:
- Virtual Machine (VM)
- Bare Metal (BM)
- Docker Containers (CO)

<!-- end of the list -->

Free5GC has been tested only on bare metal.

All data is stored in JSON file format. Each file contains the data for a specific data-plane throughput level specified in the filename.

In the Scaphandre collection we saved the output of the [JSON exporter](https://hubblo-org.github.io/scaphandre-documentation/references/exporter-json.html) without further processing.

For the smart-plug collection, other than *power* data, the files also include *thorughput* and *cpu load* metrics collected using the psutil Python library.
We also include the timestamp for each data sample.
