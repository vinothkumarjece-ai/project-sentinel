---
Document Name : Sentinel Evidence Contract
Version       : 0.1
Status        : Draft
Classification: Core Intellectual Property
Owner         : Founding Team
Repository    : Project Sentinel
Review Cycle  : Architecture
Last Updated  : 08-Aug-2026
---

# Sentinel Evidence Contract

## 1. Purpose

The Sentinel Evidence Contract defines what information Project Sentinel can consume, how that information is evaluated, what intelligence can be derived from it, and what limitations exist when evidence is unavailable.

The contract establishes a clear boundary between:

- What the enterprise provides.
- What Sentinel observes.
- What Sentinel derives.
- What Sentinel infers.
- What Sentinel does not know.

The objective is to allow Sentinel to deliver useful intelligence without requiring unrestricted access to customer infrastructure.

---

# 2. Core Philosophy

> **Sentinel should request the minimum evidence required to produce the maximum useful intelligence.**

Customer network access shall not be a mandatory prerequisite for Sentinel adoption.

Sentinel shall progressively increase its intelligence as trusted evidence becomes available.

---

# 3. Evidence Lifecycle

Every evidence item follows a common lifecycle.

```text
Source
  ↓
Collection
  ↓
Validation
  ↓
Normalization
  ↓
Classification
  ↓
Correlation
  ↓
Reasoning
  ↓
Intelligence
```

Evidence shall retain its origin and relevant metadata throughout this lifecycle.

---

# 4. Evidence Sources

Evidence may originate from multiple sources.

## 4.1 Customer-Provided Information

Examples:

- Network diagrams
- Device inventory
- Configuration exports
- Incident records
- Change records
- Maintenance schedules
- Support matrices
- Business service information
- Vendor information
- Operational procedures

---

## 4.2 Enterprise Platforms

Examples:

- ITSM
- CMDB
- Monitoring platforms
- Network management platforms
- Cloud management platforms
- Virtualization platforms
- Configuration management systems
- Identity platforms

---

## 4.3 Network Telemetry

Examples:

- SNMP
- Syslog
- NetFlow
- IPFIX
- sFlow
- Streaming telemetry
- Device APIs
- Routing information
- Interface statistics

---

## 4.4 Infrastructure Evidence

Examples:

- Device configuration
- Hardware information
- Interface information
- Routing tables
- ARP tables
- MAC address tables
- LLDP/CDP information
- VLAN information
- VRF information
- Protocol state

---

## 4.5 External Evidence

Examples:

- ISP notifications
- Vendor advisories
- Cloud provider status
- Weather events
- Public service disruption information
- Third-party service notifications

External evidence shall be clearly identified as externally sourced.

---

# 5. Evidence Access Levels

Sentinel shall support progressive evidence access.

## Level 0 — Context Only

No customer infrastructure integration.

Possible evidence:

- Enterprise description
- Business services
- Public documentation
- Customer-provided operational context

Sentinel capability:

- Basic enterprise modelling
- Initial context building
- Knowledge organization
- Preparation for deeper integration

Limitations:

- No real-time infrastructure awareness
- No direct topology discovery
- Limited incident reasoning

---

# Level 1 — Customer-Provided Evidence

Customer provides selected information.

Examples:

- Device inventory
- Configuration exports
- Network diagrams
- Incident history
- Change history
- Maintenance information

Sentinel capability:

- Device classification
- Initial topology understanding
- Historical analysis
- Incident correlation
- Evidence-based reasoning

Limitations:

- Information may become stale
- Real-time state may be unavailable
- Completeness depends on customer-provided evidence

---

# Level 2 — Approved Platform Integration

Sentinel connects to approved enterprise systems using controlled interfaces.

Examples:

- ITSM APIs
- CMDB APIs
- Monitoring APIs
- Cloud APIs
- Virtualization APIs

Preferred access:

- Read-only
- Scoped
- Auditable
- Customer controlled

Sentinel capability:

- Improved real-time context
- Automated incident correlation
- Better ownership understanding
- Better infrastructure awareness

---

# Level 3 — Read-Only Infrastructure Telemetry

Customer provides approved read-only infrastructure evidence.

Examples:

- SNMP
- Syslog
- Flow telemetry
- Streaming telemetry
- Device APIs
- Routing information
- Interface information

Sentinel capability:

- Dynamic topology understanding
- Device health analysis
- Path analysis
- Interface analysis
- Traffic intelligence
- Faster incident reasoning

---

# Level 4 — Advanced Enterprise Integration

Sentinel may receive richer enterprise-approved evidence across multiple operational domains.

Examples:

- Network
- Security
- Compute
- Cloud
- Application
- Identity
- Business services

This level enables broader enterprise operational intelligence.

Advanced integration remains subject to customer security policy and architecture.

---

# 6. Evidence Priority

Not all evidence has equal operational value.

Sentinel shall prioritize evidence based on:

- Incident relevance
- Business impact
- Reliability
- Freshness
- Completeness
- Availability
- Collection cost
- Security sensitivity

The system should prefer high-value evidence before requesting or processing lower-value information.

---

# 7. Minimum Evidence Principle

Sentinel shall identify the Minimum Evidence Set required to answer a specific operational question.

Example:

Question:

> Why is a branch unreachable?

Potential minimum evidence:

- Branch gateway availability
- Adjacent device state
- WAN circuit state
- Power evidence
- Maintenance status
- Recent changes

Sentinel should not request unrelated enterprise information merely because it is available.

---

# 8. Evidence Substitution

Sentinel shall determine whether missing evidence can be derived from another source.

Example:

If a topology diagram is unavailable, Sentinel may derive portions of topology using:

- LLDP/CDP
- Routing information
- Interface information
- ARP/MAC relationships
- Monitoring relationships
- Flow data

The system should avoid asking customers to manually provide information that can reasonably be derived from trusted evidence.

---

# 9. Evidence Sufficiency

Before producing a strong conclusion, Sentinel shall evaluate whether available evidence is sufficient.

Possible states:

```text
Sufficient
Partially Sufficient
Insufficient
Conflicting
Unknown
```

Insufficient evidence shall not be silently converted into a confident conclusion.

---

# 10. Evidence Provenance

Every important evidence item shall retain provenance.

The provenance model should identify:

- Source
- Collection method
- Collection time
- Source timestamp where available
- Evidence type
- Transformation history
- Confidence
- Retention status

This allows Sentinel to explain how information entered its reasoning process.

---

# 11. Evidence Freshness

Evidence shall have a context-dependent freshness requirement.

Examples:

Device availability:

- Near real-time evidence preferred.

Hardware model:

- May remain valid for extended periods.

Network topology:

- May require periodic validation.

Business ownership:

- May change independently of technical telemetry.

Sentinel shall avoid treating all evidence as equally time-sensitive.

---

# 12. Evidence Reliability

Evidence reliability shall depend on the source and context.

Potential evidence sources include:

- Direct device telemetry
- Enterprise monitoring
- ITSM
- CMDB
- Engineer observation
- User report
- Vendor notification
- External source

Sentinel shall not assume that one source is always correct.

Evidence reliability may be adjusted based on historical consistency and source behaviour where appropriate.

---

# 13. Conflicting Evidence

When evidence conflicts, Sentinel shall preserve the conflict.

Example:

```text
Monitoring:
Device unreachable

Device API:
Device reachable

Adjacent device:
Interface operational
```

Sentinel shall not silently select one observation.

It should report:

> Conflicting evidence detected.

Then determine what additional evidence could resolve the conflict.

---

# 14. Evidence Classification

Evidence shall be classified according to sensitivity.

Possible categories:

- Public
- Operational
- Confidential
- Restricted

Restricted information such as:

- Passwords
- Private keys
- Authentication secrets

shall not be intentionally collected as normal operational evidence.

---

# 15. Customer Data Ownership

Customer-provided and customer-derived operational information remains subject to the customer's contractual and security requirements.

Sentinel shall support:

- Customer-controlled retention
- Customer-controlled deletion
- Data export
- Access auditing
- Appropriate data segregation
- Configurable storage policies

---

# 16. Evidence Minimization

Sentinel shall avoid collecting information that is not required for its intended purpose.

Examples:

If the objective is:

> Determine WAN availability.

Sentinel should not automatically collect:

- Employee personal information
- Unrelated application content
- Unrelated security data
- Unrelated business records

