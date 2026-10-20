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

## Discovery update — 2026-10-19

**Sanitized public summary:** A 5 Gbps fiber plan uses an ISP-provided fiber termination device and a consumer Wi-Fi 6E router currently performing DHCP, NAT and wireless access. The router receives WAN settings dynamically and uses a 2.5GbE WAN interface. The intended migration is to a tested 10GbE-capable firewall with the existing router retained as an access point.

**Verified:** WAN DHCP mode, 2.5GbE WAN selection, wireless-router operating mode, router firmware checked against the vendor's current model-specific support page.

**Not yet verified:** Exact ONT manufacturer/model, ONT Ethernet handoff speed and media, required ISP settings, and performance of a candidate firewall under planned IDS/IPS load.

**Private-only discovery details:** Actual installed DHCP pool, current gateway, WAN address, WAN MAC, exported configuration and any device labels. Do not include these in issues, screenshots or commit messages.

**Next gate:** Identify ONT model and 10GbE-capable Ethernet handoff; then choose firewall and switch with verified cabling and throughput.

## ONT capability finding — 2026-10-19

**Confirmed physical model:** Calix GigaPoint GP1100X. Per Calix's official [ONT specifications](https://www.calix.com/products/platform/unlimited-subscriber/gigapoint-ont-onu.html), it uses XGS-PON optical transport but provides only **one 2.5GbE RJ45 customer-facing Ethernet port**. The advertised fiber technology speed is not equivalent to a 10GbE LAN handoff.

**Engineering implication:** The present ONT Ethernet output cannot deliver 5 Gbps to a downstream router through its single Ethernet port. A 10GbE firewall upgrade alone will not solve the WAN bottleneck.

**Next action:** Request provider confirmation of the account speed tier and a supported replacement ONT with a 10GbE RJ45 customer handoff (for example, Calix GP1101X *if supported by the provider*). Verify provisioning, installation, price, media, and transition/rollback before buying a firewall.

**Privacy:** Do not publish photographs of hardware labels, serial numbers, registration identifiers, barcodes, MAC addresses, or actual ISP account records.
