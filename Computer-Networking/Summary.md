# Summary of Computer Networking

## Physical Layer
- Protocol: 10 Base T, 802.11 (Wifi)
- Protocol Unit Data: Bits
- Addressing: n/a
- Devices: Cables (copper/fiber)
	- Copper twisted pair cables: Cat5, Cat5e, Cat6; problem: crosstalk (RJ45)
	- Fiber: optical fibers
	- Hub (for LAN)
- Technology:
	- Modulation;
	- Duplexing;

## Data-link Layer
- Protocols: Ethernet, Wi-Fi
- Protocol Unit Data: Frames
	- Preamble (8 bytes)
	- Destination address (6)
	- Source address (6)
	- Tag (4)
	- Ether-type (2)
	- Payload (0-1500)
	- FCS (4): CRC
- Addressing: MAC address (48 bits, 6 x 2 hex)
	- First three octets (24 Bits): OUI (Organizationally Unique Identifier)
	- NIC Vendor assigned: 24 bits
- Devices: switch (for LAN)
- Technology:
	- CSMA/CD: whether communications channels are clear, free to transmit data
	- Unicast
	- Broadcast (Ethernet FF:FF:FF:FF:FF:FF)

## Network Layer
- Protocols: IP, ARP, DHCP
- Protocol Unit Data: Datagram
- Addressing: IP address (4 bytes)
	- IP addresses belong to networks, not to devices attached to the network
- Devices:
	- Router
	- Home router: home devices to ISP;
	- Core router (BGP, routers share data with each other)
- Technology:
	- NAT
	- ARP (Address Resolution Protocol)
	- Dynamic Host Configuration Protocol: assign IP to networks

## Transport Layer
- Protocols: TCP/UDP (Transmission Control Protocol/ User Datagram Protocol)
- Protocol Unit Data: Segment
- Addressing: Port (80 for http)

## Application Layer
- Protocols (many): http/smtp/DHCP...
- Protocol Unit Data: messages
- Addressing: n/a
- In OSI 7 layer, including presentation layer

## Devices
- Hub (now replaced by switch?)
- Switch
- Router
- Gateway

## Concepts
- NAT (Network Address Translation):
	- IP masquerading (One-to-Many NAT, Hide IP of the computer, seems that the data is from the router)
- IANA: distributes IPs
- VPN
- Proxy
- DNS
- **ping**: send a special typle of ICMP message called Echo Request (ping 8.8.8.8)
	- Send back a reply
- **TraceRoute** (traceroute google.com)
- **netcat** (nc google.com 80)
- **nslookup** for **DNS** (nslookup twitter.com)
- Cloud

## Connect to Internet
- Telephone: Modem (modulator/demodulator)
- Broadband
	- T-carrier technologies;
	- DSL (digital subscriber line): ADSL, SDSL
	- Fiber connections
- WAN (Wide Area Network)
- Point-to-Point
- Wireless Network
	- Protocols: 802.11 (802.11a, b, g, ac), on physical + datalink layer
	- 2.4 GHz to 5 GHz
	- wireless access point
	- 4 addresses in header (rather than 2)
	- 1. Ad-hoc (connects to each other, most common)
	- 2. WLANS
	- 3. Mesh networks (mixture of 1 and 2)