Purpose determines evidence requirements.

---

# 17. Identity and User Evidence

Where identity-related evidence is available and authorized, Sentinel may correlate:

```text
User
  ↓
Identity Group
  ↓
Device
  ↓
Network Location
  ↓
VLAN / Subnet
  ↓
Application
  ↓
Destination
```

This capability shall be subject to customer authorization, privacy requirements and data minimization.

Individual-level information shall not be exposed to unauthorized users.

---

# 18. Network Evidence

Where authorized, Sentinel may consume:

- IPv4
- IPv6
- MAC addresses
- Interfaces
- VLANs
- VRFs
- Routes
- Protocol states
- Neighbour relationships
- Link statistics
- Traffic statistics
- Circuit information

This information may be used to understand connectivity and infrastructure relationships.

---

# 19. Protocol Awareness

Sentinel shall support evidence associated with multiple protocols.

Examples:

- IPv4
- IPv6
- TCP
- UDP
- ICMP
- ARP
- DHCP
- DNS
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
- IPsec
- GRE

The evidence model shall remain extensible.

---

# 20. Physical Infrastructure Evidence

Where available, Sentinel may consume information relating to:

- Cable type
- Fibre links
- Copper links
- Patch panels
- Physical interfaces
- Rack location
- Power source
- UPS
- PDU
- Physical path

Physical evidence may improve fault isolation and reduce unnecessary field visits.

---

# 21. Virtual and Cloud Evidence

The Evidence Contract shall support virtualized and cloud environments.

Examples:

- Virtual machines
- Hypervisors
- Clusters
- Containers
- Kubernetes
- Cloud networks
- Cloud interfaces
- Security groups
- Load balancers
- Cloud circuits
- Managed services

Sentinel shall not assume that physical infrastructure is the primary source of enterprise connectivity.

---

# 22. Evidence for Path Analysis

Where sufficient evidence exists, Sentinel should be able to construct a probable or confirmed path.

Example:

```text
Source
 ↓
Access Network
 ↓
LAN
 ↓
Firewall
 ↓
WAN
 ↓
ISP
 ↓
Destination
```

Each path element shall carry its evidence and confidence.

Sentinel shall distinguish:

**Confirmed Path**

from

**Inferred Path**

and

**Unknown Path Segment**

---

# 23. Evidence for Incident Investigation

For each incident, Sentinel should dynamically determine the evidence required.

Example:

```text
Incident:
Application unreachable

Initial evidence:
Application alert

Sentinel identifies:
Network dependency

Required evidence:
- Application server state
- Network path
- Firewall state
- DNS
- Load balancer
- Recent changes
```

The required evidence shall evolve as the investigation progresses.

---

# 24. Evidence and Manual Interaction

Manual engineer input shall be minimized.

Sentinel should first use:

1. Automatically available evidence.
2. Previously collected enterprise knowledge.
3. Existing platform integrations.
4. Derived evidence.
5. Only then request targeted human confirmation.

When human input is required, Sentinel should ask the smallest possible question.

Example:

Instead of:

> "Please provide complete network details."

Sentinel should ask:

> "Can you confirm whether the branch has commercial power?"

This principle reduces operational interruption.

---

# 25. Evidence Requests

When additional evidence is required, Sentinel shall explain:

- What is missing.
- Why it matters.
- How it will change the investigation.
- Who is authorized to provide it.
- Whether another source could provide it.

Example:

> Missing: ISP circuit status  
> Reason: Current evidence cannot distinguish between customer-edge failure and provider-side failure.  
> Required source: WAN monitoring or ISP portal.

---

# 26. Evidence Confidence

Evidence shall contribute to the Confidence Intelligence Engine.

Evidence may increase confidence when:

- Multiple independent sources agree.
- Evidence is recent.
- Evidence is directly relevant.
- Source reliability is high.

Evidence may reduce confidence when:

- Sources conflict.
- Evidence is outdated.
- Evidence is incomplete.
- Source reliability is uncertain.

---

# 27. Evidence and Unknown States

Unknown is a valid operational state.

Examples:

```text
Power status: Unknown
Cable type: Unknown
Adjacent device: Unknown
ISP status: Unknown
Business impact: Unknown
```

