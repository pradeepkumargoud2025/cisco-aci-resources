# Infra VLAN Overview (Cisco ACI)

## What is Infra VLAN?

**Infra VLAN** is a dedicated VLAN used by the Cisco ACI fabric for internal infrastructure communication.  
It carries control plane and management traffic between:

- APIC ↔ Leaf
- Leaf ↔ Spine
- Leaf ↔ Leaf (via Spine)

Infra VLAN is **not used for tenant traffic**.

---

## Why Infra VLAN is Important?

ACI is a distributed fabric. Infra VLAN is required for:

- APIC management communication
- Fabric control plane stability
- Fabric discovery and topology updates
- Health and monitoring

If Infra VLAN fails, the entire fabric can become unstable.

---

## Infra VLAN Properties

| Property | Description |
|----------|-------------|
| Purpose | ACI internal communication |
| Traffic | Control plane & management |
| Used by | APIC, Leaf, Spine |
| Not used by | Tenant traffic |

# Infra VLAN in Spine-Leaf Architecture (ACI)

## Infra VLAN in Spine-Leaf

### APIC to Leaf
APIC uses Infra VLAN to:
- Send policies
- Receive telemetry
- Manage leaf switches

### Leaf to Spine
Spine carries control plane traffic between leaf switches.

### Leaf to Leaf
Leaf switches exchange:
- IS-IS routes
- Fabric discovery info
- Control updates

---

## Architecture Diagram

```mermaid
graph LR
    APIC[APIC Cluster]
    Leaf1[Leaf Switch 1]
    Leaf2[Leaf Switch 2]
    Spine[Spine Switch]

    APIC -- Infra VLAN --> Leaf1
    APIC -- Infra VLAN --> Leaf2
    Leaf1 -- Infra VLAN --> Spine
    Leaf2 -- Infra VLAN --> Spine

# Infra VLAN Troubleshooting (Cisco ACI)

## Symptoms of Infra VLAN Failure

- APIC unreachable
- Fabric nodes down
- IS-IS neighbors missing
- Fabric becomes unstable

show infra vlan
show vlan internal
show interface vlan <infra-vlan-id>
ping <APIC IP>
show isis neighbors

