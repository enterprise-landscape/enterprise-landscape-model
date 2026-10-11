# Enterprise Landscape Model (ELM) — Spezifikation

**Klassifikation:** Enterprise Architecture Framework (nach ISO/IEC/IEEE 42010)  
**Kern-Artefakt:** Kanonisches Referenzmodell  
**Version:** 0.8  
**Status:** Public Preview  
**Autor:** Julia Senner (Enterprise & Solution Architecture)  
**Relevante Materialien:** [enterprise-landscape-model.pptx](assets/enterprise-landscape-model.pptx) (Vektor-Vorlage) / [enterprise-landscape-model.png](assets/enterprise-landscape-model.png) (Diagramm)  

---

## 1. Zweck, Geltungsbereich und Abgrenzung

### 1.1 Zweck und Gliederung nach ISO/IEC/IEEE 42010

Das **Enterprise Landscape Model (ELM)** bildet ein hersteller- und branchenneutrales, formales Referenzmodell, um nachhaltige, zukunftsfähige, evolvierbare und langfristig wartbare Unternehmens- und Systemlandschaften zu gestalten. Es überwindet Silos zwischen Fachbereich, Software-Engineering und Plattformbetrieb, ohne in die bürokratische Trägheit klassischer Großframeworks zu verfallen.

Gemäß dem Standard ISO/IEC/IEEE 42010 gliedert sich das ELM in drei komplementäre Ebenen:

1. **ELM Lean Metamodel (Formale Ontologie):** Definiert die minimalistische Menge an Entitätstypen, typisierten Beziehungen und Integritätsaxiomen, um Architekturbeschreibungen maschinenlesbar, auditierbar und in EAM-Werkzeugen abbildbar zu machen (Kapitel 2).
2. **ELM Canonical Reference Model (Kanonisches Referenzmodell):** Definiert die verbindliche Soll-Topologie aus fünf Schichten, Entkopplungsgateways und Guiding Principles als wiederverwendbares Strukturmuster für moderne Unternehmenslandschaften (dieses Dokument, Kapitel 3 bis 6).
3. **ELM Ökosystem (Modulare Modellerweiterungen):** Vertikale Schichten-Vertiefungen (`segments/`) als Zoom-ins und transversale thematische Projektionen (`overlays/`) als Zoom-outs über alle Schichten.

Das Referenzmodell erfüllt drei Kernfunktionen:
1. **Normativ:** Es definiert die verbindlichen Schichten, funktionalen Bausteine, Entkopplungsgateways und Interaktionsregeln für eine tragfähige Zielarchitektur.
2. **Diagnostisch:** Es liefert das neutrale Prüfraster für Architektur-Reviews, um strukturelle Brüche, fehlende Entkopplung, unklare Datenverantwortung und Inkonsistenzen zwischen Fachlichkeit, Software-Systemen und Plattformfundament objektiv aufzudecken.
3. **Kommunikativ:** Es schafft eine gemeinsame visuelle und begriffliche Orientierung über Rollen- und Disziplingrenzen hinweg (Executive Management, Fachbereiche, Solution Architecture, Software Engineering und Plattformteams).

### 1.2 Geltungsbereich

Das Modell adressiert die ganzheitliche Unternehmenslandschaft als soziotechnisches Gesamtsystem:

- **Abgedeckter Gestaltungsraum:** Der Gestaltungsraum umfasst das soziotechnische Gesamtsystem des Unternehmens: von der strategischen und normativen Unternehmenssteuerung über die fachliche Wertschöpfung, Geschäftsfähigkeiten und Geschäftsprozesse, die softwaretechnische Anwendungs- und Systemlandschaft sowie die unternehmensweite Informations- und Datenarchitektur bis hin zum technologischen Betriebs- und Plattformfundament.
- **Hebelwirkung in komplexen Organisationen:** Seine primäre Steuerungs- und Diagnosewirkung entfaltet das Modell in gewachsenen, verteilten Organisationen mit hoher Fach- und Transaktionskomplexität, heterogenen Systembeständen und regulatorischen Anforderungen.
- **Hersteller- und Technologieunabhängigkeit:** Alle Konzepte, Bausteine und Interaktionsmuster sind technologieneutral formuliert und gelten unabhängig von spezifischen Cloud-Providern, Standardsoftware-Produkten oder Programmiersprachen.

