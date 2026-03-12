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
**Note: STP was already running in background in our previous labs**
**While should we configure STP manuaally ?**
As an adminstrator we mainly do this configuration manually to make sure that the main Root switch is always the device with the highest packet translaction capacity in our network by default the root switch will always be expose to a high traffic due to the high number od **ATP** send by other devices on it So this roll can't be given to relatively old devices on the network so this will be mainly the functions of a recent and up-scale device.That is mainly a reason while STP is been set-up manaually.
For STP configuration we need to pick a priority values of the ports inside our network so can have **Primary and Secondaty priority ports** the default value for priority is 32768 and most priority values are been set up to 4096 while the highest priority value is been up to 61440.Here wad the ways the STP works only in a single VLAN network but in some many cases we will have to used mutiple VLAN systems So in this cause we will configure stp on each Vlans in other to always have the fastest connection and packet transfer in the network.
**STP is is sure an old today we can configure PVST(Rapid Spanning Tree protocol)** and also the used of portfast 
Portfast is been applied only to access device like printers and Pcs but that is not somethings needed.

**Now let move on to our spanning tree protocol Lab** 
This lab will have a topology with 6 swicthes,3 Vlans and 10 Pcs interconnnecting the network  so we gonna have VLAN10 with name HR(Human Resources),Vlan 20 (Finance) and Vlan30 (Legal) since we have many vlans we will configurate **PVST** on in our network so that we will get fastest path for our native package transfers.
1. The first we will do is to draw the topology that is mainly seen into the spanning tree folder as the a screenshot image
2. We will change the hostnames of all our swicthes for work.
3. Then we will configure PVST protocol on all our swithes.
4. Let configure Access interfaces VLANs and portfast
**Note Portfast is only applied to devices which are not inside a loop that means mainly end devices like pcs and phones need it Let configure access from port fastethenet range from 1 to 8 for each switches so that we will able to scale our network with machines if needed**
5. The interface form 1 to 8 belongs to VLAN10 from 9 to 16 to VLAN20 and from 17 to 22 to vlan30 and that for all switches
6. Now all this configurations are mained let configure Trunks interfaces So all the Gigabit interface of all the 6 switches will be set up to trunk and also following my configurations we gonna set up all the fastethenrt 23 - 24 to trunkalso.
7. After Configure Root Bridge swithes according to the Diagram for Vlan10 the main Root Bridge Switch is S1 for Vlan20 is S3 and Vlan30 with S5 for this configuaration we need to enter the following command into our switches.
**Spanning-tree vlan 10 root primary
To show the spanning tree process we used the command do show spanning-tree which will show us the actual priority on our spanning tree processes.**
To get that max priority other the default value will be reduce to a root value pushing the priority to it max limit and the default priority for the **Root ID is 32778** In some cases the Bridge ID will be equal to the Root ID
After appling this commands the priority value of our S1  Vlan 10 will reduce to 24586 with Make this Switch the main for managing VLAN10.
Then so for S3 and S5 for Vlan20 and Vlan30 respectively.
8. Let configurate the Ip addresses on Pcs inside manually in our topology and respecting the Vlans sub-networks
9. Ensure all the 6 switches has all the Vms  if not create them manually
10. Try to ping Pcs in the same Vlans if successful the lab is completed if not start checking for the errors in your configuarations and ensure all Trunk interfaces are configure
Personally i Face some errors in my Vlans Packet commnicattion across the Network i will try to correct this errors later.

# Lesson 4.1: Adding VTP configuration to our lesson 4
This lab is mainly a continuation of our previous to implement vtp into it since it will be too long to start again another lab. 
Move on to switch S5 and start our vtp configurations by using the following commands
1. "vtp mode server" note this command is been used of after the configure terminal
2. vtp domain cyber 
3. vtp password cyber
But note i had alreasy added the vlans 
4. Then move on to switch S1 and type the follwing commands **vtp mode client** after**vtp domain cyber** then **vtp pass cyber** This will automatically set up the name of our Vlans to all the machines which will be the client to the S5 switch so that we can easily intertified and browse through our network. This will be done on all of our switches which will be defined as clients.So the goal of this is to make all the switches to know the Vlans inside the network

---

# Lesson 5: Router on a Stick 2 

