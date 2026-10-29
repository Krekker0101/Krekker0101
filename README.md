<!-- GitHub-native Mermaid diagrams, collapsible details, and a locally stored animated banner. -->
<p align="center"><img src="assets/profile-banner.gif" alt="Animated dark banner: Build with intent" width="100%" /></p>
<h1 align="center">Abdullo Ashurov</h1>
<p align="center"><strong>Software Engineer · Systems Architecture · Product Engineering</strong><br/>Building independent products through thoughtful engineering.</p>
<p align="center"><code>PRODUCTS</code> · <code>SYSTEMS</code> · <code>AUTOMATION</code></p>
<p align="center"><a href="#architecture-at-a-glance">Architecture</a> · <a href="#selected-work">Selected work</a> · <a href="ARCHITECTURE.md">Deep-dive diagrams</a></p>

---

## Architecture at a glance

This map groups my public repositories by problem space. It does **not** imply that these projects are one connected platform.

```mermaid
flowchart TB
    ME["Abdullo Ashurov<br/>Independent product engineering"]
    ME --> LOCAL["Offline-first desktop software"]
    ME --> AUTO["Automation & integrations"]
    ME --> VISION["Computer vision & traffic systems"]
    ME --> WEB["Web & communication products"]
    ME --> MOBILE["Mobile & camera tools"]
    LOCAL --> M["MaktabOS<br/>Python · PySide6 · SQLite"]
    LOCAL --> N["Noz-Bogh POS<br/>Python · Qt · SQLite"]
    AUTO --> P["PULSE<br/>Telegram · Python · PostgreSQL"]
    AUTO --> C["ChatPilot<br/>Telegram · FastAPI · optional Redis"]
    VISION --> R["RohAI<br/>Vision · tracking · dashboard"]
    WEB --> L["LinkUp<br/>Go backend · web frontend"]
    WEB --> G["GAPAK<br/>Go · React starter"]
    WEB --> B["Bunker<br/>C++ game core · Telegram transport"]
    MOBILE --> S["Scetch<br/>Flutter · local-first camera tracing"]
    classDef root fill:#111418,stroke:#86DDB2,color:#F5F7F6,stroke-width:2px;
    classDef product fill:#171B1F,stroke:#59645F,color:#F0F3F1;
    class ME root;
    class M,N,P,C,R,L,G,B,S product;
```

<details>
<summary><strong>How to read this map</strong></summary>

- **Offline-first desktop:** local workflows and data storage are central to MaktabOS and Noz-Bogh POS.
- **Automation:** PULSE focuses on content discovery and publishing workflows; ChatPilot focuses on Telegram Business auto-replies and administration.
- **Vision systems:** RohAI separates dashboard, analysis/simulation, and guarded hardware-facing workflows.
- **Communication and web:** LinkUp, GAPAK, and Bunker explore different application and service boundaries.
- **Mobile tools:** Scetch focuses on camera-assisted tracing with local project storage.

Arrows group projects by purpose; they do not imply repository dependencies.

</details>

---

## Selected work

| Project | Focus | Technologies |
|---|---|---|
| [**MaktabOS**](https://github.com/Krekker0101/MaktabOS) | Offline school register, student records, Excel/Word import and export | Python · PySide6 · SQLite |
| [**Noz-Bogh POS**](https://github.com/Krekker0101/Noz-Bogh) | Desktop restaurant POS, kitchen workflow, payments, backups and reporting | Python · PySide6 · SQLite |
| [**PULSE**](https://github.com/Krekker0101/PULSE) | Telegram-managed YouTube discovery, engagement analysis, filtering and publishing workflows | Python · Telegram · PostgreSQL |
| [**ChatPilot**](https://github.com/Krekker0101/ChatPilot) | Telegram Business auto-reply assistant, admin tools and optional state/scheduling integrations | Python · FastAPI · aiogram |
| [**RohAI**](https://github.com/Krekker0101/RohAI) | Smart-traffic exploration with video analysis, tracking, simulation and dashboard | Python · computer vision · TypeScript |
| [**LinkUp**](https://github.com/Krekker0101/LinkUp) · [Frontend](https://github.com/Krekker0101/LinkUp-frontend) | Communication platform exploring real-time messaging and separated backend/frontend | Go · TypeScript |
| [**Bunker**](https://github.com/Krekker0101/Bunker) | Telegram social game with C++ game engine and separated persistence/transport | C++ · SQLite · Telegram |
| [**GAPAK**](https://github.com/Krekker0101/GAPAK) | Go + React web application starter focused on auth and application structure | Go · React · PostgreSQL |
| [**Scetch**](https://github.com/Krekker0101/Kashak) | Camera tracing and drawing app with adjustable overlays and local projects | Flutter · Dart · SQLite |

[**Explore all public repositories →**](https://github.com/Krekker0101?tab=repositories) · [**Open the architecture atlas →**](ARCHITECTURE.md)

## Engineering principles

- **Clarity over accidental complexity.**
- **Products over empty promises.**
- **Architecture that can evolve.**
- **Local-first when it improves control and resilience.**
- **Real implementation, documented limitations, and incremental refinement.**

<p align="center"><strong>BUILD WITH INTENT.</strong><br/><sub>Less noise. Better systems. Meaningful products.</sub></p>

