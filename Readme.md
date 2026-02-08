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
** What are VLANs ** 
VLANs means Virtual Local are  network On like simple LAN VLANs mainly functions the same so these are mainly virtual network found inside real networks that permit to segment a global network into smaller part and it which commnicate together but does not access to the same services in the global network so VLANs are small virtual networks inside the Big network
** VLANs are generally used in department of industries so we can have a Vlan for the management with ID 100 and another VLAN for the employeers with id 200 **
** Let discuss about the notion of VLAN Trunks,access and Portsecurity ** 

Since Vlan are small virtaul networks the mainly add more security to our networks and more control access to our devices.
So we gonna see to create Vlan  and add security to it also note the concept of using in access mode and trunk mode
** What is access and Trunk mode ?? ** 
Access mode in VLAN means the Vlan will only set up allow data to pass the end-device that is the reason while we talk about access mode while the Trunk mode is from one device of the network to another so from a switch to a Router on an internet device which is not a terminal device by terminal device i means a computer or a phone
** In this exercise we will have 3 switch with a central switch connected to 2 other switch with end of those switch been linked to 2 Pc and the central switch with another Pc ** 
** The network will have 2 VLANS which are VLAN5 and VLAN7 the rest in the lab screenshot **  