### 1.3 Bewusste Abgrenzungen

Zur Wahrung methodischer Klarheit und zur Vermeidung unnötiger Bürokratie grenzt sich das Modell explizit ab:

- **Keine schwerfällige Prozessbürokratie:** Das Modell verzichtet bewusst auf die formale Vollständigkeit schwerfälliger Großframeworks (wie des vollständigen TOGAF-ADM-Zyklus). Es folgt dem Prinzip von Lean Architecture und fokussiert auf unmittelbare Handlungs- und Entscheidungsfähigkeit vor administrativer Selbstverwaltung.
- **Keine isolierte IT-Bebauungsplanung:** Das Modell ist weder eine reine Software-Inventur noch ein Server- und Datenbankkatalog. Applikationen und Daten werden zwingend an Geschäftsfähigkeiten, Wertströme und Domänenverantwortung rückgebunden.
- **Kein Ersatz für Detail- und Software-Design:** Das Modell beschreibt die Makro-Architektur der Gesamtlandschaft. Es ersetzt weder das feingranulare Softwaredesign einzelner Services (z. B. Klassendiagramme, Framework-Auswahl, Tabellenschemata auf Spaltenebene) noch tiefes Netzwerk- und Betriebssystem-Engineering.

### 1.4 Klassifizierung der Kriterien

Jede Aussage, jedes Kriterium und jede Beziehungsregel im Modell weist ihre Verbindlichkeit transparent aus:

| Kennzeichen | Bedeutung | Konsequenz für die Bewertung |
|---|---|---|
| **[E]** | Etablierte Praxis. In Standards (TOGAF, DDD, BIZBOK, ISO/IEC/IEEE 42010), Fachliteratur oder Regulatorik (DORA, DSGVO) belegt. | Verbindlich; darf in der Zielarchitektur nicht unterschritten werden. |
| **[A]** | Abgeleitet. Aus empirischen Befunden, wiederkehrenden Fehlermustern und Beratungspraxis realer Transformationsprojekte gewonnen. | Pragmatisch begründet; im Kontext spezifischer Rahmenbedingungen anpassbar. |
| **[H]** | Hypothese. Plausible, schlüssige Arbeitsthese, die noch nicht empirisch breit abgesichert ist. | Diskursiv; darf niemals die alleinige Basis für verbindliche Architekturentscheidungen bilden. |

*Hinweis zur Modellreife:* Das kanonische Referenzmodell spezifiziert ausschließlich etablierte Praxis `[E]` und empirisch abgeleitete Architekturmuster `[A]`. Die Kategorie Hypothese `[H]` ist experimentellen Entwürfen in Segment-Vertiefungen (`segments/`) und explorativen Overlays (`overlays/`) vorbehalten und tritt im kanonischen Kernmodell nicht auf.

### 1.5 Modulare Erweiterbarkeit: Segmente und Overlays

Das Enterprise Landscape Reference Model folgt dem architektonischen Zoom-in / Zoom-out Prinzip und lässt sich über zwei standardisierte Erweiterungsmechanismen präzise skalieren:

1. **Segment-Architekturen (`segments/` — Zoom-in):** Vertikale Tiefenschnitte in einzelne Schichten oder Domänen (z. B. der detaillierte Capability-Zuschnitt im Business Layer).
2. **Thematische Overlays (`overlays/` — Zoom-out & Querschnitt):** Transversale Projektionen spezifischer Fragestellungen über alle Schichten des Modells (z. B. [AI-Readiness](../overlays/ai-readiness/ai-readiness-overlay.md), Cloud-Native, Resilienz).

---

## 2. Das ELM Lean Metamodel

Das Metamodell definiert die formale, sprach- und werkzeugneutrale Ontologie des ELM. Es stellt sicher, dass Architekturbeschreibungen präzise strukturiert, werkzeugneutral in Enterprise-Architecture-Management-Systemen abbildbar und automatisiert auditierbar sind.

Das Metamodell besteht aus drei Komponenten:
1. **Kanonische Meta-Entitäten (Knotentypen):** Die formalen Bausteinklassen der Unternehmenslandschaft.
2. **Typisierte Meta-Relationen (Kanten):** Die orthogonalen Basis-Beziehungsarten zwischen Entitäten.
3. **Architektonische Axiome (Integritätsregeln):** Unverhandelbare Invarianten für das Zusammenspiel der Bausteine.

