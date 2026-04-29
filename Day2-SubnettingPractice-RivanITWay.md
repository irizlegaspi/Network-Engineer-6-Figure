
## Accenture - VLSM Subnetting Lab — 10.0.0.0/8

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




## 📘  Teleperformance WFH Host Needed


| Location     | Hosts Needed | Bits           | Prefix | Subnet Mask        | Octet Increment | Subnet            | 1st Valid IP     | Last Valid IP     | Broadcast          | Next Subnet        |
|--------------|--------------|----------------|--------|---------------------|------------------|--------------------|-------------------|--------------------|---------------------|---------------------|
| Makati       | 1500         | 2^11 = 2048    | /21    | 255.255.248.0       | 3rd, 8i          | 172.16.8.0/21      | 172.16.8.1        | 172.16.15.254      | 172.16.15.255       | 172.16.16.0/21      |
| Laguna       | 50           | 2^6 = 64       | /26    | 255.255.255.192     | 4th, 64i         | 172.16.0.64/26     | 172.16.0.65       | 172.16.0.126       | 172.16.0.127        | 172.16.0.128/26     |
| Quezon City  | 12           | 2^4 = 16       | /28    | 255.255.255.240     | 4th, 16i         | 172.16.0.16/28     | 172.16.0.17       | 172.16.0.30        | 172.16.0.31         | 172.16.0.32/28      |





## 📘 TELUS Customer Agents — VLSM Table

| Location | Hosts Needed | Bits           | Prefix | Subnet Mask       | Octet Increment | Subnet        | 1st Valid IP | Last Valid IP | Broadcast      | Next Subnet    |
|----------|--------------|----------------|--------|--------------------|------------------|----------------|---------------|----------------|-----------------|-----------------|
| Makati   | 8500         | 2^13 = 8192    | /19    | 255.255.224.0      | 3rd, 32i         | 10.0.32.0/19   | 10.0.32.1     | 10.0.63.254    | 10.0.63.255     | 10.0.64.0/19    |
| Makati   | 350          | 2^9 = 512      | /23    | 255.255.254.0      | 3rd, 2i          | 10.0.2.0/23    | 10.0.2.1      | 10.0.3.254     | 10.0.3.255      | 10.0.4.0/23     |



## 📘 Subnet Mask Reference Table
| CIDR | 3‑Dot Subnet Mask  | Rivan Format (Octet, i) | Wildcard Mask (ACL/VPN/FW)   |
|------|------------------- |-------------------------|----------------------------- |
| /1   | 128.0.0.0          | 1st, 128i               | 127.255.255.255              |
| /2   | 192.0.0.0          | 1st, 64i                | 63.255.255.255               |
| /3   | 224.0.0.0          | 1st, 32i                | 31.255.255.255               |
| /4   | 240.0.0.0          | 1st, 16i                | 15.255.255.255               |
| /5   | 248.0.0.0          | 1st, 8i                 | 7.255.255.255                |
| /6   | 252.0.0.0          | 1st, 4i                 | 3.255.255.255                |
| /7   | 254.0.0.0          | 1st, 2i                 | 1.255.255.255                |
| /8   | 255.0.0.0          | 1st, 1i                 | 0.255.255.255                |
| /9   | 255.128.0.0        | 2nd, 128i               | 127.63.255.255               |
| /10  | 255.192.0.0        | 2nd, 64i                | 0.63.255.255                 |
| /11  | 255.224.0.0        | 2nd, 32i                | 0.31.255.255                 |
| /12  | 255.240.0.0        | 2nd, 16i                | 0.15.255.255                 |
| /13  | 255.248.0.0        | 2nd, 8i                 | 0.7.255.255                  |
| /14  | 255.252.0.0        | 2nd, 4i                 | 0.3.255.255                  |
| /15  | 255.254.0.0        | 2nd, 2i                 | 0.1.255.255                  |
| /16  | 255.255.0.0        | 2nd, 1i                 | 0.0.255.255                  |
| /17  | 255.255.128.0      | 3rd, 128i               | 0.0.127.255                  |
| /18  | 255.255.192.0      | 3rd, 64i                | 0.0.63.255                   |
| /19  | 255.255.224.0      | 3rd, 32i                | 0.0.31.255                   |
| /20  | 255.255.240.0      | 2nd, 16i                | 0.0.15.255                   |
| /21  | 255.255.248.0      | 3rd, 8i                 | 0.0.7.255                    |
| /22  | 255.255.252.0      | 3rd, 4i                 | 0.0.3.255                    |
| /23  | 255.255.254.0      | 3rd, 2i                 | 0.0.1.255                    |
| /24  | 255.255.255.0      | 3rd, 1i                 | 0.0.0.255                    |
| /25  | 255.255.255.128    | 4th, 128i               | 0.0.0.127                    |
| /26  | 255.255.255.192    | 4th, 64i                | 0.0.0.63                     |
| /27  | 255.255.255.224    | 4th, 32i                | 0.0.0.31                     |
| /28  | 255.255.255.240    | 4th, 16i                | 0.0.0.15                     |
| /29  | 255.255.255.248    | 4th, 8i                 | 0.0.0.7                      |
| /30  | 255.255.255.252    | 4th, 4i                 | 0.0.0.3                      |
| /31  | 255.255.255.254    | 4th, 2i                 | 0.0.0.1                      |
| /32  | 255.255.255.255    | 4th, 1i                 | 0.0.0.0                      |


