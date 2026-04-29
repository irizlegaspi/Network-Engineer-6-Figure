

# ** Instruction: Subnetting host requirements with DHCP results**

| **Name**      | **Hosts Needed** | **Host Bits** | **Prefix** | **Octet / i**    | **Subnet (Yours)**  | **First Valid IP (P)** | **Last Valid IP (B)** | **Broadcast**         | **Next Subnet (Not Yours)** |
|---------------|------------------|---------------|------------|------------------|---------------------|------------------------|-----------------------|-----------------------|---------------------------- |
| **BDO VPN**   | 25               | 5 bits        | /27        | 4th octet, 32i   | 172.16.0.32 /27     | 172.16.0.33 /27        | 172.16.0.62 /27       | 172.16.0.63 /27       | 172.16.0.64 /27             |
| **BPI.COM.PH**| 5000             | 13 bits       | /19        | 3rd octet, 32i   | 172.16.32.0 /19     | 172.16.32.1 /19        | 172.16.63.254 /19     | 172.16.63.255 /19     | 172.16.64.0 /19             |
| **PSBANK**    | 6                | 3 bits        | /29        | 4th octet, 8i    | 172.16.0.8 /29      | 172.16.0.9 /29         | 172.16.0.14 /29       | 172.16.0.15 /29       | 172.16.0.16 /29             |




---

# **DAY 2 — Subnetting by Host Requirements**

---

# **1. BDO VPN — D1, A1, P1**

## **Instruction**
Subnet the following by host requirements.

---

## **BDO VPN Details**
```
VPN: 172.16.0.0/16
Host: 25
VLAN: 2
VLAN NAME: BDO-VPN
```

## **Subnetting Result**
```
Convert to Bits: 5b
32 - 5 = /27
Octet/Increment: 4th, 32i

Subnet:        172.16.0.32/27
1st Valid IP:  172.16.0.33
Last Valid IP: 172.16.0.62
Broadcast:     172.16.0.63
Next Subnet:   172.16.0.64/27
```

---

## **@D1 Configuration**
```bash
conf t
vlan 2
 name BDO-VPN
exit

interface vlan 2
 no shut
 ip add 172.16.0.33 255.255.255.224   # first valid IP
exit

ip dhcp excluded-add 172.16.0.33 172.16.0.37

ip dhcp pool BDO-VPN
 network 172.16.0.32 255.255.255.224   # network address
 default-router 172.16.0.33            # first valid IP
end
```

---

## **@A1 Configuration**
```bash
conf t
interface e0/0
 no shut
 switchport access vlan 2
exit
```

---

## **@P1 Configuration**
```bash
conf t
interface e0/0
 no shut
 ip address dhcp
exit
```

### **Results**
```
Interface                  IP-Address      OK? Method Status  Protocol
Ethernet0/0                172.16.0.38     YES DHCP   up      up
```

---

# **2. BPI VPN — P2, A2, D2**

## **BPI VPN Details**
```
VPN: 172.16.0.0/16
Host: 5000
VLAN: 3
VLAN NAME: BPI-VPN
```

## **Subnetting Result**
```
Convert to Bits: 13b
32 - 13 = /19
Octet/ipasok (Increment): 3rd, 32i

Subnet:        172.16.32.0/19
1st Valid IP:  172.16.32.1
Last Valid IP: 172.16.63.254
Broadcast:     172.16.63.255
Next Subnet:   172.16.64.0/19
```

---

## **@D2 Configuration**
```bash
conf t
vlan 3
 name BPI-VPN
exit

interface vlan 3
 no shut
 ip add 172.16.32.1 255.255.224.0   # first valid IP
exit

ip dhcp excluded-add 172.16.32.1 172.16.32.100

ip dhcp pool BPI-VPN
 network 172.16.32.0 255.255.224.0   # network address
 default-router 172.16.32.1          # 1st usable IP
end
```

---

## **@A2 Configuration**
```bash
conf t
interface e1/0
 no shut
 switchport access vlan 3
exit
```

---

## **@P2 Configuration**
```bash
conf t
interface e1/0
 no shut
 ip address dhcp
exit
```

### **Results**
```
Interface                  IP-Address      OK? Method Status  Protocol
Ethernet1/0                172.16.32.101   YES DHCP   up      up
```

---

# **3. PSBANK VPN — D1, D2, S2**

## **PSBANK VPN Details**
```
VPN: 172.16.0.0/16
Host: 6
VLAN: 4
VLAN NAME: PSBANK-VPN
```

## **Subnetting Result**
```
Convert to Bits: 3b
32 - 3 = /29
Octet/Increment: 4th, 8i

Subnet:        172.16.0.8/29
1st Valid IP:  172.16.0.9
Last Valid IP: 172.16.0.14
Broadcast:     172.16.0.15
Next Subnet:   172.16.0.16/29
```

---

## **@D1 Configuration**
```bash
conf t
vlan 4
 name PSBANK-VPN
exit

interface vlan 4
 no shut
 ip add 172.16.0.9 255.255.255.248   # first valid IP
exit

ip dhcp excluded-add 172.16.0.9 172.16.0.10

ip dhcp pool PSBANK-VPN
 network 172.16.0.8 255.255.255.248   # network address
 default-router 172.16.0.9            # first valid IP
end
```

---

## **@D2 Configuration**
```bash
conf t
interface e1/0
 no shut
 switchport access vlan 4
exit
```

---

## **@S2 Configuration**
```bash
conf t
interface e1/0
 no shut
 ip address dhcp
exit
```

### **Results**
```
Interface                  IP-Address      OK? Method Status  Protocol
Ethernet1/0                172.16.0.11     YES DHCP   up      up
```

