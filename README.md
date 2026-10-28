## Ex. No: 5  VLAN Configuration Using a Managed Switch
Date:
________________________________________
# Objective
To configure Virtual Local Area Networks (VLANs) on a managed switch and verify that hosts within the same VLAN can communicate while others cannot.
________________________________________
# Apparatus/Tools Required
•	Cisco Packet Tracer<br>
•	1 Managed Switch (e.g., 2960)<br>
•	4 PCs<br>
•	Straight-through Ethernet cables<br>
________________________________________
# Network Topology Diagram
Description:<br>
•	PC0 and PC1 are assigned to VLAN 10.<br>
•	PC2 and PC3 are assigned to VLAN 20.<br>
•	All PCs are connected to different ports on the same switch.<br>
<img width="1918" height="1133" alt="Screenshot 2026-10-28 222530" src="https://github.com/user-attachments/assets/41731998-8784-4b6e-b324-06177a1641bf" />

________________________________________
# IP Addressing Table
Device	VLAN	IP Address	Subnet Mask	Port<br>
PC0	10	192.168.10.1	255.255.255.0	FastEthernet0/1<br>
PC1	10	192.168.10.2	255.255.255.0	FastEthernet0/2<br>
PC2	20	192.168.20.1	255.255.255.0	FastEthernet0/3<br>
PC3	20	192.168.20.2	255.255.255.0	FastEthernet0/4<br>
________________________________________
# Procedure
1.	Open Cisco Packet Tracer and add 4 PCs and 1 Switch.<br>
2.	Connect PC0–PC3 to switch ports FastEthernet0/1 to FastEthernet0/4 respectively.<br>
3.	Assign static IP addresses to each PC as per the IP table.<br>
4.	Enter the Switch CLI and create two VLANs:<br>
o	VLAN 10 for PC0 and PC1<br>
o	VLAN 20 for PC2 and PC3<br>
5.	Assign the respective switch ports to their VLANs.<br>
6.	Use the ping command from PC0 to PC1 (should succeed).<br>
7.	Try pinging from PC0 to PC2 (should fail — different VLANs).<br>
________________________________________
# Commands Used (Switch CLI)
bash<br>
CopyEdit<br>
Switch> enable<br>
Switch# configure terminal<br>

Switch(config)# vlan 10<br>
Switch(config-vlan)# name STAFF<br>
Switch(config-vlan)# exit<br>

Switch(config)# vlan 20<br>
Switch(config-vlan)# name STUDENTS<br>
Switch(config-vlan)# exit<br>

Switch(config)# interface range fastethernet0/1 - 2<br>
Switch(config-if-range)# switchport mode access<br>
Switch(config-if-range)# switchport access vlan 10<br>
Switch(config-if-range)# exit<br>

Switch(config)# interface range fastethernet0/3 - 4<br>
Switch(config-if-range)# switchport mode access<br>
Switch(config-if-range)# switchport access vlan 20<br>
Switch(config-if-range)# exit<br>
________________________________________
# Output (Screenshots)
•	VLAN configuration on switch<br>
<img width="1918" height="1137" alt="Screenshot 2026-10-28 222858" src="https://github.com/user-attachments/assets/e65a0fa5-506f-478b-8887-34edad47f9b1" />

•	PC IP settings<br>
<img width="1918" height="1142" alt="Screenshot 2026-10-28 223013" src="https://github.com/user-attachments/assets/6845ae01-b7cb-443e-8678-d862781c14fc" />

<img width="1918" height="1140" alt="Screenshot 2026-10-28 223029" src="https://github.com/user-attachments/assets/1a2ac8a8-9b21-4440-8bca-dbd52baba54a" />


•	Successful ping between PCs in the same VLAN<br>
<img width="1917" height="1137" alt="Screenshot 2026-10-28 210137" src="https://github.com/user-attachments/assets/19273765-da44-4ab1-bb6d-869f06f2a5de" />

•	Failed ping between PCs in different VLANs<br>
<img width="1918" height="1133" alt="Screenshot 2026-10-28 182451" src="https://github.com/user-attachments/assets/91aedf49-e700-46d2-830a-477a7c730cdc" />

________________________________________
# Result
Successfully created and configured VLANs on a managed switch. Verified that only PCs within the same VLAN could communicate with each other.

