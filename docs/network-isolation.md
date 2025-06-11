# Double-NAT Isolation Build — 2025-06-05

> **Status:** COMPLETE ✅  
> The lab now lives on its own 10.77.0.0/24 subnet behind a spare Linksys router, which in turn sits behind the AT&T BGW-320 gateway.  
> No VMs yet—this file documents the physical wiring, router configs, and validation tests so recruiters can see the foundation is solid.

---

## 🖥️  Hardware / Cable Layout

```mermaid
flowchart LR
    Internet --> BGW["BGW 320 (192.168.1.xxx)"]
    BGW -->|LAN 1| HomePC["Host PC<br>192.168.1.xxx"]
    BGW -->|LAN 2| L_WAN["Linksys WAN"]
    subgraph LabLAN["Linksys LAN 10.77.0.0/24"]
        L_MGMT["Linksys<br>10.77.0.x"]
        LabNIC["Host PC (USB-Eth) 10.77.0.xx"]
        VMs["<future> VMs<br>10.77.0.x"]
    end
    L_WAN --> LabLAN
