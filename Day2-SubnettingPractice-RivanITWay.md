Subnet the following: 
Network: 10.0.0.0 /8

Location: Cubao
Host Needed: 4300
Convert into Bits: 2^13=8192
Prefix (NSM subtract): 32-13 = /19 or 255.255.224.0
Octet, i: 3rd, 32i
Subnet: 10.0.32.0 /19
1st Valid IP: 10.0.32.1 /19
Last Vlaid IP: 10.0.64.254 /19
Broadcast: 10.0.63.255 /19
Next Subnet: 10.0.64.0 /19

Location: Cebu
Host Needed: 2500
Convert into Bits: 2^12=4096
Prefix (NSM subtract): 32-12 = /20 or 255.255.240.0
Octet, i: 3rd, 16i
Subnet: 10.0.16.0 /19
1st Valid IP: 10.0.16.1 /20
Last Vlaid IP: 10.0.21.254 /20
Broadcast: 10.0.31.255 /20
Next Subnet: 10.0.32.0 /20

Location: Davao
Host Needed: 450
Convert into Bits: 2^9=512
Prefix (NSM subtract): 32-9 = /23 or 255.255.254.0
Octet, i: 3rd, 2i
Subnet: 10.0.2.0 /23
1st Valid IP: 10.0.2.1 /23
Last Vlaid IP: 10.0.3.254 /23
Broadcast: 10.0.3.255 /23
Next Subnet: 10.0.4.0 /23


Location: Siargao
Host Needed: 220
Convert into Bits: 2^8=256
Prefix (NSM subtract): 32-8 = /23 or 255.255.255.0
Octet, i: 3rd, 1i
Subnet: 10.0.1.0 /24
1st Valid IP: 10.0.1.1 /24
Last Vlaid IP: 10.0.1.254 /24
Broadcast: 10.0.1.255 /24
Next Subnet: 10.0.2.0 /24

# VLSM Subnetting Lab — 10.0.0.0/8

This repository documents the VLSM subnetting design for four branch locations:
**Cubao, Cebu, Davao, and Siargao**.  
All subnets are allocated using **largest → smallest** methodology to prevent overlap.

---

## 📘 Consolidated VLSM Table

| Location | Hosts Needed | Bits | Prefix | Subnet Mask | Octet Increment | Subnet | 1st Valid IP | Last Valid IP | Broadcast | Next Subnet |
|---------|--------------|-------|--------|--------------|------------------|---------|---------------|----------------|------------|--------------|
| **Cubao** | 4300 | 2^13=8192 | /19 | 255.255.224.0 | 3rd, 32i | 10.0.32.0/19 | 10.0.32.1 | 10.0.63.254 | 10.0.63.255 | 10.0.64.0/19 |
| **Cebu** | 2500 | 2^12=4096 | /20 | 255.255.240.0 | 3rd, 16i | 10.0.16.0/20 | 10.0.16.1 | 10.0.31.254 | 10.0.31.255 | 10.0.32.0/20 |
| **Davao** | 450 | 2^9=512 | /23 | 255.255.254.0 | 3rd, 2i | 10.0.2.0/23 | 10.0.2.1 | 10.0.3.254 | 10.0.3.255 | 10.0.4.0/23 |
| **Siargao** | 220 | 2^8=256 | /24 | 255.255.255.0 | 3rd, 1i | 10.0.1.0/24 | 10.0.1.1 | 10.0.1.254 | 10.0.1.255 | 10.0.2.0/24 |

---

## 📊 Sorted-by-Prefix Master Table (Largest → Smallest)

| Prefix | Location | Subnet | Host Capacity | Broadcast |
|--------|-----------|---------|----------------|------------|
| /19 | Cubao | 10.0.32.0/19 | 8192 | 10.0.63.255 |
| /20 | Cebu | 10.0.16.0/20 | 4096 | 10.0.31.255 |
| /23 | Davao | 10.0.2.0/23 | 512 | 10.0.3.255 |
| /24 | Siargao | 10.0.1.0/24 | 256 | 10.0.1.255 |

---

## 🖼 ASCII Network Diagram

















