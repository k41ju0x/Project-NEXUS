# GT-BN98 Pro: 10GbE WAN negotiation verified

**Date:** 2026-11-09

The owner reports the ASUS Router mobile app's Port Overview shows a **10 Gbps negotiated link** on the connection used for the GP1101X ONT to GT-BN98 Pro WAN. The router is connected over DHCP and the Windows 11 laptop can browse the web.

Baseline speed test from the laptop's 1.0 Gbps wired Ethernet interface: 933 Mbps down and 942.46 Mbps up; latency readings reported as 20/49/33 ms. This verifies healthy gigabit-client performance, **not** full 5 Gbps ISP throughput.

**Phase 1 accomplishments:** Calix GP1101X installed; BN98 Pro staged, security baseline configured, firmware build ending `_41973` verified, router cutover online; 10GbE WAN link negotiation verified.

**Follow-up:** validate NEXUS SSID connectivity, everyday clients and stability; benchmark >2.5Gbps throughput with a suitable wired multigigabit client or appropriate router-side test; later add managed core switch and UPS. Preserve old router and private backups for rollback.

No public IP, MACs, SSIDs, credentials or configuration files included.
