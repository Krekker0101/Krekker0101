# Project Architecture Atlas

A GitHub-native architecture guide for selected public repositories by [Krekker0101](https://github.com/Krekker0101). Mermaid diagrams render directly in GitHub. These maps describe visible source boundaries and documented workflows; they do not claim all repositories form one platform or that every feature is production-deployed.

## 1. PULSE — social-content automation

[Repository](https://github.com/Krekker0101/PULSE)

```mermaid
flowchart LR
    TG["Telegram UI / bot"] --> APP["Python application"]
    API["HTTP API"] --> APP
    APP --> DOMAIN["Domain rules<br/>filters · popularity · schedule · lifecycle"]
    APP --> SERVICES["Services<br/>catalog · monitoring · publishing · media"]
    SERVICES --> SRC["Source integrations<br/>YouTube · connected sources"]
    SERVICES --> PUB["Publishing integrations<br/>destinations · OAuth · platform APIs"]
    DOMAIN --> DB["PostgreSQL"]
    SERVICES --> DB
    APP --> SEC["Security / configuration"]
```

Domain rules, services, source integrations, publishing integrations, and persistence are separate concerns. Media discovery, retention, permissions, and publishing are not the same workflow.

<details><summary><strong>Source map</strong></summary>

- `backend/app/domain/` — filtering, popularity, scheduling, lifecycle, destinations.
- `backend/app/services/` — catalog, source monitoring, publishing, media, worker workflows.
- `backend/app/integrations/` — YouTube, Telegram, social platforms and publishing.
- `backend/app/api.py`, `backend/app/bot.py` — application entry surfaces.
- `backend/app/models.py`, `backend/app/db.py` — persistence models and database access.

</details>

## 2. MaktabOS — local school register

[Repository](https://github.com/Krekker0101/MaktabOS)

```mermaid
flowchart TD
    USER["School staff"] --> UI["PySide6 desktop UI"]
    UI --> APP["Application layer"]
    APP --> VALID["Validation / domain rules"]
    APP --> XLS["Excel import / export"]
    APP --> DOC["Word import / export"]
    APP --> STORE["SQLite storage"]
    APP --> BACKUP["Backup / recovery"]
    STORE --> LOCAL["Local data files"]
    BACKUP --> LOCAL
```

Designed to work locally without a permanent internet connection. Import/export, validation, persistence, and recovery have distinct modules.

<details><summary><strong>Source map</strong></summary>

- `schoolregister/app.py` — desktop application.
- `schoolregister/storage.py` — local persistence.
- `schoolregister/validation.py` — data validation.
- `schoolregister/excel.py`, `schoolregister/word.py` — document workflows.
- `schoolregister/backup.py`, `schoolregister/recovery.py` — backup and recovery.

</details>

## 3. Noz-Bogh POS — restaurant operations

[Repository](https://github.com/Krekker0101/Noz-Bogh)

```mermaid
flowchart LR
    STAFF["Restaurant staff"] --> UI["PySide6 desktop UI"]
    UI --> PAGES["Operational pages"]
    PAGES --> SERVICE["Application services"]
    SERVICE --> DB["SQLite database"]
    SERVICE --> REPORTS["Reports / exports"]
    SERVICE --> BACKUP["Backup workflow"]
    SERVICE --> NET["Optional local network features"]
```

A native desktop POS with local database storage. The source separates database access, service operations, UI pages, localization, and styling.

<details><summary><strong>Source map</strong></summary>

- `app/main_window.py`, `app/pages.py` — window and pages.
- `app/services.py` — application operations.
- `app/database.py` — database access.
- `app/network.py` — network-related functionality.
- `app/i18n.py` — localization.

</details>

## 4. RohAI — smart traffic and computer vision

[Repository](https://github.com/Krekker0101/RohAI)

```mermaid
flowchart TB
    VIDEO["Video / camera / demo source"] --> ROUTER["Mode routing"]
    ROUTER --> DEMO["Demo runtime / simulation"]
    ROUTER --> VISION["Vision & tracking pipeline"]
    VISION --> ANALYSIS["Video analysis / observations"]
    DEMO --> ENGINE["Traffic and safety logic"]
    ANALYSIS --> ENGINE
    ENGINE --> API["Backend API / operations"]
    API --> DASH["Web dashboard"]
    ENGINE --> GATE["Hardware protocol / safety boundary"]
    GATE --> DEVICE["Device adapter or emulator"]
    NOTE["Real hardware activation is a separate gated stage"] -.-> GATE
```

Demo/simulation, video analysis, and hardware-facing paths are distinct. Repository documentation treats physical road activation as a separate gate; this diagram does not imply live traffic control is deployed.

<details><summary><strong>Source map</strong></summary>

- `apps/backend/src/smart_traffic_backend/` — runtime, mode routing, AI, video analysis, safety and hardware boundaries.
- `apps/dashboard/src/` — frontend views, data access and feature panels.
- `apps/dashboard/src/data/` — API/backend adapters and telemetry source handling.
- `docs/` — pilot, validation, and operation documentation.

</details>

## 5. LinkUp — communication platform

[Backend](https://github.com/Krekker0101/LinkUp) · [Frontend](https://github.com/Krekker0101/LinkUp-frontend)

```mermaid
flowchart LR
    CLIENT["Web client"] <--> HTTP["HTTP API"]
    CLIENT <--> WS["WebSocket"]
    HTTP --> HANDLERS["Go handlers"]
    WS --> HANDLERS
    HANDLERS --> AUTH["Authentication / authorization"]
    HANDLERS --> MODELS["Application models"]
    MODELS --> STORAGE["Database / storage"]
    HANDLERS --> UPLOAD["File upload"]
```

The backend separates app setup, handlers, auth, models, storage, and utilities. The frontend is maintained in a separate repository.

## 6. Bunker — game engine and Telegram transport

[Repository](https://github.com/Krekker0101/Bunker)

```mermaid
flowchart TD
    TG["Telegram updates / webhook"] --> APP["Bot application"]
    APP --> ENGINE["C++ game engine"]
    ENGINE --> MODEL["Game model / deck / rules"]
    ENGINE --> REPO["Repository interface"]
    REPO --> STATE["State codec / persistence"]
    APP --> CLIENT["Telegram client / transport"]
    STATE --> DB["SQLite or configured database"]
    API["Webhook / serverless adapter"] --> APP
```

Game rules/state are separated from Telegram transport and persistence. Native C++ components are paired with webhook/serverless adapters and tests.

## 7. ChatPilot — Telegram Business auto-replies

[Repository](https://github.com/Krekker0101/ChatPilot)

```mermaid
flowchart LR
    TG["Telegram Business updates"] --> WH["Webhook / FastAPI"]
    WH --> BOT["aiogram dispatcher"]
    BOT --> RULES["Auto-reply rules / templates"]
    BOT --> ADMIN["Admin and runtime settings"]
    RULES --> STORE["Persistence service"]
    ADMIN --> STORE
    STORE --> REDIS["Optional Redis"]
    BOT --> FOLLOW["Follow-up scheduling"]
    FOLLOW --> QSTASH["Optional QStash"]
```

Webhook entry points, bot handlers, application services, security, settings, and scheduling are separate concerns. Redis and QStash are optional integrations; guarantees depend on configuration.

## 8. Scetch — local camera tracing

[Repository](https://github.com/Krekker0101/Kashak)

```mermaid
flowchart TD
    USER["User"] --> UI["Flutter app"]
    UI --> CAMERA["Camera session / preview"]
    UI --> IMPORT["Reference image import"]
    IMPORT --> PROCESS["Image processing"]
    PROCESS --> OVERLAY["Adjustable tracing overlay"]
    CAMERA --> OVERLAY
    UI --> PROJECT["Local drawing project"]
    PROJECT --> DB["Local persistence"]
```

The source tree separates app bootstrap/routing, camera handling, image processing, and local project persistence. Project documentation notes that production readiness and all validation steps should not be assumed complete.

---

## Keep diagrams accurate

When a project changes, update its diagram alongside its architecture docs. Prefer clear boundaries and data flow over decoration. All diagrams are Mermaid rendered by GitHub; no external diagram service, JavaScript, or analytics embed is required.