### 2.1 Kanonische Meta-Entitäten (Knotentypen)

| ELM Metaklasse | Ontologische Kategorie | Semantische Definition & Rolle |
|---|---|---|
| **`GovernanceDirective`** | Steuerung | Verbindliche Richtlinie, Technologiestack-Vorgabe, Compliance-Regel oder RACI-Rolle |
| **`ValueStream`** | Business | Sequenz von wertschöpfenden Schritten zur Erbringung eines Kundennutzens (End-to-End) |
| **`BusinessCapability`** | Business | Stabile, technologie- und organisationsneutrale Geschäftsfähigkeit („Was tut das Unternehmen?“) |
| **`BusinessProcess`** | Business | Fachlicher Ablauf mit definierter Ausführungslogik, Vorbedingungen und Prozesszielen |
| **`Domain`** | Kontext | Soziotechnische Einheit (Bounded Context) mit einheitlicher Ubiquitous Language und Domain Ownership |
| **`ExperienceGateway`** | Interaktion | Grenzschranke für Nutzer- und Agenteninteraktion: Entkoppelt Mensch/Agent von Systemdetails; sichert Kanalneutralität |
| **`IntegrationGateway`** | Interaktion | Grenzschranke für System- und Partnerinteraktion: API-Management, Event-Broker, Authentifizierung, Rate Limiting |
| **`Workflow`** | Systeme | Zustandstragende technische Prozessausführung, Saga-Orchestrierung und Batch-/Stream-Pipelines |
| **`Application`** | Systeme | Ausführbare Software-Einheit: modularer Fachservice, Standardsoftware (COTS), SaaS oder gekapselter Kernmonolith |
| **`SemanticEntity`** | Daten | Kanonisches Geschäftsobjekt, Fachbegriff, Ontologie-Knoten der Ubiquitous Language |
| **`DataContract`** | Daten | Maschinenlesbare Schema- und Qualitätsspezifikation (SLAs/SLOs) zwischen Datenanbietern und -konsumenten |
| **`DataProduct`** | Daten | Autonomer, versionierter und qualitätsgesicherter Datenbestand mit dezentralem Ownership |
| **`PlatformCapability`** | Technologie | Standardisierte Basisfähigkeit für Compute, Storage, IAM, CI/CD und Observability |

### 2.2 Typisierte Meta-Relationen (Kanten-Grammatik)

| Metamodell-Relation | Semantische Definition | Architektonischer Geltungsbereich |
|---|---|---|
| **`owns`** | Strukturelle Klammer und soziotechnische Verantwortung (Domain Ownership). | Soziotechnische Eigentümergrenzen auf alle Elemente innerhalb desselben Kontextes |
| **`governs`** | Normative Steuerung, Richtlinie, architektonische Restriktion oder Vorgabe. | Richtliniengebende und regulierende Instanzen auf operative und infrastrukturelle Elemente |
| **`realizes`** | Strukturelle Erfüllung und Operationalisierung einer abstrakteren fachlichen Entität. | Ausführende und operationalisierende Elemente auf fachliche und konzeptionelle Elemente |
| **`enables`** | Bereitstellung funktionaler, informationeller oder infrastruktureller Grundlagen (Serving). | Bereitstellende Fundamente und Datenbestände auf abhängige oder wertschöpfende Elemente |
| **`utilizes`** | Operative Nutzung, Konsum von Schnittstellen, Datenbeständen oder Ressourcen. | Operative Konsumenten auf horizontal oder vertikal bereitgestellte Services, Produkte oder Plattformdienste |

### 2.3 Architektonische Axiome (Metamodell-Invarianten)

