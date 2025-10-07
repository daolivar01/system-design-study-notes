# Week 1: Thinking in Systems

## 🧩 1. System Boundaries & Requirements

**System boundaries** define what’s _inside_ (the system’s responsibilities, logic, and owned data) versus what’s _outside_ (external users, third-party APIs, or dependent services).
Clearly defining boundaries helps avoid scope creep and clarifies integration points.

**Functional requirements** describe _what the system should do_ — its capabilities and behaviors (e.g., “users can upload and share images”).
**Non-functional requirements (NFRs)** describe _how the system performs_ — qualities such as latency, availability, scalability, and security.
They’re often the deciding factors in architectural tradeoffs.

> Example:
>
> - Functional: “Support real-time chat between users.”
> - Non-functional: “Each message must be delivered in under 200 ms and persisted reliably.”

---

## ⚙️ 2. Core Performance Dimensions

These are the key “axes” of system behavior — understanding their relationships is central to good design.

| Dimension        | Definition                                                                                                     | Example                                       |
| ---------------- | -------------------------------------------------------------------------------------------------------------- | --------------------------------------------- |
| **Latency**      | Time taken to process a single request end-to-end.                                                             | 120 ms to return a search result              |
| **Throughput**   | Number of requests handled per unit time.                                                                      | 10,000 requests/sec                           |
| **Availability** | Probability the system is operational when needed (often expressed as a percentage or “nines”).                | 99.9% uptime = ~8.7 hours downtime/year       |
| **Reliability**  | Accuracy and consistency of system behavior and data over time. Includes fault tolerance and data durability.  | Messages are never lost or duplicated         |
| **Scalability**  | Ability to handle increased load (users, data, requests) by adding resources predictably and cost-effectively. | Auto-scaling API layer to handle peak traffic |

> 🔄 These dimensions often trade off against each other — e.g., increasing consistency can raise latency, improving availability may complicate reliability guarantees.

---

## 🏗️ 3. High-Level Architecture Patterns

### **Monolithic Architecture**

- **Definition:** Entire application deployed as a single unit (shared codebase, shared database).
- **Pros:** Simple to develop and deploy; low operational overhead.
- **Cons:** Hard to scale specific components, limited fault isolation, slower team velocity at scale.

### **Microservices Architecture**

- **Definition:** Application decomposed into independently deployable services, often aligned with **bounded contexts** in domain-driven design (e.g., Auth, Billing, Analytics).
- **Pros:** Independent scaling and deployment, strong team ownership, improved modularity.
- **Cons:** Distributed system complexity — inter-service communication, data consistency, and observability become harder.

### **Service-Oriented Architecture (SOA)**

- **Definition:** Predecessor to microservices; promotes service reuse through a central enterprise service bus (ESB).
- **Pros:** Encourages modularity and interoperability across large organizations.
- **Cons:** Heavyweight communication middleware; ESB can become a bottleneck or single point of failure.
