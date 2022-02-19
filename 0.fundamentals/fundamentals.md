Networking:

Course Link: [https://www.professormesser.com/network-plus/n10-006/n10-006-course-index/](https://www.professormesser.com/network-plus/n10-006/n10-006-course-index/)

S1 - Architecture



1. Remote Access ✔
2. Services✔
3. Topologies✔
4. Infrastructures✔
5. Addressing✔
6. Routing (BIG)
7. Cloud and Virtualization Tech
8. Implementing Networks

S2 - Operations



1. Monitoring the network

S3 - Security



1. Vulnerabilities and Threats (BIG)
2. Firewalls
3. Network Access Control

S4 - Troubleshooting



1. Troubleshooting Methodology
2. Tools (BIG)
3. Network issues (BIG)
4. Security Issues (BIG)
5. WAN Issues (BIG)

S5 - Industry Standards, Practices, and Network Theory



1. OSI Model
2. Theory and Concepts (BIG)
3. Ports and Protocols
4. Application Ports and Protocols

Security:

Course Link: [https://www.professormesser.com/security-plus/sy0-501/sy0-501-training-course/](https://www.professormesser.com/security-plus/sy0-501/sy0-501-training-course/)

S3 - Architecture and Design



1. Cloud Technologies
2. Resiliency and automation

S6 - Cryptography and PKI



1. Public Key Infra



#S1 - Architecture - Remote Access

##VPN Connections

S2S VPN



* ONPREM communicate over an existing internet connection
* Encrypt all of the traffic with a VPN appliance, or a firewall, or a router, or another device that can handle these types of site-to-site VPNs. 

Client VPN (host to site)



* Laptops at coffee shop

Host to host 



* Laptop to laptop

##VPN Protocols

PPP



* Authentication, compression, error detection, multilink, no encryption
* Physical networking: telephone lines, mobile phone, serial cables
* L2 with only modem, needs more functionality for remote access over IP

PPTP (PP Tunneling)



* Can encrypt PPP connections

SSL VPNs (secure socket layer)



* Web protocol
* Can authenticate with username and password

IPSec



* secure IP packets there at layer 3. 
* Every packet can be authenticated and encrypted through the tunnel, exposing very little. 
* Security and integrity: prevents someone from replaying that traffic and trying to use that to gain access to our network. This encryption and packet signing functionality maintains both the security, and it’s ensured that only this traffic is going to be used once through that tunnel.
* Standardized with vendor devices.
* Authentication Header: 
    * Used to make sure that the data is authenticated on both sides. 
* Encapsulation Security Payload:
    * ESP secures the data and makes sure that all of the information is also encrypted.



##TACACS and RADIUS

Central mechanism/storage for AAA(Authenticate, Authorize, Accounting) and logging.

RADIUS (Remote Authentication Dial In User Service)



* Supported by remote access servers, and wireless access points, and firewalls, and many other devices, as well. 
* Same credentials for all access

TACACS/+



* With accounting and auditing to this authentication protocol
* TACACS+: more requests and authorization capabilities. 

##RAS (Remote Access Services) / RRAS(Routing and Remote Access Service)



* Windows service
* Remote access server can be a multi-protocol router running dynamic protocols such as RIP and OSPF. 
* You have a demand-dial router inside of it so that you can connect to it with VPN connectivity.

##Web Services

XML is old way of handling data between different entities, like text files

and JSON is modern

##Unified Voice Services

Singular method of communication for voice/phone communication

##Wireless LAN Controllers

Manages multiple  access points: logging, security, provision, performance

Software or hardware: single pane of glass.



#S1 - Architecture - Network Services

##DHCP Addressing

Automatically assigning IP address, and a subnet mask, and a default gateway, and DNS settings, and NTP settings, and more.

Steps:



1. Discover: Client => DHCP Server
2. Offer: DHCP Server => Client 
3. Request: Client => DHCP Server
4. Pack: DHCP Server to Client

##DHCP Reservations

dynamic and static allocation

Reserving IP Address associating with an MAC address

##DHCP Scopes

Pool of IP addresses is configured as a scope

scope determines the address configurations used on a subnet

##DHCP Leases

IP Addresses are leased and devices has to checkback or be reallocated

T1 and T2 timers ensures the device might wait for the DHCP server to come back

##DHCP Options

Different kinds of devices need different sets of IP configuration settings. Additional settings as part of the DHCP RFC, also called DHCP Options. 

Ie. Voice over IP devices use option 129 with the IP address of the call server. So that it can then check in with the call server and become an active phone on your network.



##DNS Overview

Domain name => IP address

distributed database with servers that are located all over the world

13 root servers

gTLDs and ccTLD

Authoritative and delegation, walking the tree.

[www.example.com](www.example.com) is a FQDN

##DNS Record types

A(ipv4), AAAA(ipv4), CNAME, MX, ALIAS(AWS R53, traffic to selected AWS resources)



* Point a host name (“name”) to your site. name to resolve to an IP
* The A record maps a name to one or more IP addresses
* CNAME record maps a name to another name,

Rules:



1. A/AAAA: manage which IP addresses are assigned to a particular machine, or if the IPs are fixed.
2. CNAME: alias one name to another name, and you don’t need other records (such as MX records for emails) for the same name.  Doesn’t work on zone apex (naked domain)
3. ALIAS: if you’re trying to alias the root domain (zone apex), or if you need other records for the same name. In AWS routes traffic to selected AWS resources. Can create at zone apex.

##Dynamic DNS

This allows us to update these records in the DNS server in a process that is automated

Use when IP addresses are changing a lot

Ie. MSAD: the domain controllers register in the DNS. with DDNS any of the devices that connect to the network are able to find a domain controller.

Ie. [Dynamic DNS in EC2 ](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/dynamic-dns.html)with “noip” service.

Ie. [Serverless Dynamic DNS](https://aws.amazon.com/blogs/startups/how-to-build-a-serverless-dynamic-dns-system-with-aws/)

Ie. Access services at home from outside. It’s difficult to keep track of what the IP address might be. Much easier to assign a name to our cable modem, and use a dynamic DNS service to constantly update whenever that IP address changes, authenticating with a name/password. 

##Proxy Servers

Control, security and caching.

Middleman that makes the request (ie. website), URL filtering, content scanning, 

Reverse proxy is when you access private web server from the internet

Open proxy is third party, might not be secure

##NAT and PAT

Public IPV4 shortage and security

IPV4 private addresses translated to a public Ip address with a unique port assigned.

NAT Gateway uses PAT and IGW uses Static NAT, home router uses dynamic NAT

Has its own conversion table 

Static(One to one) or Dynamic(One to Pool), PAT(many to one with ephemeral ports)

Ie. Aka port forwarding. And we’re using this as a static configuration– that IP address of a web server or a game server is going to assume to always be available. So if any traffic is coming into our router, the router will make the translation and always send it to that device.



#S1 - Architecture - Network Topologies

Helps with the design and troubleshooting,

P2P (point to point): 



* 2 devices from end to end, WAN

P2MP (point to multiple points)



* Wireless network, all talking to central device, not each other

Mesh



* Every(full) or most every(partial) site is connected to every other site
* Redundancy: Top to bottom (tree) and send traffic over multiple links simultaneously and redundantly, ie. WAN
* Load balancing

Bus (Legacy)



* Single cable for all to connect, easy install but error prone

Ring



* Sending exactly the same information down both sides of the ring (ie. SONET)

Star



* ethernet network, central device like router, all to one, central switch

Hybrid



* Combination, ie. star x 3 in a ring

Applications:



* Client to Server, costs more for more powerful server
* Peer to peer, no central server, torrent, less secure



#S1 - Architecture - Network Infrastructures

PAN (Personal Area Network)



* Bluetooth, hotspots, mouse and keyboards

LAN (Local Area Network)



* 

WLAN (Wireless LAN)



* Communication channel with 802.11 

MAN (Metropolitan Area Network)



* Confined geographical area, Metro ethernet providers
* Connecting natively, without any additional WAN technologies

WAN (Wide Area Network)



* Communicating over a relatively long distance.
* Connecting up a LAN in one facility with the LAN in another facility
* Going to third party to provide a WAN, using point to point link, MPLS connection, or satellite link



#S1 - Architecture - Network Addressing

##Binary math

Byte or 8 bits, or octet

128 64 32 16 8 2 1

##IPV6

128-bit address

No need to subnet, so we use /64 often

Ipv4 shortage

You can remove leading 0s

##IPV6 address config

NDP (Neighbor discovery protocol)



* No broadcasts, uses multicast instead
* Neighbor MAC Discovery, unlike ARP in IPV4
* Auto configure of IP address without DHCP (SLAAC)
* Discover routers with RS and RA
* DAD (Duplicate Address Detection)

Link-local address



* works on your local subnet, talk to local devices
* starts with fe80

DHCPv6



* similar process with IPv4 but with multicast
* Ie. voice over IP configuration detail \


##IPV6 Interoperability

Translating between IPV4 to IPV6 and vice versa



* Requires relay routers
* 6to4 no support for NAT
* Dual-stack can run both



##IPv4 Classes

we know where the next step is to communicate with you with our routing and we let the routers handle the rest of that communication

Subnetting



1. IP Address and Subnet Mask
    1. Must combine. Network + Host
    2. Subnet Mask => what network it belongs
2. Default gateway
    3. We need to know the router IP to communicate outside of our subnet

Classful subnetting (Legacy, retired)



* The subnet mask was something set automatically based on your IP address.
* Static structure and no configuration of sizes of network
*  A: 255.0.0.0 | B: 255.255.0.0 | C: 255.255.255.0

Private addresses



* RFC 1918 addresses 
* 10.0.0.0 ~ 10.255.255.255 = 1 Class A = 16 million+ addresses
* 172.16.0.0 ~ 172.31.255.255 = 16 Class Bs
* 192.168.0.0 ~ 192.168.255.255 = 256 Class Cs



##CIDR (Classless Inter Domain Routing)



1. Class based subnets were inflexible, the jumps between classes were too dramatic 
2. CIDR Subnet masks did not have to end on a single octet
3. Create a flexible subnetting scheme for the right amount of IP address space.

CIDR Notation (end on octet) 

Ie. 192.168.1.1/24



* Subnet mask of 255.255.255.0 (3 x 8)
* 192.168.1.0 ~ 192.168.1.255 = 254 hosts per subnet, 256 minus .0(network address) and .255(broadcast address)

Ie. 10.1.0.1/16



* Subnet mask of 255.255.0.0 (2 x 8)
* 10.1.0.0 ~ 10.1.255.255 = 65’534 addresses per subnet

CIDR Notation (does not end on octet)

Ie. 10.1.0.1/26



* Subnet mask of 255.255.255.192 (128 + 64)
* 10.1.0.0 ~ 10.1.0.63, 62 addresses minus .0(network address) and .64(broadcast address)



#IP Subnetting

**Important don’t forget to subtract the network and broadcast address. Ie. 256 - 2 = 254


<table>
  <tr>
   <td>subnet
   </td>
   <td>1
   </td>
   <td>2
   </td>
   <td>4
   </td>
   <td>8
   </td>
   <td>16
   </td>
   <td>32
   </td>
   <td>64
   </td>
   <td>128
   </td>
   <td>256
   </td>
  </tr>
  <tr>
   <td>host
   </td>
   <td>256
   </td>
   <td>128
   </td>
   <td>64
   </td>
   <td>32
   </td>
   <td>16
   </td>
   <td>8
   </td>
   <td>4
   </td>
   <td>2
   </td>
   <td>1
   </td>
  </tr>
  <tr>
   <td>subnet mask
   </td>
   <td>/24
   </td>
   <td>/25
   </td>
   <td>/26
   </td>
   <td>/27
   </td>
   <td>/28
   </td>
   <td>/29
   </td>
   <td>/30
   </td>
   <td>/31
   </td>
   <td>/32
   </td>
  </tr>
</table>


Q: CIDR 192.168.1.0/24 and split it into 4 networks to support 40 devices

A: /26 and have 62 useable hosts in 4 networks 1 ~ 62, 65 ~ 126, 129 ~ 190, 192 ~ 254



##APIPA  (Automatic Private IP Address / link-local address)



* Device local subnet comms in the absence of a DHCP server
* 169.254.1.0 ~ 169.254.254.255. **169.254 gives aways its APIPA
* OS uses ARP to check for duplicate IP address in the local network

##Unicast, Multicast and Broadcast

Unicast



* 1 to 1
* Web surfing, file transfer

Broadcast



* Send one packet to everyone on the network
* ARP, Routing updates
* Not used in IPV6

Multicast (IPV6)



* One to many, but specific group
* Multimedia, stock exchanges
* Specialized and difficult to scale

##Broadcast Domain and Collision Domain

Collision Domain (Legacy)



* 2 devices communicated at the same time and corrupted data
* Ie. 2 people talking at the same time in a conference call
* L2 Switches solves this issue with MAC headers, CSMA/CD]

Broadcast Domain



* ARP probes / OS notifications
* Passes switch and stops at the Router



#S1 - Architecture - Routing