| Axiom | Kernprinzip | Normative Regel | Adressiertes Anti-Pattern |
|---|---|---|---|
| **Axiom 1: Schichtenkapselung** | No Layer Skipping | Fachlichkeit (`BusinessCapability`, `BusinessProcess`) greift niemals direkt auf Basisinfrastruktur (`PlatformCapability`) zu; Vermittlung erfolgt zwingend über Software (`Application`). | Schatten-Infrastruktur, Bypass-Architektur |
| **Axiom 2: Semantische Koppelung** | No Shared Database | Domänenübergreifende Interaktion zwischen Software-Systemen erfolgt niemals über gemeinsame Datenbankspeicher, sondern über `DataProduct` oder `DataContract`. | Shared-Database-Monolith, Data Leaks |
| **Axiom 3: Gateway-Schranke** | No Unguarded Ingress/Egress | Externe Interaktionen (Mensch, Agent oder Partnersystem) erreichen interne Systeme und Daten ausnahmslos über vorgeschaltete `ExperienceGateway` bzw. `IntegrationGateway`. | Ungeschützte API-Fluten, Point-to-Point-Spaghetti |
| **Axiom 4: Vertragsdisziplin** | No Contract, No Call | Schnittstellen und Datenprodukte dürfen erst domänenübergreifend konsumiert werden, wenn ein maschinenlesbarer `DataContract` mit Schemata und SLAs publiziert ist. | Blind Calls, unkontrollierte Schema-Drifts |

---

## 3. Architekturübersicht und Topologie

![Enterprise Landscape Reference Model](assets/enterprise-landscape-model.png)

Das Referenzmodell gliedert die Unternehmenslandschaft in **fünf strukturelle Schichten (Tiers)**, **zwei Gateway-Schnittstellen** und übergreifende **Leitprinzipien (Guiding Principles)**:

- **Horizontale Rahmung:**
  - **Tier 1: Governance:** Strategischer, normativer und regulatorischer Steuerungsrahmen.
  - **Tier 5: Foundation:** Technologisches Betriebs- und Plattformfundament.
- **Operativer Kern (Der funktionale Dreiklang):**
  - **Tier 2: Business Layer:** Fachliche Wertschöpfung, Geschäftsfähigkeiten und Geschäftsprozesse.
  - **Tier 3: System Layer:** Technische Ablaufsteuerung und operative Software-Systeme.
  - **Tier 4: Data Layer:** Semantisches und informationelles Fundament (Semantik, Datenverträge, Datenprodukte).
  - **Die Domäne (Bounded Context):** Die verbindende soziotechnische Schnittmenge im Zentrum des operativen Dreiklangs, die Fachlichkeit (Tier 2), Software-Services (Tier 3) und Datenhoheit (Tier 4) unter einem einheitlichen Domain Ownership klammert.
- **Gateway-Schnittstellen (Außengrenzen des operativen Kerns):**
  - **Experience** (an Tier 2/3): Entkopplung der Nutzerschnittstellen (Mensch-zu-System).
  - **Integration** (an Tier 3): Entkopplung der Systemverbindungen (System-zu-System).
- **Steuerungsrahmen:**
  - **Guiding Principles:** Übergreifende architektonische Entscheidungsleitplanken für Organisation, Applikationen/Daten und Plattform/Sicherheit.

### 3.1 Topologie und Raumaufteilung der Referenzarchitektur

Die visuelle Komposition des ELM folgt einer strikten funktionalen Raumaufteilung:

1. **Horizontale Rahmung:**  
   - **Tier 1 (Governance)** bildet das strategische Dach.  
   - **Tier 5 (Foundation)** stellt das gemeinsame technologische Betriebs- und Plattformfundament bereit.
2. **Die funktionale Dreiteilung des operativen Raums:**  
   Der Raum zwischen Governance und Foundation teilt sich in drei gleichwertige funktionale Sektoren:
   - **Obere Zone (Tier 2 Business Layer):** Fachliche Wertschöpfung, Wertströme, Capabilities und Geschäftsprozesse.
   - **Untere Zone (Tier 3 System Layer):** Operative Software-Systeme, Services und technische Ablaufsteuerung.
   - **Rechte Zone (Tier 4 Data Layer):** Semantik, maschinenlesbare Schemata, Data Contracts und Datenprodukte (beschriftet über das vertikale Tab-Label rechts).
3. **Der Konvergenzpunkt im Zentrum (Die Domäne):**  
   Dort, wo die Trennlinien der drei Sektoren im Zentrum zusammenlaufen, sitzt das architektonische Alignment: Hier manifestiert sich die **Domäne (der Bounded Context)** als soziotechnische Schnittmenge, die Fachlichkeit, Software und Datenhoheit für ein Thema vereint.
4. **Flankierende Leitplanken:**  
   Die rechte Außensäule fasst die **Guiding Principles** zusammen, die als normative Heuristiken quer über alle Schichten und Zonen wirken.

