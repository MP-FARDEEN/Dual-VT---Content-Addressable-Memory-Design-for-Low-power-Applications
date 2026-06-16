# Dual-VT based Content-Addressable-Memory Design for Low power Applications


**OVERVIEW**

This project presents a low-power 8×8 NOR-type Content Addressable Memory (CAM) architecture designed using UMC 65 nm CMOS technology in Cadence Virtuoso. The design combines the Hybrid Self-Controlled Precharge-Free (HSCPF) architecture with a Dual Threshold Voltage (Dual-VT) assignment strategy to reduce leakage power while maintaining high search speed.
The main idea is:
HVT transistors are assigned to the 6T SRAM cross-coupled inverters to suppress static leakage.
LVT transistors are assigned to access and search transistors to achieve faster write and search operations.

**OBJECTIVES**
1. Reduce static leakage power in CAM cells.
2. Improve search speed without sacrificing performance.
3. Optimize the Power-Delay Product (PDP).
4. Develop an energy-efficient CAM architecture suitable for low-power VLSI applications.

**INTRODUCTION**

Content Addressable Memory is a high-speed parallel search hardware that performs comparison between the input search data and the stored data and provides the address corresponding to the matched data [2]. Due to its high-speed search capability CAM is widely used in network routers,
packet classification, image processing and many more. This high throughput parallel search mechanism comes with high power consumption due to the presence of large number of search line and match line circuitry that switch simultaneously during each search operation.

Conventional CAM architectures are broadly classified into NOR-type and NAND-type match line structures . NOR-type CAM offers high search speed due to its short discharge path but suffers from large dynamic power consumption because most match lines discharge during evaluation. On the other hand, NAND-type CAM reduces dynamic powerbut experiences increased search delay and charge-sharing issues due to its series-connected structure. To overcome these limitations, several precharge-free and self-controlled architectures have been proposed. Among them, Hybrid Self- controlled Precharge Free CAM architecture is the latest archi- tecture with less power dissipation, improved performance and reduced area overhead. Although this architecture focused on reducing the dynamic power consumption the leakage power remains a significant concern as we scale down the technology nodes.

Power dissipation in a CAM array has two principal components.Dynamic power arises from the charging and discharging of the match lines, search lines, and internal bit-line nodes during each search cycle. Static power mainly the leakage power that originates mainly from the cross-coupled inverter pair of the 6T SRAM storage cell, which remains permanently biased to retain stored data. Due to its always on state leakage power dissipation dominates causing the overall CAM power
consuming. Several architectural innovations have been proposed to mitigate dynamic power in CAM. Precharge-Free (PF) CAM eliminates the explicit match-line precharge transistor, reducing the capacitive switching energy. The Self-Controlled Precharge-Free (SCPF) architecture adds a self-timed control circuit to further suppress unnecessary match- line transitions. The Hybrid Self-Controlled Precharge-Free (HSCPF) design .combines hybrid control logic with
precharge free circuits to achieve good Power-Delay Product. However,these works treat all transistors within the CAM cell at a single threshold voltage and therefore do not specifically address the leakage component arising from the continuously- on cross coupled inverters.

Multi-threshold voltage design is a well-established technique in standard-cell synthesis, where a cell library offerstransistor of two or more threshold voltages. High-VT (HVT) cells reduce leakage at the cost of speed; Low-VT (LVT) cells provide speed at the cost of leakage. The central insight of the present work is that within a single CAM cell these two requirements that is the cross coupled inverter is a leakage critical block since its always ON while the access transistors and the search transistors are performance critical blocks. This observation motivates a within-cell Dual-VT assignment that applies HVT devices selectively to the latch inverters and LVT devices to the access and search transistors.

**DESIGN METHODOLOGY**

The proposed 8T CAM cell consists of:

6T SRAM storage cell
HVT PMOS: MP1, MP2
HVT NMOS: MN1, MN2
Access transistors
M1, M2 → LVT for faster write operation
Search transistors
M5, M6 → LVT for faster match-line evaluation
<p align="center">
  <img src="Images/8T CAM.png" width="600">
</p>

The architecture is integrated with the HSCPF CAM design, eliminating the conventional match-line precharge phase and reducing dynamic power consumption.
