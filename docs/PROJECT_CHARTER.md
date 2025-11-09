# AgOpenNext Project Charter

## Document Control
- **Version:** 0.6.0
- **Authors:** Jon & Markus  
- **License:** GPLv3  
- **Reviewers:** ???  
- **Approval Authority:** ???  
- **Review Cycle:** Ad-hoc when scope/assumptions shift materially  
- **Created:** 2025-10-20  
- **Last Updated:** 2025-11-08  
- **Status:** Draft for Community Review  
- **Link to Markdown:** link to the markdown version if moved to google docs (or perhaps link to google docs from the markdown version)
---

## 1. Executive Summary, Mission & Vision

AgOpenNext is a ground-up rebuild of AgOpenGPS, engineered for long-term stability, maintainability, and true cross-platform operation.  
Its purpose isn’t to add features, but to rebuild the foundation—keeping today’s workflows stable while enabling a decade of open, sustainable innovation.

**Mission:**  
Build a modern, modular guidance platform that preserves v6 reliability while eliminating technical debt and enabling open, frictionless contribution.

**Vision:**  
A community-driven precision agriculture platform that:  
- Runs consistently across all platforms.  
- Preserves v6 performance through automated and real-world validation.  
- Encourages experimentation through clear architecture and documented interfaces.  
- Grows an open ecosystem where innovation compounds instead of fragmenting.  
- Supports current hardware while remaining adaptable for what comes next.

Core principle: **Rewrite the foundation. Preserve the functionality. Unlock the future.**



## 2. Guiding Principles & Guardrails

- **Foundation first:** Modernize runtime, architecture, and tooling before expanding feature scope.  
- **Parity with intent:** Document all deviations from v6 behavior in ADRs, including validation and mitigation plans.  
- **Modular and extensible:** Maintain clear architectural seams that allow plugins and extensions without modifying Core.  
- **Inclusive contribution model:** Keep workflows open and reproducible across Windows and Linux, avoiding proprietary dependencies.  
- **Deterministic validation:** Use automated, replayable tests to detect regressions before they reach the field.  
- **Future-proof design:** Architecture anticipates future extensions without forcing premature implementation.


## 3. Goals & Success Criteria

| Goal | Success Criteria | Priority |
|------|------------------|-----------|
| **G1 — Functional Parity** | Pass all critical v6 field operation test suites; preserve essential guidance accuracy, GNSS processing, autosteer behavior. Any intentional retirements documented in ADRs with operator approval. | P0-Critical |
| **G2 — Cross-Platform Support** | Unified codebase for Windows and Linux builds with identical behavior. Non-gating stretch targets: Android (P2) and iOS Companion (P3). All builds must install cleanly and pass smoke tests. | P0-Critical |
| **G3 — Modern UI** | Avalonia UI achieves ≥30 FPS on reference hardware; functionally complete WinForms replacement | P0-Critical |
| **G4 — Test Infrastructure** | Unit tests ≥80 % coverage; integration tests 100 % on critical paths; all pass in CI before merge. | P0-Critical |
| **G5 — Architectural Clarity** | Clean separation: business logic, hardware abstraction, presentation; documented APIs | P0-Critical |
| **G6 — Developer Experience** | New contributor setup <1 hour on Windows or Linux; contribution checklists align with CI expectations. | P1-High |
| **G7 — Community Validation** | Field testing by ≥20 operators across ≥3 continents prior to general availability | P1-High |

---

## 4. Foundation Phase Boundaries (Non-Goals/Out of Scope for v1.0)

The foundation phase prioritizes modernization and stability.  
These areas are not part of the official GA scope but remain supported by architecture for future implementation.

- **New implement types / guidance algorithms:** Deferred (e.g., Stanley, MPC).  
- **Machine learning / AI:** Out of scope for v1.0.  
- **Cloud or data sync:** No built-in support; extension points only.  
- **Mobile clients:** Android P2; iOS companion P3.  
- **VR/AR or fleet tools:** Deferred until post-validation.  
- **CAN bus full implementation:** Architecture supports it; full feature set deferred post-GA.  
- **USB serial connections:** May be deprecated in favor of UDP-based communication.  
- **Data migration:** Limited to published tooling *(v5 and earlier: published migration tooling only)*.  