---

## 4. Schichten und Bausteine (Strukturmodell)

Jedes Tier umfasst klar definierte, funktionale Architekturbausteine:

### Tier 1: Governance
Definiert den strategischen und normativen Handlungsrahmen:
- **Strategy & Roadmap [E]:** Strategische Zielbilder, Transformationspfade und Investitionspriorisierung.
- **Roles & Responsibilities [E]:** Aufbauorganisation, Ownership-Modelle (z. B. Domain Owner, Product Owner) und RACI-Zuordnungen.
- **Standards & Guidelines [E]:** Verbindliche Technologie-Stacks, Architekturmuster und Entwicklungsrichtlinien.
- **Compliance & Regulatorik [E]:** Gesetzliche, aufsichtsrechtliche und branchenspezifische Vorgaben (z. B. DORA, EU AI Act, DSGVO, ISO 27001).

---

### Tier 2: Business Layer (Operative Wertschöpfung)
Bildet die fachliche Wertschöpfung der Organisation ab:
- **Value Stream [E]:** End-to-End-Wertströme zur Erbringung von Kundennutzen.
- **Business Capabilities [E]:** Stabile, technologieunabhängige Fähigkeiten der Organisation (Differenzierung nach Core, Supporting, Generic).
- **Prozesse [E]:** Fachliche Abläufe mit definierter logischer und zeitlicher Reihenfolge.
- **Kanäle & Touchpoints (Experience) [E]:** Fachliche Zugangskanäle und Interaktionspunkte für Kunden, Mitarbeiter und Partner (Omni-Channel-Architektur, Customer Journey Touchpoints).

---

### Tier 3: System Layer (Operative Ausführung)
Bildet die technische Software- und Ausführungslandschaft ab:
- **Workflows & Orchestrierung [A]:** Technische Ablaufsteuerung, Saga-Orchestrierung sowie synchrone APIs, asynchrone Queues und ereignisgesteuerte Streaming-Pipelines.
- **Services & Applications [E]:** Ausführbare Software-Einheiten: modulare Fachservices (Microservices), integrierte Standardsoftware (COTS/SaaS) und gekapselte Kernsystem-Monolithen.
- **Integration (Gateway-Baustein) [E]:** Technische Integrationsschicht (API Gateways, Event Broker, Enterprise Messaging) zur Entkopplung system- und domänenübergreifender Kommunikation.

---

### Tier 4: Data Layer (Information & Semantik)
Bildet das semantische und informationelle Fundament der Organisation:
- **Semantik & Ontologie [E]:** Maschinenlesbare Begrifflichkeiten (Glossare, Ontologien, Taxonomien) und einheitliche Informationsmodelle für geteilte Geschäftsobjekte zur Sicherung der sprachlichen Eindeutigkeit.
- **Datenverträge (Contracts) [E]:** Explizite, maschinenlesbare Schnittstellen-, Schema- und Qualitätsvereinbarungen (SLAs/SLOs), die Produzenten und Konsumenten verlässlich entkoppeln.
- **Datenprodukte (Dataproducts) [A]:** Autonome, versionierte und qualitätsgesicherte Datenbestände für operative und analytische Zwecke (inkl. Reporting-Marts, Feature Stores und Wissensgraphen) nach dem Prinzip *Data as a Product*.

---

### Tier 5: Foundation (Plattform- & Betriebsfundament)
Stellt die standardisierten technischen Basisfähigkeiten bereit:
- **Platform & Infrastructure [E]:** Hosting, Cloud- und On-Premises-Ressourcen, Container-Plattformen (z. B. OpenShift, Kubernetes), Developer Platforms und Delivery-Tooling (z. B. GitLab, Backstage, CI/CD-Pipelines) sowie Netzwerk.
- **Data Storage & Management [E]:** Operative Persistenz (RDBMS, NoSQL, Object Storage), Datensicherung und Replikation sowie technische Data-Management-Plattformen (z. B. Software-Lösungen für Datenkataloge, Metadaten-Repositories, Schema-Registries).
- **Analytics Platform & Tooling [E]:** Plattformwerkzeuge für DWH, Data Lakehouse, Streaming-Infrastruktur (z. B. Kafka-Clusterbetrieb), BI und ML-Infrastruktur.
- **Observability & Resilienz [E]:** Zentrales Telemetrie-Fundament (Logs, Metriken, Distributed Tracing), Health Checks und Notfallwiederherstellung (DR/BCM).
- **Security & Identity [E]:** Identity & Access Management (IAM), Least-Privilege-Berechtigungsmodelle, Zero-Trust-Netzwerke und Secret Management.

