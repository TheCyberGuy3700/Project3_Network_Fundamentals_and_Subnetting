# Project 3: Network Fundamentals & Subnetting Lab

## Project Overview

This hands-on project builds foundational networking knowledge for cybersecurity analysis and cloud security engineering.

The project combines networking concepts, worked subnetting calculations, Windows network configuration, connectivity testing, and DNS resolution. Findings are recorded in Markdown evidence files so that the observations and calculations can be reviewed and explained.

This is a learning project developed through practical exercises. It distinguishes observed results from assumptions and documents the limitations of each test.

## Objectives

- Understand IPv4 addresses, their four octets, and their 32-bit structure.
- Practise converting between decimal and binary notation.
- Interpret CIDR prefixes and subnet masks.
- Calculate network addresses, broadcast addresses, and usable host ranges.
- Understand address capacity and host bits.
- Inspect Windows network interface configuration.
- Test IP connectivity and basic DNS resolution.
- Explain how subnetting and network segmentation support cybersecurity and cloud security.

## Topics and Practical Work

### 1. IPv4 Addressing and Subnetting

- IPv4 address structure and octets.
- Binary and decimal notation.
- CIDR prefixes and subnet masks.
- Network and broadcast addresses.
- Usable host ranges and address capacity.
- Worked `/27` subnetting examples.

Evidence: [`subnetting_fundamentals.md`](evidence/subnetting_fundamentals.md)

### 2. Windows IP Configuration

Inspected Windows network interfaces, IPv4 addresses, subnet masks, and the default gateway. Identified VirtualBox host-only adapters separately from the Wi-Fi interface.

Evidence: [`windows_ip_configuration.md`](evidence/windows_ip_configuration.md)

### 3. Connectivity Testing

Tested ICMP connectivity to the configured gateway and to the public IP address `1.1.1.1`. Recorded the results and documented why a failed ping does not, by itself, prove that a device is offline.

Evidence: [`connectivity_tests.md`](evidence/connectivity_tests.md)

### 4. DNS Resolution

Inspected the configured DNS server and used `nslookup example.com` to observe the IPv4 and IPv6 addresses returned by the DNS lookup.

Evidence: [`dns_resolution.md`](evidence/dns_resolution.md)

## Project Structure

- `README.md` — project overview, objectives, progress, and evidence links.
- `notes/` — networking concepts and learning notes.
- `evidence/` — documented calculations, configurations, and test results.
- `screenshots/` — screenshots supporting the practical work, when available.

## Tools Used

- Windows Command Prompt — network configuration and connectivity commands.
- Git Bash — command-line workflow and project file management.
- Notepad — creating and editing Markdown documentation.
- VirtualBox — virtual networking environment and host-only network adapters.
- Git and GitHub — planned version control and project publication.

## Cybersecurity Relevance

Networking fundamentals help security analysts understand how devices communicate, how IP addresses and subnets define network boundaries, and how DNS supports communication using domain names.

These skills are relevant to network troubleshooting, security monitoring, vulnerability assessment, network segmentation, and cloud network design.

## Evidence and Limitations

The evidence files record the commands used, observed results, interpretations, and limitations.

The connectivity and DNS tests represent observations made at the time of testing. They do not constitute a complete security assessment of the computer or network. A successful ping or DNS lookup does not prove that every network service is available or secure.

## Current Status

**In progress.**

Completed and documented:

- IPv4 and subnetting fundamentals with worked examples.
- Initial Windows IP configuration inspection.
- Gateway and public-IP connectivity tests.
- Basic DNS configuration and resolution investigation.

Remaining work includes reviewing the complete project structure, checking evidence quality, completing further practical subnetting and networking exercises, and preparing the repository for publication.

## Learning Outcomes

The goal is to develop a clear, practical understanding of networking concepts and the ability to explain commands, calculations, results, and limitations during technical interviews.

The project also establishes foundational knowledge for later cybersecurity projects involving vulnerability management, security monitoring, and cloud networking.