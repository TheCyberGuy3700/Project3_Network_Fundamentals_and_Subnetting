# Evidence 01: Subnetting Fundamentals

## 1. Purpose

This document records the IPv4 subnetting concepts and worked calculations completed during Project 3: Network Fundamentals & Subnetting Lab.

The objective is to understand how CIDR prefixes determine network bits, host bits, subnet masks, total addresses, network addresses, broadcast addresses, and usable host ranges.

## 2. IPv4 Address Structure

An IPv4 address contains 32 bits divided into four octets. Each octet contains 8 bits.

Example:

`192.168.1.70/27`

- `192.168.1.70` is the IPv4 address.
- `/27` is the CIDR prefix length.
- 27 bits represent the network portion.
- The remaining 5 bits represent the host portion.

## 3. Calculating Host Bits

Formula:

`Host bits = 32 - CIDR prefix length`

Examples:

- `/24`: `32 - 24 = 8 host bits`
- `/26`: `32 - 26 = 6 host bits`
- `/27`: `32 - 27 = 5 host bits`

## 4. Calculating Total and Usable Addresses

Formula:

`Total addresses = 2^(number of host bits)`

| CIDR prefix | Host bits | Total addresses | Traditionally usable host addresses |
|---|---:|---:|---:|
| `/24` | 8 | 256 | 254 |
| `/26` | 6 | 64 | 62 |
| `/27` | 5 | 32 | 30 |

For an ordinary IPv4 subnet, the network address and broadcast address are generally reserved rather than assigned to individual devices.

## 5. Subnet Masks

| CIDR prefix | Binary value of fourth octet | Subnet mask |
|---|---|---|
| `/24` | `00000000` | `255.255.255.0` |
| `/25` | `10000000` | `255.255.255.128` |
| `/26` | `11000000` | `255.255.255.192` |
| `/27` | `11100000` | `255.255.255.224` |

For `/27`, the first 24 network bits fill the first three octets. Three additional network bits occupy the fourth octet.

The fourth octet in binary is:

`11100000`

Its decimal value is:

`128 + 64 + 32 = 224`

Therefore, the `/27` subnet mask is `255.255.255.224`.

## 6. Calculating Subnet Block Size

For these examples, the block size is calculated using:

`Block size = 256 - value of the subnet mask's changing octet`

For `/27`:

`256 - 224 = 32`

The subnet ranges therefore increase in blocks of 32:

- `.0–.31`
- `.32–.63`
- `.64–.95`
- `.96–.127`
- `.128–.159`

The block containing a device address determines its network and broadcast addresses.

## 7. Worked Example 1: 192.168.1.70/27

### Calculation

- CIDR prefix: `/27`
- Subnet mask: `255.255.255.224`
- Host bits: `32 - 27 = 5`
- Total addresses: `2^5 = 32`
- Block size: `256 - 224 = 32`

The final octet `70` falls within the range `.64–.95`.

### Results

| Address type | Result |
|---|---|
| Network address | `192.168.1.64` |
| First usable address | `192.168.1.65` |
| Example device address | `192.168.1.70` |
| Last usable address | `192.168.1.94` |
| Broadcast address | `192.168.1.95` |

### Conclusion

The device address `192.168.1.70/27` belongs to the subnet `192.168.1.64/27`. The subnet contains 32 total addresses, of which 30 are traditionally usable by devices.

## 8. Worked Example 2: 192.168.1.110/27

### Calculation

- CIDR prefix: `/27`
- Subnet mask: `255.255.255.224`
- Host bits: `32 - 27 = 5`
- Total addresses: `2^5 = 32`
- Block size: `256 - 224 = 32`

The final octet `110` falls within the range `.96–.127`.

### Results

| Address type | Result |
|---|---|
| Network address | `192.168.1.96` |
| First usable address | `192.168.1.97` |
| Example device address | `192.168.1.110` |
| Last usable address | `192.168.1.126` |
| Broadcast address | `192.168.1.127` |

### Conclusion

The device address `192.168.1.110/27` belongs to the subnet `192.168.1.96/27`. The subnet contains 32 total addresses, of which 30 are traditionally usable by devices.

## 9. Why Subnetting Matters in Cybersecurity

Subnetting helps cybersecurity analysts:

- Understand which IP addresses belong to a network.
- Interpret network configurations and traffic.
- Identify network and broadcast addresses during investigations.
- Understand network segmentation and separation of resources.
- Build a foundation for cloud networking and access-control design.

In cloud environments, subnetting supports the organization of resources into IP ranges and helps administrators design controlled communication between network segments.

## 10. Learning Status and Evidence Limitations

The calculations in this document were worked through as learning exercises.

The examples are calculated subnetting exercises, not results from a live network scan or measurements of a physical network.

Further work will include checking network configuration on the Windows PC, completing additional subnetting exercises, and documenting verified practical results.

The project remains in progress.
