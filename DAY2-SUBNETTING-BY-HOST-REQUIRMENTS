Instruction: Subnet the following by host requirments:


==================================================
BDO VPN - D1, A1, P1
==================================================
VPN: 172.16.0.0 /16
Host: 25
VLAN: 2
VLAN NAME:BDO-VPN
Convert to Bits: 5b
Subtract: 32-5=/27
Octet/i: 4th, 32i
Subnet: 172.16.0.32 /27
1stLast Valid IP: 172.16.0.33 /27
Last Valid IP: 172.16.0.62 /27
Broadcast: 172.16.0.63 /27
Next Subnet: 172.16.0.64 /27


@D1
--------------
D1#conf t
Enter configuration commands, one per line.  End with CNTL/Z.
D1(config)#vlan 4
D1(config-vlan)#name PSBANK-VPN-6H-WFH
D1(config-vlan)#exit
D1(config)#!
D1(config)#int vlan 4
D1(config-if)#no shut
D1(config-if)#ip add 172.16.0.9 255.255.255.248
D1(config-if)#! first Valid IP Address
D1(config-if)#exit
D1(config)#!
D1(config)#ip dhcp excluded-add 172.16.0.9 172.16.0.10
D1(config)#ip dhcp pool PSBANK-VPN
D1(dhcp-config)#network 172.16.0.8 255.255.255.248
D1(dhcp-config)#! network Address
D1(dhcp-config)#default-router 172.16.0.9
D1(dhcp-config)#! 1st usable Ip
D1(dhcp-config)#end


@A1
----------
A1#conf t
Enter configuration commands, one per line.  End with CNTL/Z.
A1(config)#int e0/0
A1(config-if)#no shut
A1(config-if)#switchport access vlan 2
A1(config-if)#exit

@P1
-----------
FINANCE#conf t
Enter configuration commands, one per line.  End with CNTL/Z.
FINANCE(config)#int e0/0
FINANCE(config-if)#no shut
FINANCE(config-if)#ip address DHCP
FINANCE(config-if)#
!
exit

FINANCE(config-if)#do bp
Interface                  IP-Address      OK? Method Status                Protocol
Ethernet0/0                172.16.0.38     YES DHCP   up                    up      




==============================================================
                     BPI VPN - P2, A2, D2
==============================================================
VPN: 172.16.0.0 /16	
HOST: 5000
VLAN: 3
VLAN NAME: BPI-VPN	
Convert to Bits: 13b
Subtract: 32-13=/19
Octet/i: 3rd, 32i
Subnet: 172.16.32.0 /19
1st: 172.16.32.1 /19
Lst: 172.16.63.254 /19
Broadcast: 172.16.63.255 /19
Next Subnet: 172.16.64.0 /19


@D2
------------
D2#conf t
Enter configuration commands, one per line.  End with CNTL/Z.
D2(config)#vlan 3
D2(config-vlan)#name BPI-VPN
D2(config-vlan)#exit
D2(config)#!
D2(config)#int vlan 3
D2(config-if)#no shut
D2(config-if)#ip add 172.16.32.1 255.255.224.0
D2(config-if)#! first Valid IP Address
D2(config-if)#exit
D2(config)#!
D2(config)#ip dhcp excluded-add 172.16.32.1 172.16.32.100
D2(config)#ip dhcp pool BPI-VPN
D2(dhcp-config)#network 172.16.32.0 255.255.224.0
D2(dhcp-config)#! network Address
D2(dhcp-config)#default-router 172.16.32.1
D2(dhcp-config)#! 1st usable Ip
D2(dhcp-config)#end


@A2
-----
A2(config)#int e1/0
A2(config-if)#no shut
A2(config-if)#switchport access vlan 3
A2(config-if)#exit

@P2
----------
IT(config)#int e1/0
IT(config-if)#no shut
IT(config-if)#ip address DHCP
!
IT(config)#do bp
Interface                  IP-Address      OK? Method Status                Protocol
Ethernet1/0                172.16.32.101   YES DHCP   up                    up 
IT(config-if)#exit



==================================================
                PSBANK  D2, S2, D1 
==================================================
VPN: 172.16.0.0 /16
HOST: 6
VLAN: 4
VLAN NAME: PSBANK-VPN
PSBANK 6H / 172.16.0.0 /16		
Convert to Bits: 3b
Subtract: 32-3=/29
Octet/Inc: 4th, 8i
Subnet : 172.16.0.8 /29
1st Valid IP: 172.16.0.9 /29
Last Valid IP: 172.16.0.14 /29
Broadcast: 172.16.0.15 /29
Next Subnet: 172.16.0.16 /29


@D1
---------
D1(config)#vlan 4
D1(config-vlan)#name PSBANK-VPN
D1(config-vlan)#exit
D1(config)#!
D1(config)#int vlan 4
D1(config-if)#no shut
D1(config-if)#ip add 172.16.0.9 255.255.255.248
D1(config-if)#! first Valid IP Address
D1(config-if)#exit
D1(config)#!
D1(config)#ip dhcp excluded-add 172.16.0.9 172.16.0.10
D1(config)#ip dhcp pool PSBANK-VPN
D1(dhcp-config)#network 172.16.0.8 255.255.255.248
D1(dhcp-config)#! network Address
D1(dhcp-config)#default-router 172.16.0.9
D1(dhcp-config)#! 1st usable Ip
D1(dhcp-config)#end


@D2
-----------
D2(config)#int e1/0
D2(config-if)#no shut
D2(config-if)#switchport access vlan 4
D2(config-if)#exit


@S2
------------
S2(config)#int e1/0
S2(config-if)#no shut
S2(config-if)#ip address DHCP
S2(config-if)#!


S2(config-if)#do bp
Interface                  IP-Address      OK? Method Status                Protocol
Ethernet1/0                172.16.0.11     YES DHCP   up                    up 




























