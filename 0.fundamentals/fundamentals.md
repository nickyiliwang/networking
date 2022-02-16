Networking:

Course Link: [https://www.professormesser.com/network-plus/n10-006/n10-006-course-index/](https://www.professormesser.com/network-plus/n10-006/n10-006-course-index/)

S1 - Architecture



1. Remote Access
2. Services
3. Topologies
4. Infrastructures
5. Addressing
6. Routing
7. Cloud and Virtualization Tech
8. Implementing Networks

S2 - Operations



1. Monitoring the network

S3 - Security



1. Vulnerabilities and Threats
2. Firewalls
3. Network Access Control

S4 - Troubleshooting



1. Troubleshooting Methodology
2. Tools
3. Network issues
4. Security Issues
5. WAN Issues

S5 - Industry Standards, Practices, and Network Theory



1. OSI Model
2. Theory and Concepts
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



* Authentication, compression, error detection, multilink, **no encryption**
* Physical networking: telephone lines, mobile phone, serial cables
* L2 with only modem, **needs more functionality for remote access over IP**

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


