# Phase 01 — Network foundation

**Status: Planning. No purchases or deployments are claimed.**

## Design requirements

- Plan for a **5 Gbps fiber service tier**; physical ISP handoff and sustained throughput still require verification.
- Use a firewall with suitable **10GbE WAN and LAN** paths.
- Retain the existing Wi-Fi 6E router as an AP only if AP mode and cabling test successfully; its 2.5GbE uplink is a constraint.
- Select a VLAN-aware managed switch with 10GbE headroom and future NAS and Proxmox connectivity.
- Stage changes without disrupting household Wi-Fi; preserve rollback.

## Before purchasing

1. Determine whether ISP supplies an ONT or gateway; confirm 10GbE handoff port type (RJ45/SFP+), DHCP/PPPoE, VLAN tagging, and any restrictions.
2. Privately record existing router firmware, addressing, reservations and routing.
3. Capture a wired speed baseline from a device capable of multi-gig speeds.
4. Verify prospective firewall CPU performance with IPS/VPN enabled, NIC support, cooling and form factor.
5. Verify switch VLAN features, port allocation, optics and AP behavior.

## Staged implementation

1. Export existing router settings to **offline private storage**.
2. Stage OPNsense with a laptop on an isolated `10.10.99.0/24` test LAN.
3. Temporarily connect OPNsense WAN behind the existing router. Verify DHCP, DNS, outbound browsing and updates.
4. Configure a trusted home VLAN and restricted management VLAN. Test untagged access ports and tagged trunks.
5. Enforce default-deny inter-VLAN rules and explicitly allow necessary DNS/DHCP/admin flows.
6. Validate rollback before transitioning primary routing.
7. Migrate existing Wi-Fi router to AP mode on a trusted access port only when validated.
8. Configure Tailscale on trusted endpoints with MFA/device policy; test from a separate external internet connection.
9. Verify IPv4/IPv6 filtering, throughput, management isolation, power and restoration behavior.

## Acceptance criteria

- [ ] ISP handoff and actual port negotiated rate verified
- [ ] 10GbE WAN/LAN path tested
- [ ] Existing configuration exported privately
- [ ] New firewall staged non-disruptively
- [ ] VLAN separation and rule logging validated
- [ ] Trusted Wi-Fi works behind firewall
- [ ] Tailscale restricted remote access works
- [ ] No public management services exposed
- [ ] Rollback and recovery tested
- [ ] Public and private documentation separated
