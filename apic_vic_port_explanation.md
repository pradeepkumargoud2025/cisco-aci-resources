# 📘 Cisco ACI APIC Cabling

---

## 1️⃣ APIC VIC Port Overview

- Modern APIC models (M3 / L3) have **4 physical ports** grouped into **logical pairs**:
  - **Port 1 & Port 2 → Logical Pair 1**
  - **Port 3 & Port 4 → Logical Pair 2**
- ✅ **Rule:** Connect **only one port per logical pair**

---

## 2️⃣ Why Do We Skip Ports?

- **Logical Constraint**
  - Ports in the same pair share the same internal path
  - Connecting both ports in a pair causes interface issues

- **High Availability**
  - APIC uses an **Active / Standby** connectivity model

- **Fabric Discovery & Resiliency**
  - Each link connects to a **different leaf switch**
  - Ensures APIC stays reachable during:
    - Leaf failure
    - ISSU / upgrades

---

## 3️⃣ Cabling Best Practices

- 🔌 **Maximum 2 cables per APIC**
  - One cable from each logical pair
- 🌿 **Connect to different leaf switches**
- ⚡ **10G SFP+ only**
  - 1G copper is typically **unsupported** for fabric ports

---

## 4️⃣ Cabling Diagram

![APIC to Leaf Cabling](./An_informative_digital_diagram_illustrates_the_rec.png)

- **Port 1 → Leaf Switch 1 (Active)**
- **Port 3 → Leaf Switch 2 (Standby)**
- 🚫 **Ports 2 & 4 remain unused**

---

## 5️⃣ Quick Reference Table

| Logical Pair | Physical Ports | Connected To        |
|--------------|---------------|---------------------|
| Pair 1       | Port 1 / 2    | Leaf Switch 1       |
| Pair 2       | Port 3 / 4    | Leaf Switch 2       |

---

## 💡 Interview Tip

> Always mention **logical port pairs + Active/Standby design**  
