\# Network Connectivity Tests



\## 1. Objective



Test connectivity from the Windows computer to its observed default gateway and to a public IPv4 address.



The purpose is to compare the two results and understand the limitations of ping-based testing.



\## 2. Test Environment



\- Operating system: Windows

\- Tool: Windows `ping` command, executed from Git Bash

\- Wi-Fi IPv4 address: `192.168.52.30`

\- Subnet mask: `255.255.255.0`

\- Observed default gateway: `192.168.52.143`



\## 3. Test A: Default Gateway



Command:



```text

ping -n 4 192.168.52.143

```



Observed result:



\- Packets sent: 4

\- Replies received: 0

\- Packets lost: 4

\- Packet loss: 100%



Interpretation:



The default gateway did not return ping replies during this test. This result alone does not prove that the gateway is offline or that local network communication is completely unavailable. ICMP traffic may be filtered.



\## 4. Test B: Public IPv4 Address



Command:



```text

ping -n 4 1.1.1.1

```



Observed result:



\- Packets sent: 4

\- Replies received: 4

\- Packets lost: 0

\- Packet loss: 0%

\- Minimum round-trip time: 228 ms

\- Maximum round-trip time: 425 ms

\- Average round-trip time: 312 ms



Interpretation:



All four ping requests received replies from `1.1.1.1`. This confirms that the computer could exchange ICMP echo requests and replies with this public IP address at the time of testing.



It does not establish that every website, application, or internet service is working correctly.



\## 5. Comparison



The gateway test received no replies, while the public IP test received four replies.



This difference demonstrates why a failed ping must be interpreted carefully. A device may not respond to ping while traffic to other destinations still succeeds.



Possible explanations for the gateway result include ICMP filtering or differences in how the network handles local and external traffic. Further testing would be needed to determine the exact cause.



\## 6. Cybersecurity Relevance



Ping testing helps analysts perform basic network troubleshooting and collect initial connectivity evidence.



A security analyst should distinguish observed facts from possible explanations and should not declare a device offline based only on a failed ping.



\## 7. Limitations



These tests provide a small sample of ICMP connectivity at one point in time. They do not test all network protocols, prove that the network is secure, or identify the exact reason for the gateway timeout.



\## 8. Status



\*\*Completed:\*\* Initial gateway and public-IP ping tests.



\*\*Next step:\*\* Perform a DNS resolution test to investigate whether the computer can translate a domain name into an IP address.