---

## 5. Beziehungen und Zusammenspiel (Interaktionsmodell)

Das Zusammenspiel der Tiers und Bausteine folgt festen architektonischen Beziehungsregeln:

### 5.1 Der operative Dreiklang und die Domänen-Schnittmenge
Der operative Kern der Unternehmenslandschaft fungiert als Dreiklang aus Fachlichkeit (Tier 2), Software-Ausführung (Tier 3) und Information (Tier 4):

1. **Die Domäne als soziotechnische Klammer (Bounded Context) [E]:**  
   Fachdomänen bilden die primäre Gliederungs- und Eigentumsgrenze der Organisation. Ein Bounded Context nach Domain-Driven Design (DDD) vereint die fachlichen Capabilities und Prozesse (Tier 2), die realisierenden Services und Workflows (Tier 3) sowie die Verantwortung für deren Datenbestände (Tier 4 Domain Data Ownership) in der Hand eines autonomen, domänenverantwortlichen Teams.
2. **Realisierungsachse Business zu System (Realization) [E]:**  
   - *Value Streams und Prozesse (Tier 2) steuern Workflows & Orchestrierung (Tier 3):* Jeder technische Ablauf ist direkt auf einen Geschäftsprozess rückführbar.
   - *Business Capabilities (Tier 2) strukturieren Services & Applications (Tier 3):* Softwarekomponenten kapseln abgegrenzte fachliche Fähigkeiten und sichern deren kohärente Realisierung.
3. **Verankerung System zu Data [A]:**  
   - *Services (Tier 3) operationalisieren die dezentrale Datenhoheit ihrer Domäne:* Fachservices verwalten ihre operative Persistenz autonom.
   - *Domänenübergreifende Interaktion basiert auf Semantik und Verträgen (Tier 4):* Schnittstellen und Datenaustausch basieren auf standardisierten Data Contracts und maschinenlesbaren Schemata.
   - *Services publizieren und konsumieren Datenprodukte (Tier 4):* Der analytische und operative Mehrwert wird über versionierte, vertraglich zugesicherte Datenprodukte bereitgestellt.

### 5.2 Gateway-Schnittstellen (Übergänge des operativen Kerns)
Die beiden Gateways steuern und schützen die funktionalen Übergänge, die vom zentralen Domänen-Konvergenzpunkt ausgehen und den Datenraum gegenüber Fachlichkeit und Software-Ausführung aufspannen:
- **Experience-Gateway (Übergang Business zu Data) [A]:** Verbindet die fachliche Wertschöpfung (Tier 2) mit dem semantischen Datenraum (Tier 4). Es entkoppelt menschliche Akteure (Kunden, Mitarbeiter) von technischen Implementierungsdetails: Nutzer interagieren mit stabilen Geschäftsfähigkeiten auf Basis einheitlicher Semantik und Datenprodukte – unabhängig von Endgeräten, UI-Frameworks oder physischen Interaktionskanälen.
- **Integration-Gateway (Übergang System zu Data) [E]:** Verbindet die operative Software-Ausführung (Tier 3) mit dem semantischen Datenraum (Tier 4). Es kapselt die maschinelle Interaktion (System-zu-System, Partner, Drittanbieter) und sichert den domänenübergreifenden Datenaustausch durch maschinenlesbare Schnittstellenverträge (Contracts), API-Management und Event-Broker – technologieneutral (REST, Event-Driven, Messaging).

### 5.3 Domänenübergreifende Interaktion (Cross-Domain Pattern)
Services und Applikationen interagieren über die Integrationsschicht mit anderen Domänen und deren Services. Verbindliche Schnittstellenverträge und wohldefinierte Informationsmodelle der Zieldomäne sichern dabei die semantische Integrität und fungieren als natürlicher Anti-Corruption Layer.

