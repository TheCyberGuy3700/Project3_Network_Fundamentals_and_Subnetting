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
- `/25`: `32 - 25 = 7 host bits`
- `/26`: `32 - 26 = 6 host bits`
- `/27`: `32 - 27 = 5 host bits`

## 4. Calculating Total and Usable Addresses

Formula:

`Total addresses = 2^(number of host bits)`

For ordinary IPv4 subnets, the traditional usable host count is the total address count minus the network and broadcast addresses.

| CIDR prefix | Host bits | Total addresses | Traditionally usable host addresses |
|---|---:|---:|---:|
| `/24` | 8 | 256 | 254 |
| `/25` | 7 | 128 | 126 |
| `/26` | 6 | 64 | 62 |
| `/27` | 5 | 32 | 30 |

Special-purpose cases, such as `/31` point-to-point links, follow different address-use rules.

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

For `/26`, the fourth octet is:

`11000000`

Its decimal value is:

`128 + 64 = 192`

Therefore, the `/26` subnet mask is `255.255.255.192`.

## 6. Calculating Subnet Block Size

For these examples, the block size is calculated using:

`Block size = 256 - value of the subnet mask's changing octet`

Examples:

- `/26`: `256 - 192 = 64`
- `/27`: `256 - 224 = 32`

For `/27`, the subnet ranges increase in blocks of 32:

- `.0–.31`
- `.32–.63`
- `.64–.95`
- `.96–.127`
- `.128–.159`

For `/26`, the subnet ranges increase in blocks of 64:

- `.0–.63`
- `.64–.127`
- `.128–.191`
- `.192–.255`

The block containing an address determines its network and broadcast addresses.

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

## 9. Worked Example 3: 192.168.10.0/26

### Calculation

- CIDR prefix: `/26`
- Subnet mask: `255.255.255.192`
- Host bits: `32 - 26 = 6`
- Total addresses: `2^6 = 64`
- Block size: `256 - 192 = 64`

The final octet `0` falls within the range `.0–.63`.

### Results

| Address type | Result |
|---|---|
| Network address | `192.168.10.0` |
| First usable address | `192.168.10.1` |
| Example network address | `192.168.10.0` |
| Last usable address | `192.168.10.62` |
| Broadcast address | `192.168.10.63` |
| Next subnet begins | `192.168.10.64` |

### Conclusion

The subnet `192.168.10.0/26` contains 64 total addresses, of which 62 are traditionally usable by devices. The next `/26` subnet begins at `192.168.10.64`.

## 10. Worked Example 4: 192.168.10.77/26

### Calculation

- CIDR prefix: `/26`
- Subnet mask: `255.255.255.192`
- Host bits: `32 - 26 = 6`
- Total addresses: `2^6 = 64`
- Block size: `256 - 192 = 64`

The final octet `77` falls within the range `.64–.127`, because 77 is greater than or equal to 64 and less than 128.

### Results

| Address type | Result |
|---|---|
| Network address | `192.168.10.64` |
| First usable address | `192.168.10.65` |
| Example device address | `192.168.10.77` |
| Last usable address | `192.168.10.126` |
| Broadcast address | `192.168.10.127` |
| Next subnet begins | `192.168.10.128` |

### Conclusion

The device address `192.168.10.77/26` belongs to the subnet `192.168.10.64/26`. The network address is the first address in the block; the broadcast address is the last. The next subnet begins at `192.168.10.128`.

## 11. Why Subnetting Matters in Cybersecurity

Subnetting helps cybersecurity analysts:

- Understand which IP addresses belong to a network.
- Interpret network configurations and traffic.
- Identify network and broadcast addresses during investigations.
- Understand network segmentation and separation of resources.
- Build a foundation for cloud networking and access-control design.

In cloud environments, subnetting supports the organization of resources into IP ranges and helps administrators design controlled communication between network segments.

## 12. Learning Status and Evidence Limitations

The calculations in this document are worked learning exercises. The subnetting examples are calculated results, not results from a live network scan or measurements of a physical network.

The project also includes observations from Windows IP configuration, connectivity tests, and DNS resolution. Those observations reflect the environment and time when each test was performed. Network addresses and results can change when the computer connects to a different network.

Further work includes final review of the evidence, validation of project documentation, and publication of the completed project.

The project remains in progress until the planned practical work and final review are complete.