**Rationale:** Focused scope ensures a stable, modern core while keeping paths open for future expansion.



## 5. Scope

### 5.1 Version Policy
AgOpenNext targets the most recent stable combination of **.NET** and **Avalonia** verified to work together.  
- Develop on the latest **.NET** version fully supported by the current **Avalonia** release.  
- Upgrade only after CI passes and compatibility with existing modules is confirmed.  
- If Avalonia lags runtime support, remain on the last compatible .NET version until parity returns.

### 5.2 In Scope

**Platform Foundations:**  
- Unified .NET runtime (latest LTS or stable) and Avalonia UI
- CI/CD pipelines for Windows and Linux: installers, packages, containers, and systemd units (headless supported by design).  
- Modern graphics rendering via Avalonia (OpenGL/Vulkan).  

**Core Functionality (v6 Parity):**  
- GNSS integration (NTRIP, NMEA via UDP/serial) and autosteer guidance (AB lines, curves, contours, pivot).  
- Implement control (sections, rate, tramlines), field/boundary management, and vehicle calibration.  
- Data recording, telemetry hooks, and PGN compatibility for legacy hardware modules.  

**AgIO (Hardware Abstraction):**  
- Serial and UDP protocols, GNSS receivers using open formats (NMEA, UBX, RTCM), and IMU/heading sensors.  
- Implement control hardware (Arduino, Teensy, custom PCBs).  
- CAN bus architecture defined; implementation may follow post-GA.  
- Process boundaries under review during architecture phase; interface contracts defined regardless.  

**Architecture & Communication:**  
- Core guidance refactor isolating business logic, simulation hooks, and deterministic behavior.  
- Modernized AOG-Link V1 with backward compatibility for AOG-Link V0 via PGN.  

**User Interface:**  
- Full Avalonia-based replacement for WinForms including configuration dialogs and calibration wizards.  
- Real-time field display (≥30 FPS target) with settings persistence and accessibility compliance.  



## 6. Stakeholders & Governance

AgOpenNext is a volunteer-driven project built on shared ownership, transparency, and objective decision-making.  
Roles describe areas of responsibility, not authority — and continue to evolve as the project matures.

Contributor roles and current maintainers are listed in the [Meet the Team](./team/README.md) directory.

---

### Decision-Making

