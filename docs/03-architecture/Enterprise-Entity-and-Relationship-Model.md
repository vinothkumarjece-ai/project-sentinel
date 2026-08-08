---
Document Name : Enterprise Entity & Relationship Model
Version       : 0.1
Status        : Draft
Classification: Core Intellectual Property
Owner         : Founding Team
Repository    : Project Sentinel
Review Cycle  : Architecture
Last Updated  : 08-Aug-2026
---

# Enterprise Entity & Relationship Model

## 1. Purpose

The Enterprise Entity & Relationship Model (EERM) defines how Project Sentinel represents the entities that exist within an enterprise and, more importantly, how those entities are related.

Sentinel shall not treat enterprise infrastructure as a collection of isolated devices.

Enterprise operations are based on relationships.

A device may support a service.

A service may support a business function.

A user may belong to a department.

A device may belong to a VLAN.

A VLAN may connect through a switch.

A switch may depend on power, upstream connectivity and other infrastructure.

An incident may affect one or more of these relationships simultaneously.

The purpose of EERM is to provide a common structural model that allows Sentinel to understand these relationships consistently across different enterprises and technologies.

---

# 2. Core Philosophy

> **Entities provide context. Relationships provide understanding.**

Knowing that a router exists has limited operational value.

Knowing what the router connects to, what it supports, who owns it, which business services depend on it, what redundancy exists, and what incidents have previously affected it creates operational intelligence.

---

# 3. Objectives

EERM shall:

- Represent enterprise entities consistently.
- Represent relationships between entities.
- Support physical and logical infrastructure.
- Support business and organizational relationships.
- Support virtual and cloud environments.
- Support historical relationships.
- Support incident relationships.
- Support vendor and support relationships.
- Support future behavioural intelligence.
- Remain independent of vendor-specific terminology.

---

# 4. Entity Categories

Sentinel shall organize enterprise entities into logical categories.

## 4.1 Business Entities

Examples:

- Business Unit
- Business Service
- Business Application
- Customer Service
- Business Location
- Business Process

Business entities establish the business context of technical infrastructure.

---

## 4.2 Organizational Entities

Examples:

- Employee
- Team
- Department
- Operations Group
- Service Manager
- Incident Manager
- Support Organization
- Vendor Organization

Sentinel shall not assume that organizational structures are identical between enterprises.

---

## 4.3 Location Entities

Examples:

- Country
- Region
- City
- Campus
- Building
- Floor
- Data Centre
- Branch
- Remote Site

Location relationships may influence incident impact, redundancy and operational response.

---

## 4.4 Network Entities

Examples:

- Router
- Switch
- Firewall
- Wireless Controller
- Access Point
- Load Balancer
- WAN Circuit
- LAN Segment
- VLAN
- VRF
- Subnet
- IP Address
- Interface
- Port
- Network Path
- ISP
- Internet Connection

---

## 4.5 Physical Infrastructure Entities

Examples:

- Rack
- Power Source
- UPS
- PDU
- Cable
- Fibre Link
- Copper Link
- Patch Panel
- Physical Port
- Hardware Component

Physical relationships may be important when troubleshooting connectivity and infrastructure failures.

---

## 4.6 Compute Entities

Examples:

- Physical Server
- Virtual Machine
- Hypervisor
- Cluster
- Container
- Kubernetes Node
- Kubernetes Cluster
- Storage System
- Backup System

---

## 4.7 Cloud Entities

Examples:

- Cloud Provider
- Cloud Account
- Subscription
- Region
- Availability Zone
- Virtual Network
- Subnet
- Security Group
- Cloud Resource
- Managed Service

---

## 4.8 Security Entities

Examples:

- Security Device
- Security Policy
- VPN
- Identity Provider
- Authentication Service
- Endpoint Security Platform
- Security Zone
- Access Control

---

## 4.9 Operational Entities

Examples:

- Incident
- Major Incident
- Change
- Maintenance Activity
- Problem
- Known Error
- Workaround
- Standard Operating Procedure
- Escalation
- Vendor Case

---

# 5. Entity Identity

Every entity should have a stable Sentinel identity independent of how the customer names it.

Enterprise naming conventions may vary significantly.

Examples:

