<p align="center">
  <img src="https://raw.githubusercontent.com/MauriceBurt/Modular-Networks/main/Transparent_PNG.png" width="350"/>
</p>

<h1 align="center">Spark of Life Theatre Production Network Design</h1>

<p align="center">
A real-world network design demonstrating segmentation, controlled access, and secure production infrastructure in a live event environment.
</p>

<p align="center">
  <a href="https://github.com/MauriceBurt/Modular-Networks">
    <img src="https://img.shields.io/badge/Modular%20Networks-Main%20Repo-0A66C2?style=for-the-badge&logo=github"/>
  </a>
</p>

---

## 📌 Overview

This design represents a theatre production environment where multiple user groups require network access—without exposing critical systems.

The network supports:

- Guest Wi-Fi for audience members  
- Staff control systems (lighting, sound, operations)  
- Dedicated stage manager control device  
- IoT production devices on stage  
- A centralized server / portal  

The goal is simple:

> **Everything works — but only where it should.**

---

## 🧭 Repository Structure

🔧 **[Configs](./configs)**  
🗺️ **[Topology](./topology)**  
📸 **[Screenshots](./screenshots)**  
🏢 **[Floor Plan](./floor_plan)**  

---

### 🎟️ Guest Portal Access

Guest Wi-Fi is tied to a centralized event portal where attendees can:

- 🎭 Show details (schedule, cast, seating info)
- 🍔 Pre-order concessions for pickup (no POS integration needed)
- 📍 Other tour locations / upcoming shows
- 📢 Real-time announcements (delays, start times) 

This allows guests to stay connected to event services while remaining fully isolated from internal production systems.

---

## 🧩 Network Segmentation

The environment is divided into functional VLANs:

- **VLAN 10 — Staff Control**
- **VLAN 20 — Stage Manager Control (Dedicated Device)**
- **VLAN 30 — IoT Production (Stage)**
- **VLAN 40 — Guest Wi-Fi (Seating Areas)**
- **VLAN 50 — Server / Portal**
- **VLAN 999 — Disabled / Unused Ports**

Each VLAN is isolated to prevent unnecessary access between environments.

---

## 🔐 Security Implementation

### VLAN Segmentation
Logical separation ensures guests, staff, and production systems do not overlap unnecessarily.

---

### Stage Manager Isolation (VLAN 20)

A dedicated VLAN was created for the stage manager’s control device.

- Uses a /30 subnet to strictly limit available addresses  
- Provides controlled access to production systems  
- Isolated from guest and IoT traffic  

This ensures critical show operations remain stable and unaffected by general network activity.

---

### ACL Enforcement (Access Control)

Traffic is controlled intentionally:

- ❌ Guest → Staff / IoT / Control = **Blocked**  
- ✅ Guest → Server / Portal = **Allowed**  
- ✅ Staff → Internal Resources = **Allowed**  
- ❌ IoT → Internal Networks = **Restricted**  

This enforces **intent-based access**, not just connectivity.

---

### Physical Port Security

Unused ports are secured:

- Moved to **VLAN 999**
- **Administratively shut down**

#### Scenario:
A device attempts to connect to an unused wall port.

**Result:**
- No link  
- No IP assignment  
- No access  

---

## 🌐 Network Behavior

### 🎟️ Guest Users (VLAN 40)
- Connect via Wi-Fi  
- Receive IP via DHCP  
- Access only the server / portal  

---

### 🎛️ Staff & Control (VLAN 10)
- Access internal systems  
- Communicate with required resources  
- Maintain production control  

---

### 🎬 Stage Manager (VLAN 20)
- Dedicated control device (tablet)  
- Minimal subnet scope (/30)  
- Direct access to required production systems only  
- Isolated from guest traffic  

Designed for reliability and precision during live operation.

---

### 🎭 IoT Production (VLAN 30)
- Devices operate within isolated environment  
- Restricted from initiating unnecessary traffic  

---

## 🧪 Validation

Network behavior was verified using:

- DHCP lease validation  
- VLAN segmentation checks  
- Trunk verification  
- ACL match counters  
- ICMP testing (allowed vs blocked traffic)  

Expected results:

- Guest → Server: **Allowed**  
- Guest → Internal Networks: **Blocked**  
- Staff → Required Resources: **Allowed**  
- IoT → Internal Networks: **Restricted**  

---

## 🖼️ Visual Design

👉 **[View Theatre Network Layout](./floor_plan/Theatre_Network_Overview.png)**  

This diagram maps:

- Physical layout (stage, seating, control areas)  
- VLAN segmentation  
- Access behavior (allowed vs blocked)  
- Disabled port locations  

---

## 🛠️ Configurations

👉 **[View Configs](./configs)**  

Includes:

- Router-on-a-stick configuration  
- VLAN assignments  
- Trunk configuration  
- DHCP pools  
- ACL rules  

---

## 🗺️ Topology File

👉 **[Download Packet Tracer File](./topology/Spark_Of_Life_Theatre_Production.pkt)**  

---

## 📸 Screenshots

👉 **[View Screenshots](./screenshots)**  

Includes:

- Topology layout  
- VLAN segmentation  
- DHCP bindings  
- ACL enforcement  
- Validation testing  

---

## 🎯 Outcome

This design demonstrates:

- Secure segmentation across user groups  
- Controlled access using ACLs  
- Isolation of IoT production systems  
- Protection of internal resources  
- Real-world validation of network behavior  

---

## 🧰 Tools Used

- Cisco Packet Tracer  
- Cisco IOS CLI  
- Canva  
- Terminal  

---

## 📦 Modular Networks

Part of the  
👉 [Modular Networks Design Library](https://github.com/MauriceBurt/Modular-Networks)

Design-focused network engineering.

Not just configs — **systems that hold under pressure.**
