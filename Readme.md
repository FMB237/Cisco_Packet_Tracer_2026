# This is my Personal Cisco packet Tracer Course this will be a very long course on the used of Cisco packet and labs

 Hey I'm Fouenang Miguel Bruce the course author and a Fourth Year Network energineering student in Polytechnic Douala
Address:migeuelfouenanf@gmail.com | bfouenang237@gmail.com

Okay to start this course is a beginner friendly course that will accesible to each and everyone which will like to learn modern network energinnering passing through cisco packer tracer
---
# what is cisco packet tracer ??
Cisco packet tracer can be define as the default network simulate software provides by Cisco for beginners to study and practice with their devices 
For each person passing through network energineering cisco tracer is mainly the first software the uses.
---
# But the exist more advance software for network simulations like GNS3 and ENE-NG which can mainly reproduce the behaviour  of modern routers and switch 
But this course is mainly about cisco packet tracer so let start 
Cisco packet tracer can be download from the official cisco website and we mainly need to cisco account for a mode proper use

![cisco Web site link] 

In this course we will have many labs more than 50 downloadable labs will be available to you so keep up .

For those using linux we need to add the cisco packet tracer repository for windows user download the installer file 
Note for people not having netcad accounts the will need to create one for them to be able to downlaod packet tracer.
For the first time launching your cisco packet tracer you will be ask to enter your informations.
---
# Lesson 1 :Introdcution
Cisco packet tracer provide us an interactive GUI where we can interconnect device to create a network by interconnection i means connecting PCs,switch,Routers etc to build a large topology network 
Cisco packet tracer also provides to us a variaty of models and devices which will permit us to simulate differcent type and complex network architectures.

we will add some devices like 1PC, 1Laptop,a router,a switch  and connect them together.This interconnnection will be make using straight cables in real life this cables are simplie ethernet cables
In this lesson connection i mainly used Gigaethernet on the switch and router because this ports where available Link the laptop to the Router using the Rs-232 to the console port of the router.The connection using the console port is mainly defined as the first connection have to be make to a new network equipment so we can access the router using serial connection like using the telent interface.
 

# Port Speed and Types

1. Ethernet : 10Mbps
2. FastEthernet : 100MBps
3. GigabitEthernet : 1Gbps
4. G-GigabitEthernet : 10Gbps

This is a keys concepts all every network energineer most have  
Inside the switch move on to enable mode and connected to our switch in my case it is the Gig0/0 for the router to the Gig0/1 of the swicth and put that interface up  using the command 
1.  enable
2.  configure terminal
3. interface gigabitEthernet 0/0  
4. no shutdown
When using packet tracer we can add small in our lab to recall and note what we are doing is the done by pressing the key "n" in our packet tracer interface.
Let give the address 10.0.0.10 to our client pc which is mainly connnected to our switch Then launch the ping 10.0.0.10 to see how packet are been transfer between the pc and the switch.
Package can also send using package options from the GUI which stimulate the ping
---
# Lesson 2 :VLANs
**What are VLANs** 
VLANs means Virtual Local are  network On like simple LAN VLANs mainly functions the same so these are mainly virtual network found inside real networks that permit to segment a global network into smaller part and it which commnicate together but does not access to the same services in the global network so VLANs are small virtual networks inside the Big network
**VLANs are generally used in department of industries so we can have a Vlan for the management with ID 100 and another VLAN for the employeers with id 200**
**Let discuss about the notion of VLAN Trunks,access and Portsecurity** 

Since Vlan are small virtaul networks the mainly add more security to our networks and more control access to our devices.
So we gonna see to create Vlan  and add security to it also note the concept of using in access mode and trunk mode
** What is access and Trunk mode ?? ** 
Access mode in VLAN means the Vlan will only set up allow data to pass the end-device that is the reason while we talk about access mode while the Trunk mode is from one device of the network to another so from a switch to a Router on an internet device which is not a terminal device by terminal device i means a computer or a phone
*** In this exercise we will have 3 switch with a central switch connected to 2 other switch with end of those switch been linked to 2 Pc and the central switch with another Pc 
 
**The network will have 2 VLANS which are VLAN5 and VLAN7 the rest in the lab screenshot ***  

---
# Lesson 3 : Router-on-sticks
**This is a method that permit to connect togther many Vlans in differcent sub-networks together so that the can share data between them**
The principle of the Router on a stick is mainly from the concept of using a single Router to connect mainly Sub-networks where this sub-networks can be consider as Vlans 
So for this lab we will add a single Router and 4 swithes which we will create 2 Vlans mainly VLAN 100 and VLAN 200 which will have differecnt subnet address that is 192.168.1.0 for Vlan 100 and 192.168.2.0 to VLAN 200 then attach some pcs to this switch and activate the trunk to allow pass the Vlans through the switches and access to the pcs.
**Note:The Trunks we are using are base the 802.1Q encapsulations**
For the rest it will seen in the lab topology and also for this lab DHCP server will configurate for each VLANs
This is type of Lab always make show that all the switches has a Vlan attach to it
From this lab i mainly learn one thing always check weather the interface trunks are been correctly configurated like you want or you will always face errors when setting up DHCP and the packet will not have a route to travel in.
The Command which mainly save me in this lab was the **show interface trunk** command 
---
# Lesson 4 :STP(Spanning Tree Protocol)
When we are in a topology with equipement so switches,routers and pc the swicth mac table is empty that initially what happens but now the switch will start sending packets to all the devices connected to it that is what we called broadcasting and for each device the swicth  will register it mac-address that will make the switch to build it onw mac-address table  base on the devices found inside the network.
For more representaion of the situation move on the spannin tree folder and view the files for explanations.
**Note: The deviec send ARP(Address Resolution Protocol) packet to the swicth ** 

If we have many devices this will become a reel mess up so that is the reason while the STP was created  So what is STP ??
Spanning tree protocol "scans" the network to find all links,making sure the will no loop for switching and this is done by using the **STA(Spanning tree algorithms)**
For that check more the stp pdf inside the Spanning tree folder.In other to all this to function properly all switches should coperate together passing by a point call the **Root Bridge** and the Root Bridge refers to the Root of our treeand so it the central point of linkage betweeen switches inside our network

**Note we can 2 port mode mainly forwarding and blocking**
A root port is an interface that has the cost from a swicth to reach the root switch so the root port can be the shorter and fastest link to reach the root switch.
So STP is made to choose the faster path so if we have a far optics fiber cable,a media fastethernet cable and a far serial cable the **STA will choose the Far optic fiber since it is the fastest**
When the is communication between this ports one port will be blocked and the other will choosen to be root port.



I like continous after