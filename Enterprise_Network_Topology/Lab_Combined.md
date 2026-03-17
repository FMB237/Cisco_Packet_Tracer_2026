# Composite Review Lab

The goal of this lab is to reinforce the concepts from Lessons 1–6 described in `Readme.md` by combining them into a single Packet Tracer topology that touches on basic connectivity, VLAN segmentation, router-on-a-stick, STP/PVST tuning, VTP, DHCP, and STP security.

## Topology at a glance (build in Packet Tracer)

1. **Devices**
   - 6x Catalyst switches (S1–S6) plus 1x access-layer switch (S7) for the security segment.
   - 1x router with three FastEthernet interfaces (add adapter if needed for three interfaces).
   - 12x PCs distributed across VLANs (minimum 2 per VLAN) and 1x DHCP server for router-on-a-stick.

2. **Connections**
   - S1–S6 are linked via GigabitEthernet trunks (G0/1) and FA0/23–FA0/24 to enforce redundant paths.
   - The router connects to S2, S4, and S5 using FastEthernet interfaces placed in trunk mode for the router-on-a-stick subinterfaces (Lessons 3 and 5).
   - PCs connect to switch access ports grouped into VLANs (Lesson 2) and a security access switch (S7) sits off one distribution switch with BPDU guard/root guard enabled (Lesson 6).

## VLAN & IP plan (drawn from Lessons 2–5)

| VLAN | Name     | Subnet         | Assigned switches        | Ports (per switch) |
|------|----------|----------------|-------------------------|--------------------|
| 10   | HR       | 10.10.10.0/24  | S1, S2                  | Fa0/1-8            |
| 20   | Finance  | 10.20.20.0/24  | S3, S4                  | Fa0/9-16           |
| 30   | Legal    | 10.30.30.0/24  | S5, S6                  | Fa0/17-24           |
| 40   | Security | 10.40.40.0/24  | S7 (access switch)       | Fa0/1-12           |
| 90   | Mgmt     | 10.90.90.0/28  | Router management VLAN   | Physical interface |


## Step-by-step configuration

1. **Lesson 1 recap – foundation**
   - Document each device name; connect PCs + laptop to switches using straight-through cables.
   - Set a PC IP, mask, and gateway manually to test basic ping; if it works, continue.
   - Use the console to configure switches via `enable`, `conf t`, `interface Gig0/1`, `no shutdown` (Lesson 1 notes).

2. **Lesson 2 – VLAN segmentation & port modes**
   - Create VLANs 10, 20, 30, 40 on every switch; give them descriptive names (`name HR`, etc.).
   - Assign Fa0/1–Fa0/8 to VLAN 10, Fa0/9–Fa0/16 to VLAN 20, Fa0/17–Fa0/24 to VLAN 30 on each respective switch.
   - Configure S7 ports Fa0/1–Fa0/12 as VLAN 40, enable `switchport mode access`, and protect with `switchport port-security` if desired.
   - On uplinks, enable trunking with `switchport mode trunk` and `switchport trunk encapsulation dot1q`.

3. **Lesson 3 & 5 – Router-on-a-stick (multisubinterface)**
   - On the router, create subinterfaces for each VLAN:
     ```
     interface FastEthernet0/0.10
       encapsulation dot1q 10
       ip address 10.10.10.1 255.255.255.0
     interface FastEthernet0/0.20
       encapsulation dot1q 20
       ip address 10.20.20.1 255.255.255.0
     interface FastEthernet0/0.30
       encapsulation dot1q 30
       ip address 10.30.30.1 255.255.255.0
     interface FastEthernet0/0.40
       encapsulation dot1q 40
       ip address 10.40.40.1 255.255.255.0
     ```
   - Enable `ip routing` if not already on.
   - Configure PCs in each VLAN to use the router subinterface as their default gateway.
   - Add a DHCP pool on the router for VLAN 10, 20, 30, 40 (Lesson 5).
     ```
     ip dhcp excluded-address 10.10.10.1 10.10.10.10
     ip dhcp pool VLAN10
       network 10.10.10.0 255.255.255.0
       default-router 10.10.10.1
     ```

4. **Lesson 4 & 4.1 – STP & VTP tuning**
   - Turn on PVST on every switch and set root bridges per VLAN (S1 for VLAN 10, S3 for VLAN 20, S5 for VLAN 30) with `spanning-tree vlan X root primary`.
   - Verify with `show spanning-tree vlan X` and `show interface trunk` to confirm the active paths.
   - Configure VTP: S7 operates as VTP server, all other switches as VTP clients. Use domain `cyber` and password `cyber` from the README sample.

5. **Lesson 6 – STP security**
   - Create the security edge by connecting switch S7 to S4 via Fa0/23 and Fa0/24 trunk ports.
   - On the access ports that connect to PCs (e.g., S7 Fa0/1–Fa0/12), enable `spanning-tree portfast` and `spanning-tree bpduguard enable`.
   - On the trunk ports that face other switches, apply `spanning-tree guard root` to maintain the root placement; this prevents a rogue switch from taking over.
   - Test BPDU Guard by temporarily connecting an unauthorized switch to S7 Fa0/1; the port should automatically shut down. Re-enable with `shutdown`/`no shutdown` as described in Lesson 6.1.

6. **Validation & troubleshooting**
   - Use `ping` between PCs in the same VLAN to prove intra-VLAN connectivity, then between VLANs to verify router-on-a-stick forwarding.
   - Check `show vlan brief` to ensure VLAN membership matches the plan.
   - Use `show ip dhcp binding` on the router to confirm clients receiving leases.
   - For STP visibility, run `show spanning-tree detail` and confirm priorities match the desired root placements.

## Bonus stretch goals

- Add a secondary router that peers with the first using a static route for the management VLAN (Lesson 1 introduction to routing).
- Document every switch command in a text file and copy/paste as suggested in Lesson 5.
- Record two capture streams of traffic between hosts in different VLANs and observe encapsulation.

This lab pulls together the lessons you described: basic device onboarding (Lesson 1), VLAN segmentation and trunking (Lesson 2), router-on-a-stick and DHCP (Lessons 3 & 5), STP/PVST + VTP tuning (Lessons 4 & 4.1), and STP security policies (Lessons 6 & 6.1). Let me know if you want a Packet Tracer (.pkt) template or guidance building it step-by-step.
