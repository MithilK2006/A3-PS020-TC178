# AIORI-3 Hackathon — Problem Statement PS-020

## Local SRv6 Path Steering and Measured Failure Recovery
**Category:** 6G & Future Networks  
**Team Name:** NODEX  
**Team Code:** TC178  
**Repository:** [A3-PS020-TC178](https://github.com/MithilK2006/A3-PS020-TC178)

---

### 👥 Team Members & Presenters
* **Mithil Khobragade** — [khobragademithil45@gmail.com](mailto:khobragademithil45@gmail.com)
* **Sharad Kalmani** — [sharadkalamani3@gmail.com](mailto:sharadkalamani3@gmail.com)

---

## 📺 Team Video Walkthrough & Orientation

[![Watch the Video Presentation](https://img.shields.io/badge/YouTube-Video_Demonstration-red?style=for-the-badge&logo=youtube)](https://youtu.be/NiIbHxnKrSQ?si=Obk-cFiCMqS2Yi7Z)

> **Video Link:** [https://youtu.be/NiIbHxnKrSQ?si=Obk-cFiCMqS2Yi7Z](https://youtu.be/NiIbHxnKrSQ?si=Obk-cFiCMqS2Yi7Z)

In this video presentation, our team introduces:
1. Team members and assigned roles/responsibilities.
2. Problem understanding and research scope for **PS-020**.
3. Overview of our virtual network testbed and GNS3 setup.
4. Proposed implementation of SRv6 explicit path steering and backup policy switching upon link failure.

---

## 📌 Executive Summary & Abstract

Traditional IP networks forward packets hop-by-hop, where intermediate routers independently select the next hop based solely on destination lookup in their local routing tables. In contrast, **Segment Routing over IPv6 (SRv6)** enables source-driven routing by encoding an ordered list of instructions known as Segment Identifiers (SIDs) directly inside the IPv6 Segment Routing Header (SRH).

### Core Objectives:
* **Testbed Construction:** Build a repeatable 5-router virtual network testbed connecting source Host A to destination Host B.
* **Comparative Study:** Compare explicit SRv6 path steering against standard hop-by-hop IPv6 routing under identical topology, traffic, and link-down events.
* **Controlled Link Failure & Recovery:** Trigger controlled link interruption and measure recovery delay, packet loss, and header overhead.

---

## 🏗️ Architecture & Topology Design

```mermaid
flowchart LR
    HostA["Traffic Source\n(Host A)"] --> R1["Ingress Router\n(R1)"]
    
    subgraph Core Network
        R1 -->|Path A (Primary)| R2["Router 2\n(R2)"]
        R1 -->|Path B (Backup)| R3["Router 3\n(R3)"]
        R2 --> R4["Router 4\n(R4)"]
        R3 --> R4
        R4 --> R5["Egress Router\n(R5)"]
    end
    
    R5 --> HostB["Traffic Sink\n(Host B)"]
```

* **Primary Path (Path A):** `Host A ➔ R1 ➔ R2 ➔ R4 ➔ R5 ➔ Host B`
* **Backup Path (Path B):** `Host A ➔ R1 ➔ R3 ➔ R4 ➔ R5 ➔ Host B`
* **Failure Simulation:** Controlled shutdown of active forwarding link to observe and benchmark policy switchover and convergence times.

---

## 📁 Repository Deliverables & Resources

| Asset | Format | Location / Link |
| :--- | :--- | :--- |
| **Presentation PDF** | PDF (.pdf) | [📄 View Presentation Directly in GitHub](PS-020_SRv6_Hackathon_Presentation.pdf) |
| **Proposed Structure Reference** | PDF (.pdf) | [📄 View Structure Reference in GitHub](PPT%20Presentation%20Proposed-structure-hackathon.pdf) |
| **Video Walkthrough** | YouTube | [▶️ Watch on YouTube](https://youtu.be/NiIbHxnKrSQ?si=Obk-cFiCMqS2Yi7Z) |

---

## 📖 Key Standards & RFC References

1. **RFC 8402** — *Segment Routing Architecture* (IETF, 2018)
2. **RFC 8754** — *IPv6 Segment Routing Header (SRH)* (IETF, 2020)
3. **RFC 8986** — *SRv6 Network Programming* (IETF, 2021)
4. **RFC 8200** — *Internet Protocol, Version 6 (IPv6) Specification*