<img width="1918" height="1140" alt="Screenshot 2026-10-28 223029" src="https://github.com/user-attachments/assets/127f8d1a-3327-4a2c-b2a5-03784da3486d" />## Ex. No: 5  VLAN Configuration Using a Managed Switch
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
<img width="1918" height="1133" alt="Screenshot 2026-10-28 222530" src="https://github.com/user-attachments/assets/880b57dd-6f87-4617-96e0-ee02806c3bdc" />
<br>
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
<img width="1918" height="1133" alt="Screenshot 2026-10-28 210309" src="https://github.com/user-attachments/assets/c907ed04-b8f7-439e-870d-af4cb2f8a349" />


•	PC IP settings<br>
<img width="1918" height="1142" alt="Screenshot 2026-10-28 223013" src="https://github.com/user-attachments/assets/150d4216-15e9-482f-a13a-cac0b3cd0ffd" />
<img width="1918" height="1140" alt="Screenshot 2026-10-28 223029" src="https://github.com/user-attachments/assets/b44ca65b-8649-44e9-a881-8af978676ceb" />

•	Successful ping between PCs in the same VLAN<br>
<img width="1917" height="1137" alt="Screenshot 2026-10-28 210137" src="https://github.com/user-attachments/assets/c8d34483-dcc6-43d6-8668-52947dd6fb32" />

•	Failed ping between PCs in different VLANs<br>
<img width="1918" height="1133" alt="Screenshot 2026-10-28 182451" src="https://github.com/user-attachments/assets/c608c114-8833-4db5-a750-cf282ebf12f0" />

________________________________________
# Result
Successfully created and configured VLANs on a managed switch. Verified that only PCs within the same VLAN could communicate with each other.

