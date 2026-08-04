# 🧩 LLD Roadmap — Concept Videos + Problem Solving

> **Part of the 6-month switch plan.** Sibling roadmaps: [🧠 DSA](./readme.md) · [🚀 Project + 📨 Apply](./project-roadmap.md) · [📅 Daily tracker](./daily-tracker.md).
> Curriculum source: [`lld_content_index.md`](./lld_content_index.md).

> **Phase 1 (May 28 → Sep 21):** Commute videos only — passive learning of concepts. Watch one section per calendar week per `daily-tracker.md`.
> **Phase 2 (Sep 22 → Nov 2):** Active morning practice — solve 2 problems/week (design diagram first ~30 min, then C++ implementation ~90 min). Mornings switch from DSA to LLD here.
> **Goal:** Be able to walk into an LLD interview and confidently design 8+ classic systems with proper class diagrams, design pattern usage, and concurrency considerations.

## 📺 Concept track (Phase 1 — commute videos, May 28 → Sep 21)

Source: `lld_content_index.md`. Watch in order. ~1 section per week.

| ✓ | Wk | Calendar | Section | Topics |
|---|----|----------|---------|--------|
| ☐ | 3  | May 26 – Jun 1 | **1. Introduction to LLD**       | Intro, Software Design Principles |
| ☐ | 4  | Jun 2 – 8      | **2. SOLID Principles**          | SRP, OCP, LSP, ISP, DIP |
| ☐ | 5  | Jun 9 – 15     | **3. UML**                       | UML overview, Class diagrams |
| ☐ | 6  | Jun 16 – 22    | **4. Creational Patterns** (pt 1) | Intro, Singleton, Factory Method, Builder |
| ☐ | 7  | Jun 23 – 29    | **4. Creational Patterns** (pt 2) | Abstract Factory, Prototype |
| ☐ | 8  | Jun 30 – Jul 6 | **5. Structural Patterns** (pt 1) | Adapter, Decorator, Facade, Composite |
| ☐ | 9  | Jul 7 – 13     | **5. Structural Patterns** (pt 2) | Proxy, Bridge, Flyweight |
| ☐ | 10 | Jul 14 – 20    | **6. Behavioural Patterns** (pt 1) | Iterator, Observer, Strategy, Command, Template |
| ☐ | 11 | Jul 21 – 27    | **6. Behavioural Patterns** (pt 2) | State, Chain of Responsibility, Visitor, Mediator, Memento |
| ☐ | 12 | Jul 28 – Aug 3 | **7. Concurrency** (pt 1)         | Multithreading basics, Thread management, Thread pools |
| ☐ | 13 | Aug 4 – 10     | **7. Concurrency** (pt 2)         | Thread safety, Locks, Deadlock prevention, Producer-Consumer |
| ☐ | 14 | Aug 11 – 17    | **8. Dependency Injection**       | DI principles + patterns |
| ☐ | 15 | Aug 18 – 24    | **9. Exceptions & Error Handling** | Exception handling, Building resilient systems |
| ☐ | 16 | Aug 25 – 31    | **10. Best Practices**            | APIs, Database design, How to approach LLD interview |
| ☐ | 17 | Sep 1 – 7      | Re-watch weakest sections         | — |
| ☐ | Buf| Sep 8 – 12     | Full review pass                  | — |

## 🛠️ Problem track (Phase 2 — daily-active practice, Sep 22 → Nov 2)

> Cadence: **2 problems/week** = 1 design + 1 code session each. Store solutions in `lld-solutions/<problem-slug>/` with `design.md` (class diagram + reasoning) and `*.cpp` (implementation).

| ✓ | # | Problem | Wk | Suggested mornings | Key patterns to apply |
|---|---|---------|----|--------------------|------------------------|
| ☐ | 1  | **Parking Lot**               | 17 | Sep 22 (design) · Sep 23 (code) | Strategy (pricing), Singleton (lot), Factory (slots) |
| ☐ | 2  | **Logging Framework**         | 17 | Sep 25 (design) · Sep 26 (code) | Chain of Responsibility, Singleton, Strategy (sinks) |
| ☐ | 3  | **Traffic Signal System**     | — *(skip if short on time, or do as bonus)* | — | State, Observer |
| ☐ | 4  | **Vending Machine**           | 18 | Sep 29 (design) · Sep 30 (code) | State, Command |
| ☐ | 5  | **Task Management System**    | 18 | Oct 2 (design) · Oct 3 (code) | Observer, Strategy (priority), Repository |
| ☐ | 6  | **PubSub System**             | 19 | Oct 6 (design) · Oct 7 (code) | Observer, Concurrency, Thread-safe queue |
| ☐ | 7  | **ATM Machine**               | 19 | Oct 9 (design) · Oct 10 (code) | State, Strategy (transactions) |
| ☐ | 8  | **Hotel Management**          | 20 | Oct 13 (design) · Oct 14 (code) | Factory, Strategy (pricing), Repository |
| ☐ | 9  | **Elevator System**           | 20 | Oct 16 (design) · Oct 17 (code) | State, Strategy (scheduling), Observer, Concurrency |
| ☐ | 10 | **Digital Wallet** (+ locking) | 21 | Oct 20 (design) · Oct 21 (code) | Concurrency (locks), Command (txn log), State |
| ☐ | 11 | **Ride Booking App**          | 21 | Oct 23 (design) · Oct 24 (code) | Strategy (matching), Observer (driver updates), State |
| ☐ | 12 | **Music Streaming Platform** (+ streaming protocols) | 22 | Oct 27 (design) · Oct 28 (code) | Strategy (codec), Decorator, Factory |

**Done criteria:** All 11 numbered problems coded + diagrammed. Re-code your 3 weakest in Week 24.