## Address‑conversion reference (decimal → binary/hex → IPv4/IPv6)

| DEC | BIN-SUM | HEX |
|-----|---------|-----|
| 1   | 0       | 1   |
| 2   | 128     | 2   |
| 3   | 192     | 3   |
| 4   | 224     | 4   | A
| 5   | 240     | 5   | B
| 6   | 248     | 6   | C
| 7   | 252     | 7   | D
| 8   | 254     | 8   | E
| 9   | 255     | 9   | F


| Decimal | IPv4 Range | IPv6 Range |
|---------|------------|------------|
| 0–9     | 0–255      | 0–9, a–f   |

## 7.x.x.x rollover
| Decimal | IPv4             | IPv6  |
|---------|------------------|-------|
| 7999    | 7.255.255.255    | 7FFF  |
| 8000    | 8.0.0.0          | 8000  |
| 8001    | 8.0.0.1          | 8001  |

| Decimal | IPv4             | IPv6  |
|---------|------------------|-------|
| 7898    | 7.254.255.254    | 7EFE  |
| 7899    | 7.254.255.255    | 7EFF  |
| 7900    | 7.255.0.0        | 7F00  |

## 3.x.x.x rollover
| Decimal | IPv4             | IPv6  |
|---------|------------------|-------|
| 3908    | 3.255.0.254      | 3F0E  |
| 3909    | 3.255.0.255      | 3F0F  |
| 3910    | 3.255.1.0        | 3F10  |

## 5.x.x.x rollover

| Decimal | IPv4             | IPv6  |
|---------|------------------|-------|
| 5098    | 5.0.255.254      | 50FE  |
| 5099    | 5.0.255.255      | 50FF  |
| 5100    | 5.1.0.0          | 5100  |


| Decimal | IPv4             | IPv6  |
|---------|------------------|-------|
| 5098    | 5.0.255.254      | 50FE  |
| 5099    | 5.0.255.255      | 50FF  |
| 5100    | 5.1.0.0          | 5100  |


## 2.x.x.x rollover
| Decimal | IPv4             | IPv6  |
|---------|------------------|-------|
| 2899    | 2.254.255.255    | 2EFF  |
| 2900    | 2.255.0.0        | 2F00  |
| 2901    | 2.255.0.1        | 2F01  |




##

255 becomes **FF** and 254 becomes **FE** because IPv6 uses **hexadecimal (base‑16)**, not decimal (base‑10).  
Hex digits go from **0 to F**, where **A–F represent 10–15**.

---

## How the translation actually works

### Hexadecimal digit values  
Hex digits:

```
0 1 2 3 4 5 6 7 8 9 A B C D E F
```

Their decimal equivalents:

```
0–9 = 0–9
A = 10
B = 11
C = 12
D = 13
E = 14
F = 15
```

---

## Why 255 → FF

255 in decimal converted to hex:

1. Divide 255 by 16  
   - 255 ÷ 16 = 15 remainder 15  
2. 15 in hex = **F**  
3. Remainder 15 = **F**

So:

```
255 decimal = FF hex
```

---

## Why 254 → FE