```text
NYC-CORE-RTR-01
CORE-RTR-NY-001
RTR01.NYC
Router-NewYork-01
```

These may represent the same type of entity even though naming conventions differ.

Sentinel shall therefore distinguish:

**Customer Identifier**

from

**Sentinel Entity Identity**

This allows Sentinel to understand different enterprise naming conventions without requiring a universal naming standard.

---

# 6. Technology Classification

Sentinel shall distinguish between:

- Customer naming
- Observed characteristics
- Vendor
- Model
- Device type
- Technology role
- Functional role

Device classification should not depend solely on hostname or naming convention.

Where sufficient evidence exists, Sentinel should infer device characteristics from configuration, telemetry, topology and observed behaviour.

---

# 7. Network Identity Model

Sentinel shall support both IPv4 and IPv6.

An entity may have:

- IPv4 address
- IPv6 address
- Multiple addresses
- Management address
- Service address
- Virtual address
- Loopback address
- NAT representation

IP addresses shall therefore be treated as attributes or relationships rather than permanent identities of physical devices.

---

# 8. Interface Model

An interface may contain relationships to:

- Physical device
- Interface identifier
- IP address
- VLAN
- VRF
- Cable
- Adjacent interface
- Link
- Protocol
- Operational state
- Administrative state
- Traffic statistics

Sentinel should preserve both logical and physical relationships where evidence is available.

---

# 9. Protocol Model

Sentinel shall represent network protocols independently of vendors.

Examples include:

- Ethernet
- ARP
- IPv4
- IPv6
- TCP
- UDP
- ICMP
- BGP
- OSPF
- IS-IS
- EIGRP
- MPLS
- VXLAN
- STP
- LACP
- LLDP
- CDP
- DHCP
- DNS
- SNMP
- IPsec
- GRE

The protocol model shall remain extensible as new technologies emerge.

---

# 10. Physical Connectivity Model

Where evidence is available, Sentinel should understand physical connectivity.

Example:

```text
Device A
  |
Interface A
  |
Fibre Cable
  |
Patch Panel
  |
Fibre Cable
  |
Interface B
  |
Device B
```

The model should allow different levels of certainty when physical connectivity is known, inferred or unknown.

---

# 11. Logical Connectivity Model

Sentinel shall represent logical connectivity independently of physical connectivity.

Example:

```text
User
  |
Access Point
  |
VLAN
  |
Switch
  |
Routing Domain
  |
Firewall
  |
WAN
  |
Application
```

Physical and logical relationships may both exist simultaneously.

---

# 12. User and Device Context

Where customer-authorized identity and network telemetry are available, Sentinel may associate:

```text
User
  ↓
Identity Group
  ↓
Device
  ↓
Access Point / Switch Port
  ↓
VLAN / Subnet
  ↓
Network Segment
  ↓
Application / Destination
```

This foundation allows future capabilities such as enterprise behaviour intelligence without requiring a redesign of the underlying model.

---

# 13. Group Relationships

Sentinel shall support multiple types of grouping.

Examples:

- HR Department
- Finance Department
- Network Operations
- Regional Office
- VLAN Group
- Application User Group
- Device Group
- Behavioural Group
- Security Group

A single entity may belong to multiple groups.

---

# 14. Business Dependency Model

Sentinel shall represent dependencies between technology and business.

Example:

```text
Business Process
      ↓
Business Service
      ↓
Application
      ↓
Compute
      ↓
Storage
      ↓
Network
      ↓
WAN / ISP
      ↓
Physical Location
```

This relationship allows Sentinel to determine potential business impact from technical events.

---

# 15. Ownership Relationships

Every entity may have one or more ownership relationships.

Examples:

- Technical Owner
- Operational Owner
- Business Owner
- Support Team
- Vendor
- Escalation Group

Ownership shall be configurable because enterprise responsibilities differ.

---

# 16. Support Model

Sentinel shall represent different support arrangements.

Examples:

```text
Network Segment A → Internal Network Team

Network Segment B → Managed Service Provider

Security Infrastructure → Security Team

WAN Circuit → ISP

Server Infrastructure → Infrastructure Team
```

The model shall support shared, outsourced and hybrid operational responsibilities.

---

