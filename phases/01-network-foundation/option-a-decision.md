# Architecture Decision: Option A — ASUS-first

**Decision date:** 2026-10-22  
**Status:** Approved for initial deployment; not yet installed

## Context
- 5 Gbps fiber service with technician-installed Calix GP1101X.
- Existing ASUS GT-AXE11000 provides current household Wi-Fi and routing.
- ASUS ROG Rapture GT-BN98 Pro has been purchased. Reported shipping date: October 29, 2026; arrival not confirmed.
- The broader project will introduce managed switching, TrueNAS, Proxmox, and a segmented cybersecurity lab.

## Decision
Keep the existing router in service until the GT-BN98 Pro arrives. Then stage the GT-BN98 Pro as the primary router and wireless access point, connecting the ONT to its 10GbE WAN interface. Add a VLAN-capable managed switch in a subsequent phase.

Do not purchase a standalone OPNsense appliance yet. Consider OPNsense as an isolated lab firewall behind ASUS first, or later promote it to the primary firewall and transition the ASUS to AP mode, subject to testing.

## Validation gate
- Verify 10GbE WAN link negotiation and ISP configuration.
- Verify internet speed using an appropriately equipped wired client; Wi-Fi benchmarks are not a 5 Gbps throughput test.
- Test local DHCP, DNS, wireless, security features, service stability, IPv6, and rollback.
- Reassess per-VLAN isolation before onboarding storage and lab assets.
- Keep private IP inventories, order details, WAN identifiers, and device configuration exports out of the public repository.

## Tradeoffs
ASUS-first simplifies household continuity and Wi-Fi upgrades. Its firewall and wireless VLAN-policy flexibility may be narrower than a dedicated OPNsense environment. The project will revisit this decision based on measured needs.
