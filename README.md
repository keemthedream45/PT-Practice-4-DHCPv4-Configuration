# PT - DHCPv4-Configuration
Scenario Overview – “Small Business Network Upgrade”

## DHCPv4 Network Configuration Lab – PT Practice
A small business is expanding its internal network and transitioning from static addressing to a centralized DHCP system. Two LANs must be configured with automated IPv4 assignments, and Router R1 must be secured and deployed as the DHCPv4 server.

## Objective
This lab will develop my practical skills in router configuration, DHCP automation, interface addressing, and verification of IPv4 services. The primary focus is on configuring a Cisco router to dynamically assign IP addresses across multiple subnets, securing device access, and verifying full end-to-end network connectivity.

## Skills Learned
- Router Baseline Configuration – Applying essential security practices: disabling DNS lookup, securing access lines, encrypting passwords, configuring MOTDs, and setting hostnames.

- DHCPv4 Server Deployment – Creating multiple DHCP pools, assigning gateways, DNS servers, excluded addresses, and verifying address bindings.

- IPv4 Subnet & Interface Configuration – Assigning correct subnet masks, enabling interfaces, and managing multi-LAN routing.

- Network Troubleshooting & Verification – Using commands like show ip dhcp binding, ipconfig, and ping to verify successful DHCP operations and inter-LAN connectivity.

## Tools Used
- Cisco Packet Tracer – Full simulation of router configuration and DHCP delivery.

- Cisco IOS CLI – Configure router interfaces, passwords, DHCP pools, and diagnostics.

- Windows PC Simulation – Used to verify DHCP assignments and connectivity.

- Ping Utility – Validate end-to-end communication between hosts.

- Telnet (optional) – Confirm remote access functionality.

## Topology
<img width="660" height="128" alt="Screenshot 2025-11-18 135031" src="https://github.com/user-attachments/assets/fe51287b-a7bb-41a5-85af-671bac0b452b" />


## Steps
Step 1 – Preparing the Router for Configuration
- The first requirement was to connect a console cable to Router R1 in Packet Tracer and enter global configuration mode. Once in, I began configuring the baseline security and interface settings.

Hostname, DNS Lookup, and Password Security

- I first set the device hostname to R1 and disabled DNS lookup, which prevents the router from hanging when mistyped commands are entered. I then configured the privileged EXEC password (class), console password (cisco), and VTY line password (cisco) for Telnet access. All plaintext passwords were encrypted using the service password-encryption command.

MOTD Banner

- A Message of the Day banner was added to display “Authorized access only!”, helping reinforce security warnings for anyone accessing the router.

IPv4 Interface Configuration

- Using the addressing table, I configured the router’s GigabitEthernet interfaces:

- G0/0/0 → 192.168.10.1/24

- G0/0/1 → 192.168.20.1/24

After assigning the addresses, I enabled both interfaces using the no shutdown command.

<img width="329" height="143" alt="Screenshot 2025-11-18 140322" src="https://github.com/user-attachments/assets/fac49300-21d0-45df-a7b6-74c0bd129c64" />

<img width="171" height="300" alt="Screenshot 2025-11-18 140338" src="https://github.com/user-attachments/assets/d773392e-0c8d-42c6-a24e-7dfaaabbab54" />

<img width="351" height="77" alt="Screenshot 2025-11-18 140408" src="https://github.com/user-attachments/assets/cd62f0f1-1eda-444f-a243-a7ce10eaa361" />

--

Step 2 – Configuring R1 as the DHCPv4 Server
Excluding Reserved Addresses

The lab required excluding the first five usable IP addresses from each subnet. I configured exclusions for both LAN networks:

- 192.168.10.1 – 192.168.10.5

- 192.168.20.1 – 192.168.20.5
<img width="429" height="196" alt="Screenshot 2025-11-18 140847" src="https://github.com/user-attachments/assets/fc469575-00a1-4f32-b6ff-6b64ca539538" />

Creating DHCP Pools for LAN1 and LAN2

Next, I created two DHCP pools, matching each LAN:

- LAN1 → 192.168.10.0/24

- LAN2 → 192.168.20.0/24

Each pool included the network statement, default gateway, DNS server (209.165.200.225), and domain name (ccna-practice.com), as required by the lab.

<img width="371" height="183" alt="Screenshot 2025-11-18 141350" src="https://github.com/user-attachments/assets/28aaeb55-6644-458a-8889-5e4981dcacd1" />

--

Step 3 – Verifying DHCPv4 Functionality
Testing DHCP on PC-A and PC-B

I set both PCs to DHCP mode. Each PC automatically received an IP address from its respective DHCP pool:

- PC-A received an address in 192.168.10.6 – 254, with gateway 192.168.10.1.

- PC-B received an address in 192.168.20.6 – 254, with gateway 192.168.20.1.

The DNS server and subnet mask were correctly populated on both devices, confirming the DHCP server was functioning as expected.

Router DHCP Binding Verification

Using the show ip dhcp binding command, I confirmed that both PCs had active leases. Each device appeared with its assigned IP and MAC address.

<img width="545" height="85" alt="Screenshot 2025-11-18 160832" src="https://github.com/user-attachments/assets/419eb225-630e-4d55-9d00-94b1ee172ebf" />

--

Step 4 – Connectivity Testing
End-to-End Ping Testing

Once the PCs had valid IPs, I performed ping tests to:

- Each PC’s default gateway

- Router interfaces

- The opposite LAN host

All pings were successful, confirming that the router was forwarding packets correctly between the two LANs.

--

Conclusion

This lab demonstrated how to configure a Cisco router as a DHCPv4 server for multiple LAN segments. The tasks included securing the router, configuring IPv4 interfaces, building DHCP pools, excluding reserved addresses, and verifying successful address distribution. Through this lab, I strengthened my understanding of:

- DHCP pool creation

- Router interface setup

- Basic Cisco security hardening

- Network connectivity testing

- Multi-LAN routing and dynamic address assignment

By completing this lab, I achieved a working two-LAN environment where all devices received automatic addressing and were able to communicate end-to-end across the router.

--

[Ciso Netwoking Academy lab](https://www.netacad.com/courses/all-courses)



