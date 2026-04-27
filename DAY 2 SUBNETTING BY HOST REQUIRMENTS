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
conf t
vlan 2
name BDO-VPN-25WFH
exit
!
int vlan 2
no shut
ip add 172.16.0.33 255.255.255.224
! first Valid IP Address
exit
!
ip dhcp excluded-add 172.16.0.33 172.16.0.37
ip dhcp pool BDO-VPN-25WFH
network 172.16.0.32 255.255.255.224
! network Address
default-router 172.16.0.33
! 1st usable Ip
end


@A1
----------
conf t
int e0/0
no shut
switchport access vlan 2
exit

Do BP

@P1
-----------
conf t
int e0/0
no shut
ip address DHCP
!
Do BP
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
conf t
vlan 3
name BPI-VPN
exit
!
int vlan 3
no shut
ip add 172.16.32.1 255.255.224.0
! first Valid IP Address
exit
!
ip dhcp excluded-add 172.16.32.1 172.16.32.100
ip dhcp pool BPI-VPN
network 172.16.32.0 255.255.224.0
! network Address
default-router 172.16.32.1
! 1st usable Ip
end

@A2
conf t
int e1/0
no shut
switchport access vlan 3
exit

Do BP

@P2
conf t
int e1/0
no shut
ip address DHCP
!
do bp
exit

RESULTS:
-----------------
IT(config)#do bp
Interface                  IP-Address      OK? Method Status                Protocol 
Ethernet1/0                172.16.32.101   YES DHCP   up                    up 




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
conf t
vlan 4
name PSBANK-VPN
exit
!
int vlan 4
no shut
ip add 172.16.0.9 255.255.255.248
! first Valid IP Address
exit
!
ip dhcp excluded-add 172.16.0.9 172.16.0.10
ip dhcp pool PSBANK-VPN
network 172.16.0.8 255.255.255.248
! network Address
default-router 172.16.0.9
! 1st usable Ip
end


@D2
-----------
conf t
int e1/0
no shut
switchport access vlan 4
!
Do BP


@S2
------------
conf t
int e1/0
no shut
ip address DHCP
!
do bp
exit


RESULTS:
-----------------
S2(config-if)#do bp
Interface                  IP-Address      OK? Method Status                Protocol
Ethernet1/0                172.16.0.11     YES DHCP   up                    up 




























