# AgOpenNext Glossary

## Acronyms
| Acronym | Name | Definition |
| --- | --- | --- |
| **ADR** | Architecture Decision Record | A document that captures a single, significant architectural design choice. |
| **Avalonia** | Avalonia UI Framework | Cross-platform .NET-based user interface framework used for AgOpenNext. |
| **Core** | Core Logic Layer | The main business logic layer handling guidance, field management, and system orchestration. |
| **GA** | General Availability | Public, stable software release ready for production use. |
| **GNSS** | Global Navigation Satellite System | Satellite navigation systems including GPS, GLONASS, Galileo, and BeiDou. |
| **HAL** | Hardware Abstraction Layer | Interface between the business logic (Core) and physical hardware; process architecture TBD. |
| **Next** | Project Codename | Internal codename for the AgOpenGPS rewrite project (AgOpenNext). |
| **RFC** | Request for Comments | A structured proposal document used to discuss and review major changes, features, or governance updates before formal adoption. |
| **RTK** | Real-Time Kinematic | High-precision GNSS correction technique for centimeter-level accuracy. |
| **SRS** | Software Requirements Specification | Comprehensive document outlining the functional and non-functional requirements of a software system. |

---

## Platform-wide Terms
| Term | Definition |
| --- | --- |
| **Pose** | A timestamped position/orientation sample for a physical or virtual node (tractor, implement, toolbar, sensor) within the canonical coordinate reference system. |
| **PoseStream** | The ordered, canonical time series of poses and associated state deltas that all AgOpenNext services, plugins, and replays consume. |
| **Equipment** | A configured machine profile representing a tractor, combine, sprayer, or other power unit that may host one or more implements. |
| **Implement** | A functional attachment (planter, toolbar, sprayer) mounted to equipment and containing toolbars, sections, and sensors. |
| **Toolbar** | A physical or logical boom/bar spanning multiple sections with shared lookahead, overlap, and control metadata. |
| **SectionRow** | Marker defining a crop row if multiple exist within a section; used when controlling multiple rows per section but tracking rows individually. |
| **SectionNode** | The smallest controllable output element (row unit, nozzle, valve) with an addressable on/auto/off state. |
| **SectionGroup** | A named grouping of SectionNodes (or nested groups) that can receive aggregate commands, overlaps, or rates. |
| **Master Group** | The highest-priority SectionGroup controlling a toolbar or implement; manual overrides or safety interlocks apply here first. |
| **Layer** | A time- or session-bounded spatial dataset (coverage, rate, yield, diagnostics) registered with units, precision, and visualization metadata. |
| **Prescription** | A target layer prescribing rates or setpoints to controllers (e.g., variable-rate fertilizer or seeding) and feeding automation decisions. |
| **Event** | A discrete control or telemetry record representing an observed action (e.g., section on/off, obstruction detected). |
| **Opportunity** | The expected number of controllable actions in an interval (e.g., rows that should fire) used to evaluate misses or doubles. |
| **Tile** | A chunk of gridded spatial data persisted in the TileStore with shared codec/precision metadata. |
| **Cell** | The individual sample within a tile storing a value, weight, min/max, and quality metadata. |
| **Vector Log** | The append-only PoseStream/SectionState record used for deterministic replay and audit trails. |
| **Fusion** | The process of combining multiple PoseStreams or layers (sessions, implements, seasons) into a unified dataset with provenance. |
| **Provenance** | Recorded lineage describing how data was produced, transformed, and validated across plugins, sessions, and exports. |
| **Registry Hash** | A stable hash computed over layer definitions and schemas to detect mismatches between plugins, firmware, and stored data. |
| **AgIO** | Companion I/O service providing network, CAN, and serial connectivity for AgOpenGPS. |
| **Headless** | Running without a directly attached display, controlled remotely or via automation. |
| **Kiosk Mode** | Locked-down runtime experience intended for field operators with minimal UI. |
| **Multi-Monitor** | Use of two or more displays to show different dashboards or controls simultaneously. |
| **Remote UI** | User interface accessed via another device (tablet, browser, or thin client). |

---

## Guidance Orchestrator Terms
| Term | Definition |
| --- | --- |

> Have another term to add? Update this master glossary and cross-link any domain-specific guides back here.