254 ÷ 16 = 15 remainder 14  
- 15 → F  
- 14 → E  

So:

```
254 decimal = FE hex
```

---

## Quick pattern  
Decimal → Hex:

- 255 → **FF**
- 254 → **FE**
- 253 → **FD**
- 252 → **FC**
- 251 → **FB**
- 250 → **FA**
- 249 → **F9**
- 248 → **F8**

This is why your IPv6 column increments like:

```
... F9, FA, FB, FC, FD, FE, FF, 100, 101 ...
```

It’s just a counter in base‑16.

---

If you want, I can show the same conversions in binary so you can see the rollover visually.



Hex and binary line up cleanly because both are **base‑2 systems**, just grouped differently.  
Seeing 254 → **11111110₂** → **FE₁₆** makes the rollover obvious.

---

## Binary → Hex mapping  
Hex digits are just **4‑bit binary chunks**:

```
Binary     Hex
0000       0
0001       1
0010       2
0011       3
0100       4
0101       5
0110       6
0111       7
1000       8
1001       9
1010       A
1011       B
1100       C
1101       D
1110       E
1111       F
```

---

## Why 255 → FF (binary view)

255 decimal:

```
255 = 11111111₂
```

Group into 4‑bit chunks:

```
1111   1111
  F      F
```

So:

```
255₁₀ = FF₁₆
```

---

## Why 254 → FE (binary view)

254 decimal:

```
254 = 11111110₂
```

Group into 4‑bit chunks:

```
1111   1110
  F      E
```

So:

```
254₁₀ = FE₁₆
```

---

## Why the IPv6 counter rolls like this

When your IPv6 column increments:

```
... F9, FA, FB, FC, FD, FE, FF, 100, 101 ...
```

That’s because:

- **F** is the highest hex digit (15)
- After **FF**, the next number is **100** (just like 99 → 100 in decimal)

Binary makes this clear:

```
FF  = 1111 1111
100 = 0001 0000 0000
```

It’s the same rollover behavior as IPv4 octets, just in base‑16 instead of base‑10.

---

If you want, I can show the same rollover using your actual examples (3908, 5099, 5899, etc.) so you can see the binary → IPv4 → IPv6 alignment step by step.




A decimal‑to‑hex conversion always follows the same computation:  
divide by **16**, multiply back, subtract, then translate the remainder into a hex digit.  
Your example for **255 → FF** is correct, and here it is in clean GitHub‑ready format.

---

## Decimal → Hex conversion (step‑by‑step)

```markdown
### Convert 255 (decimal) to hexadecimal

1. Divide by 16  
   255 ÷ 16 = 15 remainder 15

2. Multiply the quotient  
   15 × 16 = 240

3. Subtract  
   255 − 240 = 15

4. Convert remainder to hex  
   15 = F

5. Convert quotient to hex  
   15 = F

### Final:
255 (decimal) = FF (hex)
```

---

If you want, I can add 254 → FE and 253 → FD using the same computation style.


Your breakdown is correct — 255 becomes **FF** and 254 becomes **FE** because the binary groups map cleanly into hexadecimal. Here is your explanation rewritten cleanly in GitHub‑ready format, preserving your exact logic.

---

## Decimal → Binary → Hex (GitHub format)

```markdown
### 255 (decimal → binary → hex)

To Binary:
128 + 64 + 32 + 16 + 8 + 4 + 2 + 1 = 255

Binary grouping (4 bits each):
8 4 2 1   8 4 2 1
1 1 1 1   1 1 1 1

Left 4 bits  = 1111 = 15 = F  
Right 4 bits = 1111 = 15 = F  

**255 → FF**
```

---

```markdown
### 254 (decimal → binary → hex)

To Binary:
128 + 64 + 32 + 16 + 8 + 4 + 2 + 0 = 254

Binary grouping (4 bits each):
8 4 2 1   8 4 2 1
1 1 1 1   1 1 1 0

Left 4 bits  = 1111 = 15 = F  
Right 4 bits = 1110 = 14 = E  

**254 → FE**
```

---

This is the exact reason your IPv6 column increments like:

```
... F9, FA, FB, FC, FD, FE, FF, 100, 101 ...
```

Hex rolls over the same way decimal does — just in base‑16 instead of base‑10.





