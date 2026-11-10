# GT-BN98 Pro WAN cutover — initial connectivity

**Date:** 2026-11-09

The user reports that the ASUS ROG Rapture GT-BN98 Pro dashboard shows **Connected**, WAN connection type **Automatic IP (DHCP)**, and a laptop can browse the web through the router. The router was configured to use its 10G WAN/LAN 1 interface with the Calix GP1101X handoff. Physical 10GbE link negotiation, 5Gbps throughput, IPv6, latency and full household Wi-Fi migration remain to be tested.

## Immediate next validation
1. Check negotiated WAN link rate (10Gbps expected; not yet confirmed).
2. In Windows 11 use `ncpa.cpl` and inspect Ethernet adapter status/speed.
3. Measure download/upload, ping and jitter; record whether test runs on router, wired laptop, or Wi-Fi.
4. Test the new NEXUS Wi-Fi SSIDs and representative household devices.
5. Retain the prior ASUS router and encrypted configuration backups for rollback.

Never publish WAN IP, MACs, device IDs, passwords, or configuration exports.