### 5.4 Rückkopplungsbeziehungen (Feedback-Schleifen)
Architekturbeziehungen sind keine Einbahnstraße. Aggregierte Informationen und Messwerte fließen strukturiert zurück, um operative Ausführung und fachliche Weiterentwicklung zu speisen:
- **Datenprodukte (Tier 4) steuern Workflows & Orchestrierung (Tier 3):** Analytische und inferierende Datenprodukte (z. B. Scoring-Modelle, Klassifikatoren) werden von Workflow-Engines konsumiert, um Verzweigungen automatisiert und datenbasiert in Echtzeit zu steuern (*operative Rückkopplung*).
- **Datenprodukte (Tier 4) informieren und optimieren den Business Layer (Tier 2):** Aggregierte Datenprodukte (Reporting-Marts, Nutzungs- und KPI-Analysen) liefern die empirische Basis für Prozessanpassungen, Touchpoint-Optimierungen (Experience) und strategische Capability-Investitionen (*fachlich-analytische Rückkopplung*).
- **Observability & Resilienz (Tier 5) optimiert Prozesse und Workflows (Tier 2/3):** Laufzeitmetriken zu Durchlaufzeiten, Fehlerraten und Systemlatenzen decken operative Engpässe auf und treiben die kontinuierliche Fehlerbeseitigung (*diagnostische Rückkopplung*).

### 5.5 Schichten-Interaktionsmatrix

Die zulässigen Interaktionsbeziehungen zwischen den fünf Schichten des Referenzmodells werden über eine formale Kantenmatrix gesteuert. Sie projiziert die vier orthogonalen Relationen des Metamodells (`governs`, `realizes`, `enables`, `utilizes` aus Abschnitt 2.2) auf das Zusammenspiel der Schichten. Jede Zelle definiert, welche Beziehungssemantik von der Quellschicht (Zeile) in Richtung der Zielschicht (Spalte) architektonisch zulässig ist. Nicht unmittelbar miteinander interagierende oder getrennte Schichten sind als `n/a` gekennzeichnet:

| Quelle (Zeile) \ Ziel (Spalte) | Tier 1: Governance | Tier 2: Business | Tier 3: System | Tier 4: Data | Tier 5: Foundation |
|---|---|---|---|---|---|
| **Tier 1: Governance** | — | governs | governs | governs | governs |
| **Tier 2: Business** | n/a | — | utilizes | utilizes | n/a |
| **Tier 3: System** | n/a | realizes | utilizes | utilizes | utilizes |
| **Tier 4: Data** | n/a | enables | enables | — | utilizes |
| **Tier 5: Foundation** | n/a | n/a | enables | enables | — |

**Projektion der Metamodell-Kanten auf die Schichten:**
- `governs`: Tier 1 setzt normative Leitplanken, Richtlinien, RACI-Rollen und Technologievorgaben für alle operativen und infrastrukturellen Schichten durch.
- `realizes`: Technische Applikationen und Workflows (Tier 3) realisieren die fachlichen Fähigkeiten (Capabilities) und Geschäftsprozesse (Tier 2).
- `enables`: Zugrundeliegende Plattformfähigkeiten (Tier 5) befähigen Systeme und Daten mit Laufzeit-, Speicher- und Resilienzressourcen; der Data Layer (Tier 4) befähigt Fachlichkeit und Software-Ausführung mit verlässlicher Information und Semantik.
- `utilizes`: Fachprozesse (Tier 2) nutzen Applikationen und Daten; Applikationen (Tier 3) nutzen andere Applikationen (z. B. Workflows nutzen Services), Datenprodukte und Plattformdienste; Datenprodukte nutzen physische Persistenz- und Kataloginfrastrukturen der Foundation.

### 5.6 Architektonische Invarianten

Zur Vermeidung typischer Architektur-Antipatterns und architektonischer Erosion erzwingt das Interaktionsmodell die vier im Metamodell verankerten Integritätsaxiome (Abschnitt 2.3):

1. **Invariante der Schichtenkapselung (No Layer Skipping) [E]:**  
   Fachliche Prozesse und Capabilities (Tier 2) dürfen niemals direkte Abhängigkeiten auf infrastrukturelle Plattform-Ressourcen (Tier 5) aufbauen (in der Matrix als `n/a` ausgewiesen). Jede Interaktion zwischen Fachlichkeit und Infrastruktur wird über Software-Applikationen (Tier 3) vermittelt. Umgekehrt stellt die Foundation keine fachspezifische Geschäftslogik bereit.
