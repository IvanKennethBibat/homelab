# homelab
A centralised repository for documenting the config, deployment, and maintenance of my homelab using a 2017 Acer Swift SF314-52.


## 1. Hardware
- Acer Swift SF314-52
- i3-7100U
- 8 GB RAM
- 119 GB SSD

## 2. Network
- FRITZ!Box — primary router
- ASUS XT9 — Access Point (AP)
- Homelab LAN: `192.168.178.0/24`
- FRITZ!Box gateway: `192.168.178.1`
- XT9: `192.168.178.31`
- Homelab: `192.168.178.50`
- Interface: `wlp1s0`
- DHCP, routing, and NAT are handled by the FRITZ!Box
- The XT9 provides WiFi/Ethernet connectivity in AP mode

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
- The homelab and XT9 have been assigned permanent IPv4 addresses now.

The following address changes were made:
- FRITZ!Box  - 192.168.178.1
- Homelab    - 192.168.178.50
- XT9        - 192.168.178.31

#### Update 17:47
- Verified homelab connectivity after converting XT9 to AP.
- 192.168.178.1 - Default gateway is reachable with 0% packet loss
- 1.1.1.1 - Internet connectivity without DNS resolution, 0% packet loss
- google.com - DNS resolution and internet connectivity with 0% packet loss

#### Update 18:18
- Established the current homelab hardware/system resources.
- Commands:
    - hostnamectl
    - free -h
    - lsblk

- Hostname: `acer-homelab`
- OS: Debian 13 (Trixie)
- Kernel: `6.12.107+deb13-amd64`
- Architecture: x86-64
- Hardware: Acer Swift SF314-52
- RAM: 7.6 GiB total, 7.2 GiB available
- Swap: 6.2 GiB total, currently unused
- Storage: 119.2 GB SSD
  - EFI: 976 MB
  - Root: 112.1 GB
  - Swap: 6.2 GB