# DNS Resolution Investigation

## 1. Objective

Investigate the Windows computer's DNS configuration and verify whether a domain name can be resolved to IP addresses.

## 2. Tools Used

- `ipconfig /all` — displays detailed Windows network configuration.
- `nslookup example.com` — queries DNS to resolve a domain name to IP addresses.

## 3. DNS Configuration Evidence

The following information was observed in the Windows Wi-Fi adapter configuration:

| Setting | Observed value |
|---|---|
| Wi-Fi IPv4 address | `192.168.149.30` |
| Subnet mask | `255.255.255.0` |
| Default gateway | `192.168.149.200` |
| DHCP server | `192.168.149.200` |
| DNS server | `192.168.149.200` |
| DHCP enabled | Yes |

The Wi-Fi address and gateway belong to the same `/24` IPv4 subnet, `192.168.149.0/24`.

The output also identified two VirtualBox Host-Only Ethernet Adapters, using `192.168.56.1/24` and `192.168.137.1/24`. These are separate from the Wi-Fi interface.

## 4. DNS Lookup Test

Command executed:

`nslookup example.com`

The response identified DNS server address `192.168.149.200` and returned the following addresses for `example.com`:

- IPv4: `172.66.147.243`
- IPv4: `104.20.23.154`
- IPv6: `2606:4700:10::6814:179a`
- IPv6: `2606:4700:10::ac42:93f3`

The response was marked as non-authoritative. This is normal for many recursive DNS lookups and does not, by itself, indicate a problem.

## 5. Findings and Interpretation

1. Windows reports `192.168.149.200` as the configured DNS server.
2. A DNS lookup for `example.com` successfully returned IPv4 and IPv6 addresses.
3. The configured DNS server address is the same as the default gateway and DHCP server address.
4. The available evidence does not independently establish the exact device type or how DNS requests are forwarded upstream.
5. DNS resolution succeeded during the recorded test. This does not guarantee that every domain or internet service is reachable.

## 6. Cybersecurity Relevance

DNS translates human-readable domain names into IP addresses. Security analysts may investigate DNS activity when looking for suspicious domains, phishing infrastructure, malware command-and-control activity, or unusual network behaviour.

Recording the configured DNS server and the observed lookup response establishes a baseline for future network investigations.

## 7. Limitations

This was a basic DNS configuration and name-resolution test. It did not inspect DNS packet contents, validate the authenticity of the returned addresses, or establish whether the DNS service uses encryption.

The results represent observations from the time of testing. Network addresses may change when a DHCP lease is renewed or the network configuration changes.

## 8. Status

- [x] Recorded Windows DNS configuration.
- [x] Performed a DNS lookup for `example.com`.
- [x] Recorded the returned IPv4 and IPv6 addresses.
- [x] Documented findings and limitations.

DNS configuration and basic resolution testing are complete for this stage of Project 3.