- **Technical:** Managed through the ADR process with open discussion on GitHub and Telegram.  
- **Scope:** Guided by this charter’s boundaries; major changes require documented rationale and community review.  
- **Code Acceptance:** Pull requests are reviewed by active contributors; consensus is based on evidence and testing, not popularity.  
- **Communication Channels:** Telegram Development (primary), GitHub (issues/PRs), [docs.agopengps.com](https://docs.agopengps.com), and Discourse for public updates.  
- **Meeting Cadence:** Async-first via GitHub and Telegram; ad-hoc calls (*Zoom, Discord, etc.*) or quarterly community check-ins as needed.  

---

### Governance Principles

- **Transparency:** All design and architectural decisions are documented through ADRs or SRS updates.  
- **Objectivity:** Decisions rely on evidence, testing, and documented rationale — not emotion or popularity.  
- **Accountability:** Each change references an ADR or issue discussion; consensus is formed through reasoned debate, not polls.  
- **Communication:** GitHub and Telegram serve as the primary collaboration channels; synchronous meetings are rare and optional.  

---

This structure keeps governance lightweight but rigorous — prioritizing clear documentation, traceable decisions, and engineering objectivity over hierarchy.

## 7. Key Deliverables

| ID | Deliverable | Description | Acceptance Criteria |
|----|--------------|-------------|----------------------|
| **D1** | Core Library | Cross-platform business logic (.NET) for GNSS, guidance, and field management. | Unit tests ≥80%; API docs complete. |
| **D2** | AgIO Service/Hardware Abstraction | Hardware interface layer for Windows/Linux handling serial, UDP, CAN, and sensors. | All v6 hardware operational; Linux service validated. |
| **D3** | Avalonia UI | Cross-platform desktop interface replacing WinForms. | Functional v6 parity; ≥30 FPS on reference hardware. |
| **D4** | Packaging Matrix | Windows installers (P0), Linux packages (P1). Android APK (P2), iOS Companion (P3) | Clean install and smoke tests pass. |
| **D5** | Test Suites | Automated unit, integration, and simulated field tests. | 100 % of critical v6 field scenarios pass. |
| **D6** | Documentation | Architecture, API, operator, and contributor docs. | Published to docs.agopengps.com; community reviewed. |
| **D7** | Migration Toolkit | Tools for v6 → Next data migration. | User settings, boundaries, and configs transfer successfully. |

---

## 8. Risks & Mitigations

| ID | Risk | Likelihood | Impact | Mitigation / Contingency |
|----|------|------------|--------|--------------------------|
| R1 | Linux/ARM64 graphics performance issues. | Medium | High | Benchmark early; software rendering fallback; delay ARM64 GA if needed. |
| R2 | GNSS/device behavior differs by OS. | Medium | High | Standardize on open formats; expand AgIO adapters; document quirks. |
| R3 | Volunteer time fluctuates. | High | Critical | Keep scope small; rotate ownership; acknowledge contributions. |
| R4 | Feature creep diverts focus. | High | High | Track extras as plugin or post-GA ideas; enforce ADR boundaries. |
| R5 | v6 → Next migration regressions. | Low | High | Build migration tools early; support reversible imports. |
| R6 | UI/UX changes frustrate operators. | Medium | High | Gather feedback; preserve familiar workflows; document differences. |
| R7 | CI/CD instability or cost. | Low | Medium | Use open runners; cache deps; minimize test matrix complexity. |
| R8 | Hardware variability complicates validation. | Medium | Medium | Encourage diverse testing; log hardware metadata; prioritize reproducibility. |

---

## 9. Migration & Transition

- Automated tools migrate v6 data (fields, vehicles, settings).  
- Real datasets validated pre-GA with rollback support.  
- Clear guides and community help for operators.  
- **No forced migration:** v6 remains supported.

---

## 10. Success Measures

- **Functional parity:** 100 % of critical v6 features working in real field use.  
- **Cross-platform reliability:** Windows (P0) and Linux (P1) stable; ARM64 verified post-GA.  
- **Field validation:** ≥20 operators across ≥3 continents.  
- **Build quality:** ≥95 % CI pass rate; <5 critical bugs at RC.  
- **Adoption:** Operators migrate from v6 voluntarily due to stability and usability gains.  
- **Governance maturity:** All key decisions traceable through ADRs or documented rationale.

---



## 11. Post-Foundation Outlook

Post-v1.0: plugin system, CAN bus integration, advanced guidance algorithms, cloud sync, and broader ecosystem support.  
All future features remain ADR-driven and community-reviewed — **foundation first** always.

---

## 12. Charter Governance & Revision

### Approval
This charter is a shared understanding — not a legal contract.
Approval requires community consensus with no major objections on GitHub or Telegram.  
Core contributors must agree to operate within the charter’s scope and principles.  
The Project Coordinator (Richard) declares the charter “accepted” based on community sentiment.  


### Governance & Values
Contributors are expected to uphold:
- **Foundation first:** Modernization before expansion.  
- **Transparency:** All decisions documented and reviewable.  
- **Objectivity:** Engineering choices grounded in data, not popularity.  
- **Quality:** Field-tested, operator-validated releases.  
- **Sustainability:** Designed for long-term maintainability.

### Revision Process
- **Minor updates** (clarifications, formatting): may be committed directly with a short changelog note.  
- **Major changes** (scope, governance, direction): proposed via GitHub Discussion or PR with a one-week comment period.  
- Version numbers increment with each accepted major change.  
- All previous versions remain archived for transparency and traceability.

---

Further execution details—timelines, QA, and resource planning—will be maintained in separate project documents.

## 13. Appendices

### A. Glossary
For definitions of technical terms (ADR, SRS, HAL, etc.), see the maintained [Glossary](./GLOSSARY.md) document in the repository.

### B. References
- **AgOpenGPS Repository:** [github.com/AgOpenGPS-Official/AgOpenGPS](https://github.com/AgOpenGPS-Official/AgOpenGPS)  
- **Documentation:** [docs.agopengps.com](https://docs.agopengps.com)  
- **Avalonia UI:** [avaloniaui.net](https://avaloniaui.net)  
- **.NET Documentation:** [learn.microsoft.com/dotnet](https://learn.microsoft.com/dotnet)  
- **Community Forum:** [discourse.agopengps.com](https://discourse.agopengps.com)


### C. Change Log
| Version | Date | Changes | Author | PR / Issue |
|---------|------|----------|--------|------------|
| 0.6.0 | 2025-11-08 | Back to Markdown for Github, even more compact at 246 lines, cut out redundant fat | Jon Fortney |  |
| 0.5.0 | 2025-11-06 | Compact Edition: Condensed from 673 to 370 lines (~45% reduction) for easier reading and sharing; preserved all essential sections and critical information; streamlined tables and explanations; removed redundancy | Markus |  |
| 0.4.0 | 2025-10-24 | Major rewrite for clarity and realism: simplified governance, reframed risks, modernized mission and vision to reflect community-led development. | Nexus Team (Fortney) |  |
| 0.3.2 | 2025-10-23 | Streamlined charter to emphasize mission, guardrails, goals, and scope; removed process-specific execution details. | Nexus Team (Codex) |  |
| 0.3.1 | 2025-10-22 | Consolidated charter with vision guardrails and baseline assumptions. | Nexus Team (Codex) |  |
| 0.3.0 | 2025-10-22 | Expanded goals, scope, and governance based on Next charter lessons learned. | Nexus Team (Fortney) |  |
| 0.2.0 | 2025-10-21 | Community review update incorporating steering feedback. | Next Team (Markus) |  |
| 0.1.0 | 2025-10-20 | Initial draft aligning with SRS foundations. | Nexus Team (Codex) |  |

### E. Ongoing Discussions

These topics remain under active discussion within the community and may inform future charter updates or ADRs.  
They represent naming, platform, and structural decisions that are not yet finalized but influence long-term direction.

| Topic | Summary | Current Status |
|-------|----------|----------------|
| **Project Codename** | Whether to retain **AgOpenNext** or adopt an alternate such as *AgOpenGPS Next*, *AgNext*, or *AgOpenGPS Nexus*. Final name will serve as the bridge between the v6 lineage and future v7 release. | AgOpenNext favored; open for feedback. |
| **First GA Release Name** | Determining what to call the first general-availability release: continue using the codename (*AgOpenNext v1.0*) or formally resume the legacy naming as **AgOpenGPS v7.0** to maintain continuity with previous versions. | Community leaning toward **AgOpenGPS v7.0** to signal a direct, modern continuation of the AgOpenGPS line. |
| **Domain Terminology** | What to call individual core domains—built-in and community. “Modules” currently refers to hardware PCBs; “plugins” suits community extensions; “blocks” is also used informally. Architectural boundaries are defined, but naming remains undecided. | Decision pending; may standardize through early ADRs. |
| **Runtime Version Policy** | Defining the target policy for **.NET** and **Avalonia** versions (latest stable vs LTS). Current practice is “latest stable combination verified by CI.” | Ongoing; documented in §5.1. |
| **Headless / Remote UI Strategy** | How to handle headless operation and remote UIs. Android is popular as a first-class runtime; Android/iOS companions may leverage the existing gRPC bridge for lightweight remote control. | Architectural support in place; implementation priority TBD. |

*These items are tracked for transparency and may be formalized in future charter revisions or ADRs as consensus emerges.*


*End of document.*
