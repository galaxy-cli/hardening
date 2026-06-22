# Hardened Home Network Architecture Blueprint

An enterprise-grade, privacy-first home network architecture designed to eliminate ISP metadata harvesting, quarantine untrusted devices, and block tracking vectors. By collapsing complex corporate networking concepts into a streamlined, all-in-one open-source router framework, this setup achieves maximum data isolation with minimal maintenance overhead.

---

## System Architecture

Data flows strictly through a single logical choke point to guarantee that no unencrypted or unfiltered packets ever reach the public internet:

[ Device ] ──► [ Ethernet / Wi-Fi Mesh ] ──► [ Wi-Fi Router ] ──► [ ISP Modem ] ──► [ Internet ]
---

## Physical Connection Topologies

This architecture natively supports two interchangeable physical deployment methods depending on your home layout and performance requirements.

### 1. Hardware Ethernet Setup
Optimized for stationary, high-bandwidth hardware requiring maximum stability and zero wireless latency.
* **The Flow:** Device ➔ Ethernet-only USB Tethered Cabling ➔ Managed Network Switches ➔ Ethernet-only Open-Source Firmware Router ➔ ISP Modem ➔ Internet.

### 2. Wireless Mesh Setup
Optimized for mobile devices and widespread, whole-home coverage without running physical cables through walls.
* **The Flow:** Device ➔ Wi-Fi Mesh Interconnected Nodes ➔ Open-Source Firmware Wi-Fi Router ➔ ISP Modem ➔ Internet.

---

## Implementation Checklist

### Client-Level Hardening (Device Settings)
* [ ] **MAC Address Randomization:** Enabled on all smartphones, laptops, and tablets to prevent local hardware profiling.
* [ ] **Privacy-Hardened Browser:** Deploy open-source browsers (e.g., LibreWolf, Brave) with advanced first-party ad blockers enabled to catch content-layer scripts.

### Network-Level Hardening (Router Settings)
* [ ] **VLAN Segmentation:** Group and isolate devices by trust level via the router interface (e.g., Main, IoT, Guest).
* [ ] **Network-Wide Ad Blocker:** Run an inbound DNS sinkhole (e.g., AdGuard Home, Pi-hole) to drop tracker domains natively at the perimeter.
* [ ] **Outbound Open-Source DNS Resolver:** Deploy a recursive resolver (e.g., Unbound) configured strictly for **DNS-over-TLS (DoT)** or **DNS-over-HTTPS (DoH)**.
* [ ] **Outbound Leak Mitigation:** Completely disable all IPv6 traffic across the entire router interface to block background data leakage.

---

## Centralized Router Firewall Rules

All traffic routing intelligence is managed entirely within the open-source router firmware dashboard (e.g., OpenWrt, OPNsense). 

### VLAN Segment Rule Order (Strict Top-to-Bottom Execution)
To prevent network lockouts, your virtual interfaces must execute traffic rules in this exact chronological order:
1. **Rule 1 (ALLOW):** Destination ➔ Internal DNS Resolver / Ad Blocker IP address.
2. **Rule 2 (ALLOW):** Destination ➔ Outbound WireGuard Tunnel interface.
3. **Rule 3 (BLOCK/DROP):** Destination ➔ Any other internal VLAN (Full Network Isolation).

### The Outbound Tunnel & Kill Switch Rule
* **The Tunnel:** All authorized outbound traffic is packed into an open-source VPS tunnel or a audited, no-logs VPN service (utilizing the high-speed WireGuard protocol).
* **The Kill Switch:** A hardcoded firewall rule on the default WAN interface that dictates an **immediate, unconditional network disconnect if the tunnel drops**. If the VPN connection blinks, internet access for the entire house is instantly severed to prevent public IP leaks.

---

## Threat Model Resolution

| Threat Vector | Standard Consumer Network | Hardened Home Network |
| :--- | :--- | :--- |
| **ISP Eavesdropping** | Sells full DNS and web history metadata. | Sees nothing but scrambled WireGuard noise. |
| **IoT Gadget Spyware** | Compromised smart tech hacks local PCs. | Quarantined inside a restricted VLAN bucket. |
| **Bypassed Ad Blockers** | Smart TVs ignore local blocklists via hardcoded DNS. | Intercepted via Port 53 rules and forced back to AdGuard. |
| **VPN Dropout Leaks** | Device quietly reverts to regular ISP lines. | Kill switch immediately freezes the internet pipe. |
