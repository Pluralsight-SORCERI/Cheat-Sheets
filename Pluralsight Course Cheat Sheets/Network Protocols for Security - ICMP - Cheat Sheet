# Network Protocols for Security - HTTP - Cheat Sheet
**Pluralsight Lab:** [Network Protocols for Security: ICMP -- COMING SOON](https://app.pluralsight.com/profile/author/brandon-devault)

## Ping Reference
`ping` command options:

| Flag | Description                                  |
| ---- | -------------------------------------------- |
| -c   | Specifies the number of ICMP packets to send |
| -s   | Specifies the size of the payload            | 

Send 10 large ICMP packets (testing for network throughput and latency):
- `ping -c 10 -s 65507 172.31.24.20`

## tcpdump 
Command Options:
| Flag | Description                           |
| ---- | ------------------------------------- |
| -nn  | No hostname or port resolution        |
| -w   | Write output to file                  |
| -r   | Read in a PCAP file                   |
| -X   | Display HEX and ASCII packet contents |
| -A   | Display only ASCII packet contents    | 

Syntax:
- `tcpdump [OPTIONS] [BPF Filter]`

Capture traffic filtering for ICMP or ARP and write output to PCAP file:
- `sudo tcpdump -nn 'icmp or arp' -w icmp.pcap`

Read a PCAP, filtering on a specific host and printing the packet contents:
- `tcpdump -nn -X -r icmp.pcap 'host 172.31.24.20'

## Wireshark
Display filter for ICMP type 11 (time-to-live exceeded):
- `icmp.type == 11`

Display filter for ICMP Destination and Port Unreachable:
- `icmp.type == 3 && icmp.code == 3`

## Strings
Show printable characters from a file:
- `strings icmp-tunnel.pcap`

Show text with strings at least 15 characters long, filtering out a specific string:
- `strings -n 15 icmp-tunnel.pcap | grep -v "0123456"`
