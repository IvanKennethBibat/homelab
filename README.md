# homelab
A centralised repository for documenting the config, deployment, and maintenance of my homelab using a 2017 Acer Swift SF314-52.


## 1. Hardware
- Acer Swift SF314-52
- i3-7100U
- 8 GB RAM
- 119 GB SSD

## 2. Network
- FRITZ!Box — upstream router
- ASUS XT9 — router
- Homelab LAN: 192.168.50.0/24
- XT9 gateway (LAN): 192.168.50.1
- XT9 WAN: 192.168.178.31
- Homelab: 192.168.50.5
- Interface: wlp1s0
- FritzBox network: 192.168.178.0/24
- The XT9 creates a separate '192.168.50.0/24' network behind the FritzBox.

## 3. Debian
- Debian 13 Stable
- SSH
- UFW
- dhcpcd

## 4. Security
- SSH key authentication
- Password SSH disabled
- Root SSH disabled
- Firewall configuration


## What I've learnt so far
### 29.09.26
- DHCP automatically assigns IP addresses to devices connected to a network.
- The homelab sends traffic outside its local subnet to its default gateway, the XT9 router (192.168.50.1).
- Debian was chosen over Ubuntu Server for its leaner resource usage (7% idle RAM usage vs 15% RAM usage with Ubuntu); with the constraints of the hardware with 8GB RAM the difference in RAM usage is meaningful 
- (Source: https://www.techaddressed.com/features/4-reasons-debian-vs-ubuntu-server/).
- My network is double NAT, meaning that the XT9 router is itself a router behind the FritzBox router, creating two separate NAT layers.

#### Update 17:09
- Double NAT issue was resolved by converting XT9 from router mode to Access Point (AP) mode, making its use to be exclusively for WiFi/Ethernet connectivity.
- The FritzBox now exclusively handles routing, NAT, and DHCP.

The following address changes were made:
- FRITZ!Box  → 192.168.178.1
- XT9        → 192.168.178.31
- Homelab    → 192.168.178.50