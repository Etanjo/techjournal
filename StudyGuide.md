

## OSI Model (Layers 1–4)

### Layer 1 — Physical Layer
Deals with the actual physical transmission of data — cables, wires, radio waves, and the hardware components of devices. Doesn't care about what the data is, just moves signals.

**Hub** — Layer 1 device. Sends incoming data out to every port no matter what. No configuration needed.

---

### Layer 2 — Data Link Layer
Handles how data gets sent between devices on the same network. Uses MAC addresses to identify devices.

**MAC Addresses** — 48-bit hardware addresses that look like `00:1A:2B:3C:4D:5E` (6 pairs of hex digits).
- First 3 pairs = OUI (identifies the manufacturer)
- Last 3 pairs = UID (unique to that specific device)

**Switch** — Layer 2 device. Keeps a table of which MAC address is on which port and only sends data where it needs to go (smarter than a hub).

---

### Layer 3 — Network Layer
Handles routing data between different networks using IP addresses.

**IPv4 Addresses** — look like `192.168.1.10` (4 numbers, each 0–255, separated by dots).

**Network ID vs. Host ID** — the subnet mask tells you which part of the IP is the network and which part is the host.
- Example: `192.168.1.10` with mask `255.255.255.0` → network is `192.168.1`, host is `.10`

**Private IP Ranges**

| Class | Range | Mask |
|-------|-------|------|
| A | 10.0.0.0 – 10.255.255.255 | /8 |
| B | 172.16.0.0 – 172.31.255.255 | /16 |
| C | 192.168.0.0 – 192.168.255.255 | /24 |

Other reserved: `127.x.x.x` (loopback), `169.254.x.x` (APIPA — no DHCP found), `255.255.255.255` (broadcast)

**VLSM Table**

| CIDR | Subnet Mask | Usable Hosts |
|------|-------------|--------------|
| /24 | 255.255.255.0 | 254 |
| /25 | 255.255.255.128 | 126 |
| /26 | 255.255.255.192 | 62 |
| /27 | 255.255.255.224 | 30 |
| /28 | 255.255.255.240 | 14 |
| /29 | 255.255.255.248 | 6 |
| /30 | 255.255.255.252 | 2 |

> Note: find a fuller VLSM table (/8–/32) for the Tech Journal

**Wildcard Masks** — the inverse of a subnet mask, used in OSPF and ACLs. Flip all the bits: `255.255.255.0` → `0.0.0.255`

**Router** — Layer 3 device. Moves packets between networks. Needs an IP and subnet mask on each interface, plus `no shutdown` to turn the port on.

**Multilayer Switch** — works at both Layer 2 and Layer 3, so it can route between VLANs without a separate router.

---

### Layer 4 — Transport Layer
Manages end-to-end communication between hosts.
- **TCP** — reliable, connection-based (makes sure everything arrives in order)
- **UDP** — faster, no guarantees (used for video, gaming, etc.)
- Uses **port numbers** to get data to the right application

---

## Switches and Routers

**Network Topologies**
- Star — all devices connect to one central switch (most common)
- Bus — all devices on one shared cable
- Ring — devices in a loop
- Mesh — every device connects to every other
- Hybrid — mix of the above

**MAC Address Table** — a switch builds this automatically, mapping MAC addresses to ports. Used to send frames to the right place instead of flooding everything.

**Routing Table** — a router's list of known networks, where to send packets for each one, and which interface to use. Can be built from directly connected networks, static routes, or dynamic routing protocols.

**Default Gateway** — the router's IP address on your local network. Anything going outside your subnet gets sent here first. Has to be on the same subnet as your device.

**Static vs. Dynamic Routing**
- Static: you manually type in routes. Simple but doesn't scale.
- Dynamic: routers figure out routes automatically using a protocol like RIPv2 or OSPF. Better for bigger networks.

**Wireless Routing** — a wireless router is basically a router + switch + access point in one box. You configure the SSID, channel, WPA2 password, and DHCP.

**VLANs** — split one physical switch into multiple logical networks. Devices on different VLANs can't talk without a router.
- Access port — one VLAN, connects to end devices
- Trunk port — carries multiple VLANs, connects switches/routers

**Wireless Terms**
- SSID — the name of the Wi-Fi network
- Access Point — broadcasts the wireless signal
- Channel — the frequency being used (1, 6, or 11 on 2.4 GHz)
- WPA2 — the encryption standard for Wi-Fi security
- DHCP — automatically hands out IP addresses to devices

---

## Commands

**ipconfig** — shows your IP address, subnet mask, and default gateway

**ipconfig /all** — same as above but also shows your MAC address, DNS servers, and DHCP info

**ping** — sends a test packet to an address to see if it's reachable. Shows response time and whether packets were lost.

**tracert** — shows every hop (router) a packet passes through on its way to a destination. Good for finding where something breaks.

**nslookup** — asks a DNS server to look up a hostname and return its IP address. Useful for checking if DNS is working.

---

## Protocols

| Protocol | What it does |
|----------|--------------|
| ICMP | Sends error/diagnostic messages — what ping and tracert use |
| ARP | Figures out the MAC address for a given IP on the local network |
| DHCP | Automatically assigns IP, subnet mask, gateway, and DNS to devices |
| HTTP | Transfers web pages between a browser and server |
| RIPv2 | Dynamic routing protocol, uses hop count, max 15 hops |
| OSPF | Dynamic routing protocol, uses bandwidth as cost, scales better than RIP |

**IGP vs. EGP**
- IGP (like RIPv2, OSPF) — used for routing inside a single organization's network
- EGP (like BGP) — used for routing between different organizations/networks on the internet

---

## Security

**CIA Triad**
- Confidentiality — only the right people can access data
- Integrity — data hasn't been changed or tampered with
- Availability — systems are up and accessible when needed

**Firewall** — sits at the edge of a network and filters traffic based on rules (IP, port, protocol). Can be hardware or software.

**IDS vs. IPS**
- IDS — watches traffic and sends alerts but doesn't do anything about it
- IPS — watches traffic and actively blocks threats

---

## Packet Tracer

**Connecting devices**
- PC to switch: straight-through cable
- Switch to router: straight-through cable
- Router to router: crossover or serial cable

**Configuring a router interface**
```
interface GigabitEthernet0/0
ip address 192.168.1.1 255.255.255.0
no shutdown
```

**Configuring a PC** — go to Desktop > IP Configuration, enter IP address, subnet mask, and default gateway manually.

**PDU vs. ping** — PDU is Packet Tracer's built-in simulation tool that lets you see exactly what's happening at each hop. Ping is just a quick command-line connectivity check.

**Configuring VLANs**
```
! Create VLAN
vlan 10

! Access port
interface FastEthernet0/1
switchport mode access
switchport access vlan 10

! Trunk port
interface FastEthernet0/24
switchport mode trunk
```

**Setting up a wireless router** — open its GUI, set the SSID/channel/WPA2 password, enable DHCP. On the laptop go to Desktop > PC Wireless, connect to the SSID, enter the password.

**Troubleshooting steps**
1. Figure out what's not working
2. Come up with a theory for why
3. Test it (ping, check cables, check configs)
4. Make a fix
5. Verify everything works
6. Document what you did

When troubleshooting, start at Layer 1 (is it plugged in?) and work your way up.