2. **Invariante der semantischen Koppelung (No Shared Database) [E]:**  
   Domänenübergreifende Interaktionen zwischen Systemen (Tier 3) erfolgen niemals über gemeinsame, ungeschützte Datenbankspeicher. Der domänenübergreifende Datenaustausch erfolgt ausnahmslos über vertraglich gesicherte Datenprodukte oder maschinenlesbare Schnittstellenverträge (Tier 4) unter Einhaltung des Bounded-Context-Prinzips.
3. **Invariante der Gateway-Schranke (No Unguarded Ingress/Egress) [E]:**  
   Keine externe Interaktion (weder menschliche/agentische Nutzerinteraktion noch maschinelle Partner-Integration) erreicht Applikationen oder Datenbestände unter Umgehung der jeweiligen Gateway-Schranke (`ExperienceGateway` bzw. `IntegrationGateway`). Gateways erzwingen Authentifizierung, Schema-Validierung, Ratenbegrenzung und Entkopplung.
4. **Invariante der Vertragsdisziplin (No Contract, No Call) [A]:**  
   Applikationen und Datenprodukte dürfen erst dann domänenübergreifend bereitgestellt oder konsumiert werden, wenn ein maschinenlesbarer Vertrag (API Contract, Data Contract) mit definierten SLAs/SLOs und Schema-Definitionen in Tier 4 publiziert und versioniert ist.

---

## 6. Guiding Principles

Die **Guiding Principles** definieren die grundlegenden architektonischen Gestaltungsmaximen und qualitativen Leitplanken der Organisation und wirken in allen Schichten der Unternehmenslandschaft.

Während **Tier 1 (Governance)** den formalen und regulatorischen Steuerungsrahmen (Roadmaps, Rollen/RACI, verbindliche Technologiestacks, Compliance-Vorgaben) bereitstellt, geben die **Guiding Principles** die übergreifende architektonische Denkweise und Orientierung für jedes Systemdesign, jede Transformation und jede Investitionsentscheidung vor.

Sie wirken transversal über die gesamte Landschaft und gliedern sich in drei korrespondierende Ebenen:

| Prinzipien-Ebene | Adressierte Schichten | Kernleitplanken für die Gestaltung |
|---|---|---|
| **Business & Organization** | Tier 1 (Governance)<br>Tier 2 (Business Layer) | **Conway's Law beachten:** Organisations- und Teamstrukturen formen die Systemarchitektur (aktive Nutzung des Inverse Conway Maneuver).<br>**Echtes Domain Ownership:** Klare, langlebige Ende-zu-Ende-Verantwortung für fachliche Fähigkeiten und Datenbestände in autonomen Teams.<br>**Capability-Zentrierung:** Investitionen, Modularisierung und Sourcing richten sich an strategischen Geschäftsfähigkeiten (Core vs. Supporting vs. Commodity) aus. |
| **Application & Data** | Tier 3 (System Layer)<br>Tier 4 (Data Layer) | **Loose Coupling & Contract-First:** Systeme interagieren ausschließlich über explizite, versionierte und maschinenlesbare Schnittstellen- und Datenverträge.<br>**Data as a Product:** Daten werden als autonome, wertstiftende Produkte mit garantierten SLAs/SLOs bereitgestellt, nicht als unkontrollierte Nebenprodukte von Anwendungsspeichern.<br>**Semantik vor Implementierung:** Fachliche und sprachliche Eindeutigkeit (Ubiquitous Language) besitzt Vorrang vor technischen Programmierdetails.<br>**Single Source of Truth:** Eindeutiges Golden Master und klare Hoheit für jedes geschäftskritische Geschäftsobjekt. |
| **Platform & Security** | Tier 5 (Foundation) | **Zero Trust by Default:** Keine implizite Netzwerksicherheit; Verifikation, Authentifizierung und Least-Privilege an jedem Systemübergang.<br>**Everything as Code:** Reproduzierbare, deklarative Plattformressourcen, Infrastrukturen und Automatisierungs-Pipelines.<br>**Observability by Default:** Telemetrie, Distributed Tracing und Metriken sind integrale, nicht verhandelbare Bestandteile jedes Systems.<br>**Resilienz vor Ausfallvermeidung:** Systeme werden auf unvermeidbare Teilausfälle hin entworfen (Graceful Degradation, Circuit Breaker, Self-Healing). |
