# Project 3: Network Fundamentals & Subnetting Lab

## Project Overview

This hands-on project develops foundational networking skills for cybersecurity analysis and cloud security engineering.

The project combines IPv4 addressing, CIDR notation, subnet masks, subnet calculations, Windows network configuration, connectivity testing, and DNS resolution.

Practical observations and calculations are documented in Markdown evidence files. The documentation distinguishes observed results from interpretations and explains the limitations of each test.

**Project status: Core learning activities completed and published. Final repository review in progress.**

## Objectives

- Understand IPv4 addresses, four octets, and the 32-bit address structure.
- Understand binary and decimal notation in IPv4 addressing.
- Interpret CIDR prefixes and subnet masks.
- Calculate network addresses, broadcast addresses, and usable host ranges.
- Calculate host bits and total address capacity.
- Inspect Windows network interfaces and IP configuration.
- Test IP connectivity using ICMP.
- Investigate basic DNS resolution using `nslookup`.
- Explain how network segmentation supports cybersecurity and cloud security.

## Topics and Practical Work

### 1. IPv4 Addressing and Subnetting

Studied IPv4 address structure, CIDR prefixes, subnet masks, host bits, address capacity, block sizes, and subnet boundaries.

Four worked examples demonstrate `/27` and `/26` calculations, including network addresses, usable host ranges, broadcast addresses, and the start of the next subnet.

**Evidence:** [Subnetting Fundamentals](evidence/subnetting_fundamentals.md)

### 2. Windows IP Configuration

Inspected Windows network interfaces, IPv4 addresses, subnet masks, default gateway, DHCP configuration, and DNS server settings. Distinguished the Wi-Fi interface from VirtualBox host-only adapters.

**Evidence:** [Windows IP Configuration](evidence/windows_ip_configuration.md)

### 3. Connectivity Testing

Tested ICMP connectivity to the configured gateway and the public IP address `1.1.1.1`.

The recorded results demonstrate why a failed ping does not, by itself, prove that a device is offline, and why a successful ping does not prove that every network service is available.

**Evidence:** [Connectivity Tests](evidence/connectivity_tests.md)

### 4. DNS Resolution

Inspected the configured DNS server and used `nslookup example.com` to observe the IPv4 and IPv6 addresses returned by the lookup.

The evidence records the observed response and explains what it does and does not establish about DNS operation.

**Evidence:** [DNS Resolution](evidence/dns_resolution.md)

## Project Structure

```text
Project3_Network_Fundamentals_and_Subnetting/
├── README.md
└── evidence/
    ├── connectivity_tests.md
    ├── dns_resolution.md
    ├── subnetting_fundamentals.md
    └── windows_ip_configuration.md
```

## Tools Used

- Windows Command Prompt — IP configuration, connectivity testing, and DNS lookup.
- Git Bash — command-line workflow and project file management.
- Notepad — editing Markdown documentation.
- VirtualBox — virtual networking and host-only network adapters.
- Git — version control and change history.
- GitHub — remote repository and project publication.

## Cybersecurity Relevance

Networking knowledge helps security professionals understand how devices communicate, how IP addressing defines network boundaries, and how DNS supports communication through domain names.

These fundamentals support network troubleshooting, security monitoring, vulnerability management, network segmentation, and cloud network design.

Understanding subnets is particularly useful when reviewing cloud virtual networks, subnets, routing rules, and security boundaries.

## Evidence and Limitations

The evidence files document practical commands, observed results, interpretations, and limitations.

- Network configuration and test results reflect the environment at the time of observation.
- IP addresses and network settings may change when the computer connects to a different network.
- A successful ping or DNS lookup does not establish that all network services are available or secure.
- These exercises are foundational learning activities, not a comprehensive security assessment.
- Subnet calculations assume conventional IPv4 subnets unless an example explicitly states otherwise.

## Current Status

The core learning activities are completed and documented, and the project is published on GitHub.

Completed:
- IPv4 addressing and subnetting fundamentals.
- Worked `/27` and `/26` subnetting examples.
- Windows IP configuration inspection.
- ICMP connectivity testing.
- Basic DNS configuration and resolution investigation.
- Markdown evidence documentation.
- Git version control and GitHub publication.

The final review checks documentation accuracy, repository consistency, and publication status.

## Learning Outcomes

This project develops the ability to interpret basic IPv4 network configuration, calculate subnet boundaries, perform elementary connectivity and DNS checks, and explain the meaning and limitations of observed results.

It provides a foundation for subsequent cybersecurity projects involving vulnerability management, security monitoring, and cloud networking.