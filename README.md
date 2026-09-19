<img width="1238" height="568" alt="Screenshot 2026-09-19 145024" src="https://github.com/user-attachments/assets/78d727f7-f761-4d8d-97f2-f3bb024e1ac4" /># 📱 Food Delivery Platform – Real-Time Order Tracking & Communication Enhancement
### Comprehensive Business Requirement Document (BRD) & System Analysis

---

## 📌 Project Overview
* **Role:** Business Analyst Intern
* **Domain:** Food Delivery & Logistics
* **Deliverables:** Business Requirement Document (BRD), UML Use Case Modeling, End-to-End Activity Flowcharts, Risk Analysis

This project addresses post-order transparency challenges within a food delivery mobile platform by specifying functional architectures for live GPS telemetry, dynamic ETA forecasting, and secure in-app telecommunication bridges.

---

## 🎯 Business Problem & Objectives
* **Problem Statement:** Ambiguity surrounding food preparation stages and rider dispatch resulted in a **35% surge in customer support inquiries** related to order status and arrival time.
* **Primary Objective:** Reduce ETA-related support tickets by **25% within 3 months** of rollout and enhance the post-checkout Customer Satisfaction (CSAT) rating from 3.8 to 4.5.

---

## 👥 Stakeholder Matrix
* **Customer (End User):** Tracks real-time order progression and receives meal handoffs.
* **Delivery Rider:** Provides real-time GPS telemetry and manages order drop-offs.
* **Restaurant Partner:** Manages order acceptance and kitchen fulfillment stages.
* **Customer Support:** Handles operational escalations and logistics delays.
* **Engineering Team:** Builds geolocation APIs, WebSocket infrastructure, and UI frontends.

---

## ⚙️ Functional & Non-Functional Requirements

### Key Functional Requirements (FR)
1. **Real-Time State Pipeline:** Transitions order status across `Placed` $\rightarrow$ `Accepted` $\rightarrow$ `Preparing` $\rightarrow$ `Out for Delivery` $\rightarrow$ `Delivered`.
2. **Live Geolocation Tracking:** Streams rider coordinates to the mobile map interface at $\le$ 10-second polling intervals.
3. **Dynamic ETA Computation:** Recalculates remaining delivery minutes dynamically leveraging route distance and live road congestion metrics.
4. **Automated Notification Engine:** Triggers instant push notifications and SMS upon every core state change ($\le$ 5s delivery target).
5. **Masked Telephony Bridge:** Enables mutual, one-tap VoIP/proxy calling between customer and rider without exposing PII phone numbers.

### Key Non-Functional Requirements (NFR)
* **Latency:** Map tile rendering and live telemetry refreshes under 2 seconds over standard mobile connections.
* **Scalability:** Architected to handle 10,000+ concurrent active tracking sessions during peak dining hours.
* **Data Security:** Strict encryption standards (TLS 1.3 in transit, AES-256 at rest) for all GPS coordinates and user data.

---

## 📝 Agile User Stories & Acceptance Criteria

### User Story 01: Live Route Tracking
> **As a** Customer,  
> **I want to** observe my delivery partner moving on an interactive live map with an accurate ETA,  
> **So that** I know exactly when to receive my order without anxiety.

* **Scenario:** Seamless live transit tracking
  * **Given** an order status is updated to `Out for Delivery`,
  * **When** the customer navigates to the active tracking view,
  * **Then** the map renders the rider pin, destination pin, and route polyline,
  * **And** the estimated arrival time updates dynamically every 60 seconds.

### User Story 02: Masked Driver Contact
> **As a** Delivery Rider,  
> **I want to** initiate a phone call with the customer via a masked channel,  
> **So that** I can coordinate the delivery handoff without sharing personal contact details.

* **Scenario:** Masked call initiation
  * **Given** an order is currently in transit,
  * **When** either party taps the `Call` button,
  * **Then** the telephony server connects the call via a virtual proxy number,
  * **And** no personal telephone numbers are exposed on the screen.

---

## 📊 Visual System Architecture & Diagrams

### 1. System Use Case Diagram
<img width="847" height="645" alt="Screenshot 2026-09-19 132906" src="https://github.com/user-attachments/assets/591417bb-5ec9-4f5c-878d-66eb0f09ef7d" />


### 2. End-to-End Process Flowchart
<img width="516" height="678" alt="Screenshot 2026-09-19 133123" src="https://github.com/user-attachments/assets/ecd85100-8e23-4ad1-aba7-d05571fbdb3b" />


---

## ⚠️ Risk Management & Mitigation
* **GPS Signal Drift & Battery Consumption:** Mitigated via adaptive polling algorithms that adjust GPS sampling intervals based on vehicle velocity.
* **Customer Data Privacy:** Protected using temporary masked proxy numbers and strict zero-logging policies for direct rider-customer calls.
* **Peak Traffic Latency:** Addressed via lightweight WebSocket protocol streaming and auto-scaling microservices.

---

## 📄 Complete Documentation
Download the complete, officially formatted Business Requirement Document (BRD) PDF from this repository.

## 📊 Agile & Sprint Management (Jira)

The end-to-end implementation requirements were broken down into functional Epics, Agile User Stories, and estimated using Story Points via Jira Software.

* **Tracking Board:** Scrum Workflow (`To Do` ➔ `In Progress` ➔ `Done`)
* **Estimation:** Fibonacci Story Points applied based on technical complexity (Telemetry Engine: 5 pts, Proxy Calling: 3 pts).
* **Acceptance Criteria:** Integrated Gherkin syntax directly into ticket descriptions for engineering alignment.

![Jira Scrum Board](jira-scrum-board.png)







