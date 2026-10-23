# Core switch expansion decision (candidate)

**Status: Research / not purchased.** The owner prefers to buy a long-lived managed core switch rather than replace a small two-uplink switch later.

## Leading candidate
**QNAP QSW-M3216R-8S8T:** eight 100M/1G/2.5G/5G/10G RJ45 ports plus eight 1G/10G SFP+ ports. Managed Layer 2, 802.1Q VLANs, ACLs and SNMP. Official specification: https://www.qnap.com/en-us/product/qsw-m3216r-8s8t

Retail price observed around $599 in October 2026; availability and price must be checked before purchase. No PoE ports; no expectation of full Layer 3 firewall routing. Fan noise, power and available switch space should be validated.

## Alternative
MikroTik CRS312-4C+8XG-RM: eight native multigig RJ45 ports and four RJ45/SFP+ combo ports (12 total 10G connections), four fans and RouterOS/SwOS. Vendor: https://mikrotik.com/product/crs312_4c_8xg_rm

## Planned topology
Provider GP1101X ONT -> purchased ASUS GT-BN98 Pro router -> one RJ45 10GbE port on managed core switch. Then TrueNAS, Proxmox, a future lab node, backup storage and workstation connect as needed. A future OPNsense firewall may be inserted upstream with the ASUS switched into AP mode; it is *not yet deployed*.

## Buying gate
- Confirm 10GBASE-T uplink compatibility and cable distance.
- Verify required native RJ45 vs SFP+ counts including 25–40% spare capacity.
- Plan separate PoE access switching if future APs/cameras need power.
- Verify desk/rack space, noise, UPS load and management support.
- Remember the switch does not add ports to the router or replace an inter-VLAN firewall.
- Sanitized examples only; no real network identity data.