This lab will clearly be a review of my other Router on a Stick lab sinec in this i will used the  previous knowledge from the other lessons which are mainly  **VTP and STP(Spanning Tree protocol)**.For that let drive into the Router on a stick folder mainly the into lab2 from that folder is this were we gonna find good things.
1. Let first redo the topology.
2. Let start by adding 8 swithes from swicth1 to switch8
3. Then in the middle of the topology add a router and link it to switch2,6 and 7 
4. The swicth most be 2960 cisco switches
5. Link all this switches togeher passing through their Gigaehernet ports using cross-over cables since the devices of the same type
6. To the added router give it a link it fastethernet post with the fa/24 of the switch2,6 and 7 .
**Note:For all this linkage we will need to add another adapter to the router for it to have 3 fastethernet post for linkage**
7. The module name to add on switch 2960 is the **NE-1FE-TX** which will give us and additions fastethernet port.
8. Add Pcs according to the topology of the lab
9. Put our Pcs in various Vlans that we will create 3 vlans mainly Vlan 700,800 and 900 which will all carries pairs of informations about the pcs in them.
10. Let set up hostname and PVST on all the swicthes
11. Also change the hostanme of our router
12. Using notepad we can type all the command we need to enter into our switches architecture so to avoid repetition we will need to enter the command into a simple bloc notes then copy then to each of of our swicthes.
**Note: Port 1 to 8 will be located in VLAN700 for all the swithes while port 9 to 16 will be in VLAN800 and port 17-23 in VLAN900**
13. Set up port fa0/24 as Trunk and all the Gigabits of the switches in trunk also
14. Configurate the Root switches accoring to the diagram 
15. Set up Swithes7 as the VTP Server then all the others as clients.
16. Using a Dhcp server we will then configure ip addresses on the pcs via the router server.
17. When configurating the DHCP do not forget to excluded our 10 fisrt server addresses from the client machines.
18. **Using the commands   ip dhcp excluded-address 10.7.0.0  10.7.0.10 or ip dhcp excluded-address 10.9.0.0 10.9.0.10** depending on the network we want to used.


# Lesson 6 : STP Security
From the previous lessons we learn that STP(Spanning Tree protocol) maintains the loop-free topologies in a redundant L2 network.
**BPDU(Bridge Protocol Data Unit)** message are frames that switches distribute in between themselve.Swithes choose Root Bridge, Designated,and Root ports based on information from BPDUs.
Let consider we have an attack in our network to destroy the network the attacker will only attack to the primary switches since the are the switches which mainly carries the principalment routes for package  transfers.

But We can prevent this attack by using the stategy of the **BPDU guard** which is an addition to STP that was introduce to protect port to which end users connected. This is possible because BPDU messages are only exchange between swithes since if we observe a Pc BPDU will be wrong the there 
To configure BPDU will do that after the spanning portfast it is very simple

We have another method of protection call **Root guard** which will block the port we it realise the package comming is seen to have a greater priority than the current root while BPDU root the port.

**Note  we can configurate Root primary and secondary**


# 6.1 Exercise
Let move on the STP exercise
Inside the STP_Security Folder you will find the lab for this lesson
The lab topology is made up of 5 switches and 3pcs connected as end-devices to the swithces
1. we need to reproduce the topology 
2. connecting our upper swithes using the fa/23 and fa/24 in trunk with the other swithes.
3. Then configure rapid PSVT on all our swithes.
4. Now configure access port interface on the ports used for the connection with the pcs and the **BPDU Guard** this step will mainly be done a switch 3 to 5 do not forget to configurated the spanning-tree portfast
5. Then Configure the Port trunk on all the swithes that is from sw1 ro sw5 so mainly includes port f0/23 ,f0/24  and G0/1 
6. Let Now configurate the Root Bridges let select the SW1 to be the made root switch and lat used the default vlan1 for this operations
7. Then configure root guard on interfacing connected to our access swithces so fa0/23 and fa0/24 so those 2 This is done by using the command **spanning-tree guard root**
8. To test the used of the bpduguard we can add a new switch and try to connect to the switch3 through fa0/1 that port will be block.
9. Then if we want to connect back the pc to switcth since the post is down we need to do a **shutdown first on the port to turn it off then a no shutdown**
10. Now let test the group-guard config in our topology by using trying to configurate the sw3 as root with a lower priority.
11. Used the command **Spanning-tree detail** to shwo the actual priority on sw3
12. **spanning-tree vlan 1 priority 20480**
13. on swicth1 we will find a warning message.
14. **spanning-tree vlan 1 priority 32768**
