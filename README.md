## Ex. No: 3  DHCP Configuration Using a Router
Date:30-08-2025
________________________________________
# Objective
To configure a router to automatically assign IP addresses to client PCs using the Dynamic Host Configuration Protocol (DHCP).
________________________________________
# Apparatus/Tools Required
•	Cisco Packet Tracer<br>
•	1 Router<br>
•	1 Switch<br>
•	2 PCs<br>
•	Straight-through Ethernet cables<br>
________________________________________
# Network Topology Diagram
Description:<br>
•	PC0 and PC1 are connected to Switch0.<br>
•	Switch0 is connected to Router0 on FastEthernet0/0.<br>
•	The router acts as a DHCP server for the connected LAN.<br>
(Insert screenshot of your Packet Tracer setup here)<br>
________________________________________
# IP Addressing Table
Device	Interface	IP Address	Subnet Mask<br>
Router0	FastEthernet0/0	192.168.50.1	255.255.255.0<br>
PC0	NIC	DHCP (Auto)	Assigned by DHCP<br>
PC1	NIC	DHCP (Auto)	Assigned by DHCP<br>
DHCP Pool:<br>
•	Network Address: 192.168.50.0<br>
•	Subnet Mask: 255.255.255.0<br>
•	Default Gateway: 192.168.50.1<br>
•	DNS Server: 8.8.8.8<br>
•	Excluded IP Range: 192.168.50.1 to 192.168.50.9<br>
________________________________________
# Procedure
1.	Open Cisco Packet Tracer and add 2 PCs, 1 Switch, and 1 Router.<br>
2.	Connect both PCs to the Switch using straight-through cables.<br>
3.	Connect the Switch to Router0’s FastEthernet0/0.<br>
4.	Assign the IP address 192.168.50.1 to the router’s FastEthernet0/0 interface.<br>
5.	Enable the interface using the no shutdown command.<br>
6.	Configure the router as a DHCP server:<br>
o	Define the DHCP pool with network address, default gateway, and DNS.<br>
o	Exclude gateway and reserved addresses from the pool.<br>
7.	Set both PC0 and PC1 to obtain their IP address via DHCP (auto).<br>
8.	Verify that each PC receives an IP address dynamically.<br>
9.	Use the ping command to test connectivity between the two PCs.<br>
________________________________________
# Commands Used (Router CLI)
bash<br>
CopyEdit<br>
Router> enable<br>
Router# configure terminal<br>
Router(config)# interface fastethernet0/0<br>
Router(config-if)# ip address 192.168.50.1 255.255.255.0<br>
Router(config-if)# no shutdown<br>
Router(config-if)# exit<br>

Router(config)# ip dhcp excluded-address 192.168.50.1 192.168.50.9<br>

Router(config)# ip dhcp pool MYPOOL<br>
Router(dhcp-config)# network 192.168.50.0 255.255.255.0<br>
Router(dhcp-config)# default-router 192.168.50.1<br>
Router(dhcp-config)# dns-server 8.8.8.8<br>
Router(dhcp-config)# exit<br>
________________________________________
# Output (Screenshots)
<img width="3199" height="1681" alt="image" src="https://github.com/user-attachments/assets/67581031-67c4-4c50-aea2-581667519911" />

•	DHCP IP configuration shown in PC0 and PC1<br>
<img width="3199" height="1672" alt="image" src="https://github.com/user-attachments/assets/70d3da64-3073-4c37-b88d-efb944778b40" />
<img width="3199" height="1680" alt="image" src="https://github.com/user-attachments/assets/9aa242b7-0ea9-4d93-95e8-344576912364" />


•	Router configuration screen<br>
<img width="3199" height="1679" alt="image" src="https://github.com/user-attachments/assets/d8d28c99-c26f-438c-84ee-05b862bbc4b6" />

•	Successful ping test between the two PCs<br>
<img width="3199" height="1672" alt="image" src="https://github.com/user-attachments/assets/494ff61c-0d09-453e-950f-3bff930fca17" />
________________________________________
# Result
Successfully configured a DHCP server on the router. PCs were dynamically assigned IP addresses and were able to communicate over the network.
