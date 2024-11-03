# DNS-Query-Packet-Analysis
This repository contains an analysis of a DNS query packet captured from network traffic. The packet is part of a PCAP file that includes a DNS query to www.duckduckgo.com with various details about the Ethernet, IP, and DNS layers.
## Packet Details

- **Frame Length:** 89 bytes
- **Source Ethernet Address:** `ba:db:ee:ff:24:18`
- **Destination Ethernet Address:** `ba:db:ee:ff:24:39`
- **Source IP Address:** `172.16.27.8`
- **Destination IP Address:** `8.8.8.8`
- **Source Port:** 55793 (UDP)
- **Destination Port:** 53 (DNS)
- **Query:** `www.duckduckgo.com`
- **Query Type:** A (Host Address)
- **Protocol:** User Datagram Protocol (UDP)
- **Transaction ID:** 0x6011
- **EDNS0 Options:** Extended RCODE: 0x00, Payload Size: 1472

## Analysis Steps

1. **Network Traffic Capture:**
   - The DNS query packet was captured using Wireshark and is included in the PCAP file.
   - The packet capture contains details about Ethernet, IP, UDP, and DNS layers.

2. **Packet Dissection:**
   - The DNS query was parsed to show details such as:
     - Transaction ID (`0x6011`)
     - Query for the domain `www.duckduckgo.com`
     - DNS flags indicating a standard query (Opcode: 0)
     - No answer or authority records as this is just a query.

3. **DNS Query Breakdown:**
   - The query requests the A record (Host Address) for `www.duckduckgo.com`.
   - The query was sent to the DNS server at `8.8.8.8` (Google's public DNS).

4. **EDNS0 Options:**
   - The packet includes an OPT record for EDNS0, which allows for larger UDP packet sizes and extensions to the DNS protocol.

## Tools Used

- **Wireshark:** For capturing and analyzing the network packet.
- **TShark/Pyshark:** (Optional) Scripts for extracting packet details from the PCAP file.

## Usage

### Viewing the Packet

To view the packet details, you can open the provided `.pcap` file in Wireshark. If you prefer using a command-line tool, you can use `tshark` to extract specific details:

```bash
tshark -r dns_query.pcap -V 
```

## Scripts
``` You can also analyze the DNS query using Python with libraries like pyshark or scapy: import pyshark

capture = pyshark.FileCapture('dns_query.pcap')
for packet in capture:
    print(packet)
```

## File Structure
- **dns_query.pcap** - The packet capture file.
- **README.md** - This readme file with detailed analysis.
- **(Optional)** - Python scripts for further analysis.