Sentinel shall not convert unknown information into assumptions.

Unknown information may become a targeted evidence requirement.

---

# 28. Evidence Lifecycle and Change

Evidence may become obsolete.

Examples:

- Device replaced
- Circuit changed
- VLAN redesigned
- Application migrated
- Team ownership changed

Sentinel shall maintain evidence history where appropriate and distinguish current evidence from historical evidence.

---

# 29. Evidence Security

Evidence collection shall follow Security by Design principles.

Preferred mechanisms:

- Least privilege
- Read-only access
- Scoped permissions
- Encryption
- Audit logging
- Customer-controlled credentials
- Customer-controlled integration
- Data minimization

Sentinel shall never require unrestricted administrative access merely because a richer integration is technically possible.

---

# 30. Evidence Contract and Enterprise Adaptation

The Enterprise Adaptation Engine determines which evidence sources are available and authorized within a particular enterprise.

Therefore:

```text
Enterprise Context
       ↓
Available Evidence Sources
       ↓
Evidence Contract
       ↓
Evidence Intelligence
       ↓
Reasoning
```

Different enterprises may provide different evidence while using the same Sentinel intelligence architecture.

---

# 31. Evidence Contract and Cognitive Architecture

The Evidence Contract provides the boundary between the external enterprise environment and the Project Sentinel Cognitive Architecture.

```text
Enterprise
    ↓
Approved Evidence
    ↓
Evidence Contract
    ↓
Evidence Intelligence
    ↓
Enterprise Memory Fabric
    ↓
Operational Reasoning
    ↓
Confidence
    ↓
Decision Intelligence
```

---

# 32. Evidence Quality States

Sentinel shall maintain a clear distinction between:

### Available

Evidence is currently available.

### Available but Stale

Evidence exists but may no longer represent current state.

### Partially Available

Some required attributes exist while others are missing.

### Derived

Information has been calculated or inferred from available evidence.

### Conflicting

Multiple sources disagree.

### Unavailable

The evidence source exists but cannot currently be accessed.

### Not Authorized

The evidence may exist but Sentinel is not permitted to access it.

### Unknown

Sentinel has no reliable evidence regarding the requested information.

These states must not be treated as equivalent.

---

# 33. Evidence Readiness

Before executing a high-impact operational recommendation, Sentinel should evaluate evidence readiness.

Example:

```text
Business Impact: High
Decision Risk: High
Evidence Readiness: Low
```

Expected behaviour:

> Do not make a strong recommendation. Identify the minimum additional evidence required.

---

# 34. Future Compatibility

The Evidence Contract shall remain technology independent.

Future evidence sources may include:

- New network telemetry protocols
- AI-generated operational summaries
- Digital twin data
- Edge infrastructure
- 5G
- Satellite connectivity
- New cloud platforms
- New virtualization technologies
- Emerging observability platforms

New evidence sources should be added without redesigning the core Cognitive Architecture.

---

# 35. Success Criteria

The Sentinel Evidence Contract succeeds when:

1. Sentinel can provide useful intelligence without direct customer network access.
2. Customers can progressively increase evidence availability.
3. Sentinel clearly distinguishes fact, inference and unknown.
4. Evidence provenance is maintained.
5. Evidence conflicts are visible.
6. Engineers are asked for minimal information.
7. Existing enterprise tools can be used as evidence sources.
8. Vendor-specific evidence can be normalized into vendor-neutral concepts.
9. Security restrictions are respected.
10. Future evidence sources can be added without redesigning the platform.

---

# 36. Summary

The Sentinel Evidence Contract establishes the boundary between enterprise information and Sentinel intelligence.

Its central principle is:

> **Sentinel does not require everything. Sentinel requires the right evidence.**

The platform shall progressively improve its understanding as trusted evidence becomes available.

Where evidence is missing, Sentinel shall identify the gap.

Where evidence conflicts, Sentinel shall expose the conflict.

Where evidence is insufficient, Sentinel shall say so.

Where evidence can be derived, Sentinel shall derive it rather than unnecessarily burdening engineers.

This evidence-first architecture enables Project Sentinel to deliver operational intelligence while minimizing customer integration effort, security exposure and manual intervention.