# 17. Incident Relationships

An incident may be related to:

- Device
- Interface
- Circuit
- Application
- Business Service
- Location
- Team
- Vendor
- Change
- Maintenance
- Previous Incident

Example:

```text
Incident
  ↓
WAN Circuit
  ↓
ISP
  ↓
Branch
  ↓
Business Service
  ↓
Business Users
```

---

# 18. Change Relationships

A change may be associated with:

- Device
- Configuration
- Application
- Service
- Network path
- Security policy
- Infrastructure component

This allows Sentinel to evaluate whether recent changes may be relevant to an incident.

---

# 19. Historical Relationships

Relationships may change over time.

Examples:

- Device replaced.
- ISP changed.
- VLAN redesigned.
- Application migrated.
- Team ownership changed.
- Circuit upgraded.
- Network path changed.

Sentinel shall preserve historical context where appropriate.

Current relationships and historical relationships must not be treated as identical.

---

# 20. Relationship Confidence

Relationships may have different levels of certainty.

Sentinel shall distinguish between:

### Confirmed

Directly verified by a trusted source.

### Observed

Detected through operational telemetry or configuration.

### Inferred

Derived from multiple pieces of evidence.

### Reported

Provided by an authorized enterprise user or document.

### Unknown

Relationship has not yet been established.

This prevents inferred relationships from being presented as confirmed facts.

---

# 21. Relationship Lifecycle

Relationships may be:

- Created
- Verified
- Updated
- Suspended
- Replaced
- Retired

Historical relationships shall remain traceable where required.

---

# 22. Relationship Discovery

Sentinel may discover relationships through:

- Configuration
- Monitoring data
- Network topology
- IP information
- Routing information
- LLDP/CDP
- ARP
- Flow information
- CMDB
- ITSM
- Cloud inventory
- Virtualization platforms
- Enterprise documentation
- Authorized user input

No single discovery mechanism shall be assumed to be universally available.

---

# 23. Evidence-Based Relationships

Every discovered relationship should retain its source and supporting evidence.

Example:

```text
Switch A
   ↓ connected to
Router B

Evidence:
LLDP observation
Source:
Network monitoring platform
Observed:
2026-08-08 14:05
Confidence:
High
```

This allows Sentinel to explain why it believes a relationship exists.

---

# 24. Unknown Is a Valid State

Sentinel shall never create a relationship merely because one is expected.

If sufficient evidence does not exist:

> Relationship = Unknown

Unknown information shall become a potential evidence requirement rather than an invented fact.

---

# 25. Future Compatibility

The entity model shall be extensible without redesigning existing core relationships.

Future entities may include:

- IoT Devices
- Edge Computing
- 5G Infrastructure
- Satellite Connectivity
- AI Infrastructure
- Autonomous Systems
- New Cloud Services
- Emerging Network Technologies

The model must therefore avoid excessive dependency on current vendor terminology.

---

# 26. Architectural Relationship to Other Sentinel Components

EERM provides structural context to:

- Enterprise Intelligence Model
- Enterprise Memory Fabric
- Evidence Intelligence Engine
- Incident Understanding Engine
- Operational Reasoning Engine
- Confidence Intelligence Engine
- Decision Intelligence Engine
- Enterprise Adaptation Engine

The model is therefore a foundational component of the Project Sentinel Cognitive Architecture.

---

# 27. Design Principles

The Enterprise Entity & Relationship Model follows these principles:

- Relationships before isolated records.
- Vendor neutrality.
- Technology independence.
- Evidence before assumption.
- Current state separated from historical state.
- Unknown information remains unknown.
- Every important relationship should be explainable.
- Customer naming conventions must not limit Sentinel's understanding.
- The model must support future technologies.

---

# 28. Summary

The Enterprise Entity & Relationship Model provides Project Sentinel with a common structural language for understanding enterprises.

It allows Sentinel to connect:

- People
- Teams
- Locations
- Devices
- Networks
- Applications
- Business services
- Vendors
- Incidents
- Changes
- Physical infrastructure
- Virtual infrastructure
- Cloud infrastructure

into a connected operational model.

This model is intended to provide the structural foundation required for enterprise operational intelligence, reasoning, decision support and future behavioural intelligence.
