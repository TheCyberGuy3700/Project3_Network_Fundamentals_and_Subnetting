\# Windows IP Configuration Investigation



\## 1. Objective



Inspect the IPv4 network configuration of a Windows computer and identify its IPv4 addresses, subnet masks, network addresses, and default gateway.



This investigation connects IPv4 and subnetting theory to real network configuration evidence.



\## 2. Tool Used



\*\*Tool:\*\* Windows `ipconfig` command



\*\*Purpose:\*\* Displays the computer's IP configuration, including network adapters, IPv4 addresses, subnet masks, and default gateways.



\## 3. Evidence Collection



The command executed was:



```text

ipconfig

```



The output showed three adapters with assigned IPv4 addresses.



| Adapter | IPv4 Address | Subnet Mask | Default Gateway |

|---|---|---|---|

| Ethernet 2 | 192.168.56.1 | 255.255.255.0 | Not listed |

| Ethernet 3 | 192.168.137.1 | 255.255.255.0 | Not listed |

| Wi-Fi | 192.168.52.30 | 255.255.255.0 | 192.168.52.143 |



Two additional wireless-related adapters reported that their media was disconnected.



\## 4. Subnet Mask Analysis



All three adapters with IPv4 addresses displayed the subnet mask:



```text

255.255.255.0

```



This subnet mask is equivalent to the CIDR prefix `/24`.



A `/24` prefix means:

\- 24 bits identify the network portion.

\- 8 bits remain for the host portion.

\- There are 256 total IPv4 addresses in the subnet.

\- Under traditional IPv4 subnetting, 254 addresses are usable by hosts.



\## 5. Wi-Fi Network Calculation



Observed configuration:



```text

IPv4 Address: 192.168.52.30

Subnet Mask:  255.255.255.0

Gateway:      192.168.52.143

```



Calculated from the observed address and subnet mask:



| Item | Result |

|---|---|

| CIDR prefix | /24 |

| Network address | 192.168.52.0 |

| First traditionally usable address | 192.168.52.1 |

| Last traditionally usable address | 192.168.52.254 |

| Broadcast address | 192.168.52.255 |

| Default gateway | 192.168.52.143 |



The Wi-Fi IPv4 address and default gateway are within the same `/24` subnet.



\## 6. Interpretation



The Wi-Fi adapter has an IPv4 address, a subnet mask, and a default gateway. This configuration is consistent with an adapter configured to communicate on a local IPv4 network and route traffic to other networks through its gateway.



Ethernet 2 and Ethernet 3 also have IPv4 addresses but no default gateways displayed in this output. Their addresses are consistent with private or virtual networking arrangements. Their precise purposes have not yet been independently verified.



The `ipconfig` output alone does not prove internet connectivity, identify every device on the network, or establish that a particular adapter is a VirtualBox adapter.



\## 7. Cybersecurity Relevance



Understanding IP addresses, subnet masks, and gateways helps a security analyst:



\- Interpret network configurations during investigations.

\- Identify which subnet an IP address belongs to.

\- Understand whether two addresses are in the same subnet.

\- Troubleshoot network communication problems.

\- Recognize the role of virtual networks in a cybersecurity lab.



\## 8. Evidence Limitations



This investigation records the configuration displayed by `ipconfig`. It does not establish which devices are currently reachable, whether firewall rules permit communication, or whether the network is secure.



Further testing would be needed to verify connectivity and the roles of the individual adapters.



\## 9. Status



\*\*Completed:\*\* Initial Windows IP configuration inspection and `/24` subnet analysis.



\*\*Next step:\*\* Investigate network connectivity and distinguish the Windows host's network adapters from the virtual networks used by the cybersecurity lab.

