# Enterprise Landscape Model (ELM) — Spezifikation

**Klassifikation:** Enterprise Architecture Framework  
**Kern-Artefakt:** Kanonisches Referenzmodell  
**Version:** 0.8  
**Status:** Public Preview  
**Autor:** Julia Senner (Enterprise & Solution Architecture)  
**Relevante Materialien:** [enterprise-landscape-model.pptx](assets/enterprise-landscape-model.pptx) (Vektor-Vorlage) / [enterprise-landscape-model.png](assets/enterprise-landscape-model.png) (Diagramm)  

---

## 1. Zweck, Grundprinzipien und Geltungsbereich

### 1.1 Zweck und architektonische Einordnung

Das **Enterprise Landscape Model (ELM)** ist ein eigenständiges, modernes Enterprise Architecture Management (EAM) Framework. Es bietet ein hersteller- und branchenneutrales, formales Referenzmodell, um tragfähige, evolvierbare und resilient wartbare Unternehmens- und Systemlandschaften zu gestalten. Das ELM überwindet Silos zwischen Unternehmensführung, Fachbereich, Software-Engineering und Plattformbetrieb, ohne in die bürokratische Trägheit und Vorratsmodellierung klassischer Großframeworks zu verfallen.

Konzeptionell orientiert sich das ELM an den Grundbegriffen der ISO/IEC/IEEE 42010 (Architektur, Stakeholder Concerns, Viewpoints) als methodische Basis und fokussiert auf eine schlanke, werkzeugneutrale Beschreibung für die praktische Anwendung.

Das ELM gliedert sich in drei komplementäre Ebenen:

1. **ELM Lean Metamodel (Formale Ontologie):** Definiert die minimale Menge an Entitätstypen und typisierten Beziehungen, um Architekturbeschreibungen maschinenlesbar, auditierbar und in EAM-Werkzeugen abbildbar zu machen (Kapitel 2).
2. **ELM Canonical Reference Model (Kanonisches Referenzmodell):** Definiert die verbindliche Soll-Topologie aus fünf Schichten, Entkopplungsgateways und Guiding Principles als wiederverwendbares Strukturmuster für moderne Unternehmenslandschaften (dieses Dokument, Kapitel 3 bis 5).
3. **ELM Ökosystem (Modulare Modellerweiterungen):** Vertikale Schichten-Vertiefungen (`segments/`) als Zoom-ins und transversale thematische Projektionen (`overlays/`) als Zoom-outs über alle Schichten.

Das Referenzmodell operationalisiert die funktionale Triade der Architekturarbeit:
1. **Normativ:** Verbindliche Definition der Schichten, funktionalen Bausteine, Entkopplungsgateways und Interaktionsregeln für eine tragfähige Zielarchitektur.
2. **Diagnostisch:** Neutrales, auditierbares Prüfraster für Architektur-Reviews, um strukturelle Brüche, fehlende Entkopplung, unklare Datenhoheit und Schichteninkonsistenzen objektiv nachzuweisen.
3. **Kommunikativ:** Gemeinsame visuelle und begriffliche Orientierung zur Abstimmung über Rollen- und Disziplingrenzen hinweg.

### 1.2 Zielgruppen- und Nutzenmatrix

Als interdisziplinäre Disziplin verbindet das Enterprise Architecture Management (EAM) die strategischen, fachlichen und technischen Perspektiven der Organisation. Die Matrix ordnet den zentralen Stakeholder-Gruppen ihren primären Nutzen und Fokus im Modell zu:

| Zielgruppe | Adressierte Stakeholder Concerns | Primärer architektonischer Nutzen | Relevanter Modellfokus |
|---|---|---|---|
| **Executive & Steering** | Investitionssicherheit, Portfoliotransparenz, strategische Handlungsfähigkeit, regulatorische Compliance | Makro-Transparenz über Abhängigkeiten und Zukunftsfähigkeit der Landschaft; fundierte Entscheidungsgrundlage für Budgetierung und strategische Steuerung ohne Detailballast. | Tier 1 (Guidance), Guiding Principles |
| **Business & Product** | Time-to-Market, Reaktionsgeschwindigkeit auf Marktveränderungen, funktionale Differenzierung, organisatorische Autonomie | Klare Zuordnung von Fähigkeiten (Capabilities) zu Wertströmen; fachliche Autonomie und gezielte Kapselung von Domänen zur Reduzierung organisatorischer Abhängigkeiten. | Tier 2 (Business Layer), Experience Gateway |
| **Architecture & Engineering** | Evolvierbarkeit, Wartbarkeit, Interoperabilität, Beherrschung von Systemkomplexität, Steuerung von Kopplungsrisiken und technischen Schulden | Verbindliche System- und Integrationsgrenzen; strukturierte Entkopplung über Gateways und definierte Schichtenbeziehungen zur Vermeidung unkontrollierter Punkt-zu-Punkt-Verbindungen. | Tier 3 (System Layer), Integration Gateway |
| **Data Architecture & Analytics** | Verlässliche Datenqualität, klare Datenverantwortung, semantische Eindeutigkeit, Stabilität domänenübergreifender Datenflüsse | Ablösung monolithischer Datensilos durch Domain Data Ownership; Durchsetzung maschinenlesbarer Data Contracts und verlässlich operationalisierter Datenprodukte. | Tier 4 (Data Layer), Domäne (Bounded Context) |
| **Platform Engineering** | Betriebsstabilität, Skalierbarkeit, Bereitstellungseffizienz, Developer Experience | Entlastung der Anwendungsteams durch standardisierte, automatisierte Self-Service-Plattformfähigkeiten (Compute, Storage, CI/CD-Pipelines). | Tier 5 (Foundation: Platform & Infrastructure, Data Storage) |
| **Security & Operations** | Informationssicherheit, kontrollierte Zugriffssteuerung, Systemintegrität, durchgängige Revisionssicherheit (Audit-Readiness) | Durchgängige technische Verifikation und Zugriffskontrolle an allen System- und Plattformübergängen; automatisierte Nachweisbarkeit regulatorischer Schutzziele in Betrieb und Laufzeit. | Tier 5 (Foundation: Security & Identity, Observability), Gateways |

### 1.3 Geltungsbereich und Abgrenzung

Das Modell adressiert die ganzheitliche Unternehmenslandschaft als soziotechnisches Gesamtsystem:

- **Abgedeckter Gestaltungsraum:** Der Gestaltungsraum umfasst das soziotechnische Gesamtsystem des Unternehmens: von der strategischen und normativen Unternehmenssteuerung über die fachliche Wertschöpfung, Geschäftsfähigkeiten und Geschäftsprozesse, die softwaretechnische Anwendungs- und Systemlandschaft sowie die unternehmensweite Informations- und Datenarchitektur bis hin zum technologischen Betriebs- und Plattformfundament.
- **Hebelwirkung in komplexen Organisationen:** Seine primäre Steuerungs- und Diagnosewirkung entfaltet das Modell in gewachsenen, verteilten Organisationen mit hoher Fach- und Transaktionskomplexität, heterogenen Systembeständen und regulatorischen Anforderungen.
- **Hersteller- und Technologieunabhängigkeit:** Alle Konzepte, Bausteine und Interaktionsmuster sind technologieneutral formuliert und gelten unabhängig von spezifischen Cloud-Providern, Standardsoftware-Produkten oder Programmiersprachen.
- **Fokus auf Makro-Architektur:** Das Modell beschreibt die Makro-Architektur der Gesamtlandschaft. Es ersetzt weder das feingranulare Softwaredesign einzelner Services (z. B. Klassendiagramme, Framework-Auswahl, Tabellenschemata auf Spaltenebene) noch tiefes Netzwerk- und Betriebssystem-Engineering.

### 1.4 Gestalterische Grundprinzipien des Modells

Die Konstruktion des Referenzmodells folgt vier tragenden Grundgedanken:

- **Handlungsfähigkeit vor Vorratsmodellierung (Lean Architecture):** Das Modell beschränkt sich bewusst auf die strukturellen Elemente und Übergänge, die für strategische Steuerung, Domänenschnitt und Entkopplung entscheidungsrelevant sind. Es verzichtet auf flächendeckende Inventarisierung oder Prozessbürokratie und wächst bedarfsorientiert über Segmente und Overlays.
- **Anschlussfähigkeit für gewachsene Landschaften:** Unternehmensarchitektur entsteht selten auf der grünen Wiese. Das Modell ist so geschnitten, dass es heterogene Bestandsrealitäten, vom gekapselten Kernsystem-Monolithen über Standardsoftware (COTS/SaaS) bis zu modularen Eigenentwicklungen, ohne künstliche Modellierungsbrüche abbilden und schrittweise weiterentwickeln kann.
- **Soziotechnische Kohärenz:** Systemarchitektur, Fachlichkeit und Organisationsstruktur bedingen sich wechselseitig (Conway's Law). Das Modell verbindet deshalb Geschäftsfähigkeiten, Anwendungen und Datenverantwortung entlang fachlicher Domänen, statt IT-Systeme isoliert von Organisation und Wertschöpfung zu betrachten.
- **Autonomie im Inneren, explizite Verträge an den Grenzen:** Unternehmensweite Zentralschemata scheitern in komplexen Organisationen an ihrer Kopplungstiefe. Das Modell setzt auf fachliche und technische Eigenständigkeit innerhalb der Domänen und regelt das Zusammenspiel über definierte Grenzschranken (Gateways), maschinenlesbare Schnittstellenverträge (Contracts) und klar verantwortete Datenprodukte.

### 1.5 Klassifizierung von Prüfkriterien

In Segmenten (`segments/`), thematischen Overlays (`overlays/`) und Architektur-Reviews (`canvases/`) wird die Verbindlichkeit von Aussagen und Prüfkriterien nach drei Stufen klassifiziert:

| Kategorie | Bedeutung | Konsequenz für die Bewertung |
|---|---|---|
| **Etablierte Praxis [E]** | In Industrie- und Architekturstandards, anerkannter Fachliteratur oder Regulatorik (z. B. DORA, DSGVO) belegt. | Verbindlich; darf in der Zielarchitektur nicht unterschritten werden. |
| **Abgeleitete Praxis [A]** | Aus empirischen Befunden, wiederkehrenden Fehlermustern und Praxis realer Transformationsprojekte gewonnen. | Pragmatisch begründet; im Kontext spezifischer Rahmenbedingungen anpassbar. |
| **Hypothese [H]** | Plausible, schlüssige Arbeitsthese, die noch nicht empirisch breit abgesichert ist. | Diskursiv; darf niemals die alleinige Basis für verbindliche Architekturentscheidungen bilden. |

### 1.6 Modulare Erweiterbarkeit: Segmente und Overlays

Das Enterprise Landscape Reference Model folgt dem architektonischen Zoom-in / Zoom-out Prinzip und lässt sich über zwei standardisierte Erweiterungsmechanismen präzise skalieren:

1. **Segment-Architekturen (`segments/`, Zoom-in):** Vertikale Tiefenschnitte in einzelne Schichten oder Domänen (z. B. der detaillierte Capability-Zuschnitt im Business Layer).
2. **Thematische Overlays (`overlays/`, Zoom-out & Querschnitt):** Transversale Projektionen spezifischer Fragestellungen über alle Schichten des Modells (z. B. [AI-Readiness](../overlays/ai-readiness/ai-readiness-overlay.md), Cloud-Native, Resilienz).

---

## 2. Das ELM Lean Metamodel

Das Metamodell definiert die formale, sprach- und werkzeugneutrale Ontologie des ELM. Es stellt sicher, dass Architekturbeschreibungen präzise strukturiert, werkzeugneutral in Enterprise-Architecture-Management-Systemen abbildbar und automatisiert auditierbar sind.

Das Metamodell besteht aus zwei orthogonalen Komponenten:
1. **Kanonische Meta-Entitäten (Knotentypen):** Die formalen Bausteinklassen der Unternehmenslandschaft.
2. **Typisierte Meta-Relationen (Kanten):** Die orthogonalen Basis-Beziehungsarten zwischen Entitäten.

### 2.1 Kanonische Meta-Entitäten (Knotentypen)

| ELM Metaklasse | Ontologische Kategorie | Semantische Definition & Rolle |
|---|---|---|
| **`StrategicObjective`** | Steuerung (Guidance) | Unternehmens- und Architektur-Vision, strategisches Zielbild oder Portfolio-Vorgabe (`Vision & Strategy`) |
| **`OrganizationalUnit`** | Steuerung (Guidance) | Soziotechnische Einheit, Team-Topologie oder Rollen- und Ownership-Profil (`People, Culture & Organization`) |
| **`EnterpriseGuardrail`** | Steuerung (Guidance) | Verbindliche Unternehmens- und Architektur-Policy, operative Landschafts-Guardrail oder Referenz-Blueprint (`Policies, Guardrails & Blueprints`) |
| **`ComplianceRequirement`** | Steuerung (Guidance) | Vertrauens- und Ethik-Anspruch, risikobasierter Schutzbedarf oder regulatorische Vorgabe (`Trust, Risk & Compliance`) |
| **`GuidingPrinciple`** | Leitprinzipien | Übergreifende architektonische Gestaltungsmaxime und Entscheidungsheuristik bei Zielkonflikten (`Guiding Principles`) |
| **`ValueStream`** | Business | Sequenz von wertschöpfenden Schritten zur Erbringung eines Kundennutzens (End-to-End) |
| **`BusinessCapability`** | Business | Stabile, technologie- und organisationsneutrale Geschäftsfähigkeit („Was tut das Unternehmen?“) |
| **`BusinessProcess`** | Business | Fachlicher Ablauf mit definierter Ausführungslogik, Vorbedingungen und Prozesszielen |
| **`Domain`** | Kontext | Soziotechnische Einheit (Bounded Context) mit einheitlicher Ubiquitous Language und Domain Ownership |
| **`ExperienceGateway`** | Interaktion | Grenzschranke für Nutzer- und Agenteninteraktion: Entkoppelt Mensch/Agent von Systemdetails; sichert Kanalneutralität |
| **`IntegrationGateway`** | Interaktion | Grenzschranke für System- und Partnerinteraktion: API-Management, Event-Broker, Authentifizierung, Rate Limiting |
| **`Workflow`** | Systeme | Zustandstragende technische Prozessausführung, Saga-Orchestrierung und Batch-/Stream-Pipelines |
| **`Application`** | Systeme | Ausführbare Software-Einheit: modularer Fachservice, Standardsoftware (COTS), SaaS oder gekapselter Kernmonolith |
| **`SemanticEntity`** | Daten | Fachliches Geschäftsobjekt, Fachbegriff oder Ontologie-Knoten der Ubiquitous Language |
| **`DataContract`** | Daten | Maschinenlesbare Schema- und Qualitätsspezifikation (SLAs/SLOs) zwischen Datenanbietern und -konsumenten |
| **`DataProduct`** | Daten | Autonomer, versionierter und qualitätsgesicherter Datenbestand mit dezentralem Ownership |
| **`PlatformCapability`** | Technologie | Standardisierte Basisfähigkeit für Compute, Storage, IAM, CI/CD und Observability |

### 2.2 Typisierte Meta-Relationen (Kanten-Grammatik)

| Metamodell-Relation | Semantische Definition | Architektonischer Geltungsbereich |
|---|---|---|
| **`owns`** | Strukturelle Klammer und eindeutige soziotechnische Verantwortung (Domain Ownership). | Soziotechnische Eigentümergrenzen (`Domain`) auf alle gekapselten Elemente innerhalb desselben Bounded Context (`BusinessCapability`, `BusinessProcess`, `Workflow`, `Application`, `SemanticEntity`, `DataContract`, `DataProduct`) |
| **`guides`** | Strategische Orientierung, organisatorische Rahmung, verbindliche Leitplanke oder regulatorische Vorgabe. | Übergreifende Leitprinzipien (`GuidingPrinciple`) auf die Leitplanken in Tier 1 (`EnterpriseGuardrail`) sowie steuernde und regulierende Instanzen (`StrategicObjective`, `OrganizationalUnit`, `EnterpriseGuardrail`, `ComplianceRequirement`) auf Domänen und alle fachlichen, operativen und infrastrukturellen Elemente (Tier 2 bis 5) |
| **`enables`** | Bereitstellung funktionaler, operativer, informationeller oder infrastruktureller Grundlagen (Serving). | Dienende und ausführende Elemente auf darüberliegende Schichten: Plattformfähigkeiten (Tier 5) auf Systeme und Daten (Tier 3/4), Datenprodukte und Semantik (Tier 4) auf Systeme, Fachlichkeit und Steuerung (Tier 3, 2, 1) sowie Systeme und Workflows (Tier 3) auf Geschäftsprozesse und Geschäftsfähigkeiten (Tier 2) |
| **`utilizes`** | Operative Nutzung, Konsum von Schnittstellen, Systemen, Datenbeständen oder Plattformressourcen. | Konsumierende Elemente auf vertikal oder horizontal bereitgestellte Fähigkeiten, Services, Datenprodukte oder Plattformdienste (komplementäre Gegenrichtung zu `enables`) |

---

## 3. Architekturübersicht und Topologie

![Enterprise Landscape Reference Model](assets/enterprise-landscape-model.png)

Das Referenzmodell gliedert die Unternehmenslandschaft in **fünf strukturelle Schichten (Tiers)**, **zwei Gateway-Schnittstellen** und übergreifende **Leitprinzipien (Guiding Principles)**:

- **Horizontale Rahmung:**
  - **Tier 1: Guidance:** Strategischer, soziotechnischer, normativer und regulatorischer Orientierungs- und Steuerungsrahmen (vereint richtungsgebendes Enablement mit verbindlichen Leitplanken).
  - **Tier 5: Foundation:** Technologisches Betriebs- und Plattformfundament.
- **Operativer Kern (Der funktionale Dreiklang):**
  - **Tier 2: Business Layer:** Fachliche Wertschöpfung, Geschäftsfähigkeiten und Geschäftsprozesse.
  - **Tier 3: System Layer:** Technische Ablaufsteuerung und operative Software-Systeme.
  - **Tier 4: Data Layer:** Semantisches und informationelles Fundament (Semantik, Datenverträge, Datenprodukte).
  - **Die Domäne (Bounded Context):** Die verbindende soziotechnische Schnittmenge im Zentrum des operativen Dreiklangs, die Fachlichkeit (Tier 2), Applikationen und Services (Tier 3) und Datenhoheit (Tier 4) unter einem einheitlichen Domain Ownership klammert.
- **Gateway-Schnittstellen (Außengrenzen des operativen Kerns):**
  - **Experience** (Tier 2/4): Kanal- und Nutzerentkopplung für menschliche Akteure und Agenten.
  - **Integration** (Tier 3/4): System- und Partnerentkopplung für maschinelle Schnittstellen.
- **Steuerungsrahmen:**
  - **Guiding Principles:** Übergreifende architektonische Entscheidungsheuristiken und Gestaltungsmaximen für Business & Organization, Application & Data sowie Platform & Security.

### 3.1 Topologie und Raumaufteilung der Referenzarchitektur

Die visuelle Komposition des ELM folgt einer strikten funktionalen Raumaufteilung:

1. **Horizontale Rahmung:**  
   - **Tier 1 (Guidance)** bildet das strategische, organisatorische und normative Dach.  
   - **Tier 5 (Foundation)** stellt das gemeinsame technologische Betriebs- und Plattformfundament bereit.
2. **Die funktionale Dreiteilung des operativen Raums:**  
   Der Raum zwischen Guidance und Foundation teilt sich in drei gleichwertige funktionale Sektoren:
   - **Obere Zone (Tier 2 Business Layer):** Fachliche Wertschöpfung, Value Streams, Business Capabilities und Business Processes.
   - **Untere Zone (Tier 3 System Layer):** Operative Software-Systeme, Services und technische Ablaufsteuerung.
   - **Rechte Zone (Tier 4 Data Layer):** Semantik, maschinenlesbare Schemata, Data Contracts und Data Products (beschriftet über das vertikale Tab-Label rechts).
3. **Der Konvergenzpunkt im Zentrum (Die Domäne):**  
   Dort, wo die Trennlinien der drei Sektoren im Zentrum zusammenlaufen, sitzt das architektonische Alignment: Hier manifestiert sich die **Domäne (der Bounded Context)** als soziotechnische Schnittmenge, die Fachlichkeit, Software und Datenhoheit für ein Thema vereint.
4. **Flankierende Leitplanken:**  
   Die rechte Außensäule fasst die **Guiding Principles** zusammen, die als überzeitliche Entscheidungsheuristiken quer über alle Schichten und Zonen wirken.

---

## 4. Schichten und Bausteine (Strukturmodell)

Das Strukturmodell umfasst die fünf Schichten (Tiers) sowie die flankierenden Guiding Principles mit ihren jeweils klar definierten funktionalen Architekturbausteinen:

### Tier 1: Guidance (Strategische Steuerung, Organisation & Leitplanken)
Definiert den strategischen, soziotechnischen, normativen und regulatorischen Orientierungs- und Steuerungsrahmen der Unternehmenslandschaft:
- **Vision & Strategy:** Unternehmens- und Architektur-Vision als gemeinsamer Nordstern, strategisches Makro-Zielbild (Target Landscape) sowie wertorientierte Portfolio- und Investitionssteuerung im Spannungsfeld zwischen stabilem Betrieb und Erneuerung (Run vs. Change).
- **People, Culture & Organization:** Soziotechnische Ausgestaltung der Organisation vom Menschen her gedacht: Entwicklung und Wertschätzung von Fähigkeiten, Rollen und individueller Selbstwirksamkeit (`People`: Skills, Agency & Mastery), getragen von gelebter Lernkultur, psychologischer Sicherheit sowie geteilten Architektur- und Engineering-Routinen (`Culture`: Enablement, Communities of Practice) und strukturell ermöglicht durch einen bewussten Team- und Domänenzuschnitt entlang der Geschäftsfähigkeiten bei gesteuerter kognitiver Last (`Organization`: Team Topologies, Inverse Conway Maneuver).
- **Policies, Guardrails & Blueprints:** Interne architektonische Leitplanken, die die übergeordneten *Guiding Principles* in konkret prüfbare Vorgaben übersetzen: verbindliche Architektur-Richtlinien und Direktiven (`Policies`), operative Schranken zur Sicherung autonomer Entscheidungsspielräume der Teams (`Guardrails`) sowie wiederverwendbare Makro-Referenzarchitekturen und Lösungsmuster (`Blueprints`).
- **Trust, Risk & Compliance:** Schutz- und Sorgfaltsrahmen gegenüber Kunden, Markt und Aufsicht: Vertrauen durch souveränen, ethischen Umgang mit Daten und KI als eigentlicher Nordstern (`Trust`), risikobasierte Steuerung und proportionale Schutzmaßnahmen bei IKT-, Drittparteien- und Cyber-Risiken (`Risk`) sowie die nachweisbare Einhaltung gesetzlicher und aufsichtsrechtlicher Vorgaben wie DORA, DSGVO, NIS-2 und EU AI Act (`Compliance`).

---

### Tier 2: Business Layer (Operative Wertschöpfung)
Bildet die fachliche Wertschöpfung der Organisation ab:
- **Value Streams:** End-to-End-Wertströme zur Erbringung von Kundennutzen.
- **Business Capabilities:** Stabile, technologieunabhängige Fähigkeiten der Organisation (Differenzierung nach Core, Supporting, Generic).
- **Business Processes:** Fachliche Abläufe mit definierter logischer und zeitlicher Reihenfolge.
- **Experience (Gateway):** Zugangskanäle und Interaktionspunkte (Omni-Channel-Architektur, Customer Journey Touchpoints) zur kanalneutralen Entkopplung von Kunden, Mitarbeitern, Partnern und Agenten.

---

### Tier 3: System Layer (Operative Ausführung)
Bildet die technische Software- und Ausführungslandschaft ab:
- **Workflows & Orchestration:** Technische Ablaufsteuerung, Saga-Orchestrierung sowie synchrone APIs, asynchrone Queues und ereignisgesteuerte Streaming-Pipelines.
- **Services & Applications:** Ausführbare Software-Einheiten: modulare Fachservices (Microservices), integrierte Standardsoftware (COTS/SaaS) und gekapselte Kernsystem-Monolithen.
- **Integration (Gateway):** Technische Integrationsschicht (API Gateways, Event Broker, Enterprise Messaging) zur Entkopplung system- und domänenübergreifender Kommunikation.

---

### Tier 4: Data Layer (Information & Semantik)
Bildet das semantische und informationelle Fundament der Organisation:
- **Semantics & Ontology:** Maschinenlesbare Begrifflichkeiten (Glossare, Ontologien, Taxonomien) und domänenspezifische Informationsmodelle zur Sicherung der sprachlichen Eindeutigkeit innerhalb eines Bounded Context.
- **Data Contracts:** Explizite, maschinenlesbare Schnittstellen-, Schema- und Qualitätsvereinbarungen (SLAs/SLOs), die Produzenten und Konsumenten verlässlich entkoppeln.
- **Data Products:** Autonome, versionierte und qualitätsgesicherte Datenbestände für operative und analytische Zwecke (inkl. Reporting-Marts, Feature Stores und Wissensgraphen) nach dem Prinzip *Data as a Product*.

---

### Tier 5: Foundation (Plattform- & Betriebsfundament)
Stellt die standardisierten technischen Basisfähigkeiten bereit:
- **Platform & Infrastructure:** Hosting, Cloud- und On-Premises-Ressourcen, Container-Plattformen (z. B. OpenShift, Kubernetes), Developer Platforms und Delivery-Tooling (z. B. GitLab, Backstage, CI/CD-Pipelines) sowie Netzwerk.
- **Data Storage & Management:** Operative Persistenz (RDBMS, NoSQL, Object Storage), Datensicherung und Replikation sowie technische Data-Management-Plattformen (z. B. Software-Lösungen für Datenkataloge, Metadaten-Repositories, Schema-Registries).
- **Analytics Platform & Tooling:** Plattformwerkzeuge für DWH, Data Lakehouse, Streaming-Infrastruktur (z. B. Kafka-Clusterbetrieb), BI und ML-Infrastruktur.
- **Observability & Resilience:** Zentrales Telemetrie-Fundament (Logs, Metriken, Distributed Tracing), Health Checks und Notfallwiederherstellung (DR/BCM).
- **Security & Identity:** Identity & Access Management (IAM), Least-Privilege-Berechtigungsmodelle, Zero-Trust-Netzwerke und Secret Management.

---

### Guiding Principles (Architektonische Leitlinien)
Die Guiding Principles flankieren die Schichten des Modells als überzeitliche architektonische Gestaltungsmaximen und Entscheidungsheuristiken für Zielkonflikte (`GuidingPrinciple`). Während `Tier 1: Guidance` (insbesondere über `Policies, Guardrails & Blueprints` als `EnterpriseGuardrail`) diese Maximen aufgreift (`guides`) und in den konkreten, kontext- und zeitgebundenen Steuerungsrahmen übersetzt (*„Was gilt konkret?“*), definiert diese Außensäule die grundlegende architektonische Denk- und Abwägungsrichtung der Organisation (*„Nach welchen Maximen entscheiden wir im Zielkonflikt?“*). Sie gliedern sich thematisch in drei Bereiche:
- **Business & Organization:** Leitlinien für Organisationsschnitt, Zusammenarbeit, Entscheidungsfindung sowie Wertstrom- und Capability-Ausrichtung (z. B. Value-Driven Alignment, Buy before Build, Business Continuity).
- **Application & Data:** Leitlinien für Software-, Integrations- und Informationsarchitektur sowie Schnittstellen- und Datenverantwortung (z. B. Loose Coupling, API First, Data as a Product).
- **Platform & Security:** Leitlinien für Infrastruktur, Plattformbetrieb, Automatisierung, Resilienz und Informationssicherheit (z. B. Everything as Code, Observability by Default, Secure by Design).

---

## 5. Beziehungen und Zusammenspiel (Interaktionsmodell)

Das Zusammenspiel der Tiers und Bausteine folgt festen architektonischen Beziehungsregeln:

### 5.1 Der operative Dreiklang, die Domänen-Schnittmenge und die Steuerungsachsen
Der operative Kern der Unternehmenslandschaft fungiert als Dreiklang aus Fachlichkeit (Tier 2), Software-Ausführung (Tier 3) und Information (Tier 4), der aus `Tier 1: Guidance` über zwei komplementäre Wirkachsen ausgerichtet wird:

1. **Die Domäne als soziotechnische Klammer (Bounded Context):**  
   Fachdomänen bilden die primäre Gliederungs- und Verantwortungsgrenze der Organisation. Ein Bounded Context nach Domain-Driven Design (DDD) verbindet die fachlichen Capabilities und Prozesse (Tier 2), die befähigenden Applikationen, Services und Workflows (Tier 3) sowie die Verantwortung für deren Datenbestände (Tier 4 Domain Data Ownership) unter einer klaren Domänenverantwortung (`owns`).
2. **Differenzierte Steuerungsachsen aus Tier 1 (Guidance):**  
   Tier 1 wirkt nicht pauschal auf alle Elemente, sondern leitet (`guides`) den operativen Dreiklang entlang zweier präziser Achsen, die im Data Layer (Tier 4) und in der Domäne zusammenlaufen:
   - *Strategisch-organisatorische Achse (`Vision & Strategy` sowie `People, Culture & Organization`):* Leitet (`guides`) primär den **Business Layer (Tier 2)**, den **Data Layer (Tier 4: Semantics & Domain Data Ownership)** sowie den Zuschnitt der **Domänen**. Hier werden Wertströme und Geschäftsfähigkeiten priorisiert (`StrategicObjective`) und mit dem Team- und Verantwortungszuschnitt (`OrganizationalUnit`) sowie der fachlichen Begriffs- und Datenhoheit in Deckung gebracht.
   - *Normativ-regulatorische Achse (`Policies, Guardrails & Blueprints` sowie `Trust, Risk & Compliance`):* Leitet und begrenzt (`guides`) sowohl den **Business Layer (Tier 2: Kritikalität von Geschäftsfunktionen, fachlicher Verarbeitungszweck und Risikoklassifizierung)** als auch den **System Layer (Tier 3)**, den **Data Layer (Tier 4: Data Contracts & Data Products)** und die **Domänen**, technisch abgesichert und durchgesetzt über die **Gateways** und die **Foundation (Tier 5)**. Hier greifen verbindliche Leitplanken (`EnterpriseGuardrail`), Referenz-Blueprints, Schutzbedarfe und regulatorische Anforderungen (`ComplianceRequirement`, z. B. DORA, DSGVO, NIS-2, EU AI Act) durchgängig vom Geschäftsprozess bis in Systemdesign, Schnittstellenverträge und Plattformkontrollen.
3. **Befähigungs- und Nutzungsachse zwischen Business und System:**  
   - *Value Streams und Business Processes (Tier 2) nutzen Workflows & Orchestration (Tier 3):* Jeder technische Ablauf dient einem fachlichen Geschäftsprozess (`utilizes` / `enables`).
   - *Services & Applications (Tier 3) befähigen Business Capabilities (Tier 2):* Softwarekomponenten befähigen abgegrenzte fachliche Fähigkeiten (`enables`). Während modulare Services direkt einer einzelnen Domäne zugeordnet sind (`owns`), können gekapselte monolithische Systeme (wie z. B. integrierte Standardsoftware) Fähigkeiten mehrerer Domänen befähigen (`enables`), wobei die Eigentümerschaft (`owns`) über Capabilities, Prozesse, Semantik und Datenprodukte strikt in den jeweiligen Fachdomänen verbleibt.
4. **Verankerung System zu Data:**  
   - *Services & Applications (Tier 3) operationalisieren die Datenhoheit ihrer Domäne:* Systeme kapseln ihre internen Datenzugriffe und setzen die fachliche Datenverantwortung (Domain Data Ownership) technisch um.
   - *Domänenübergreifende Interaktion basiert auf Semantics & Ontology sowie Data Contracts (Tier 4):* Schnittstellen und Datenaustausch basieren auf standardisierten Datenverträgen und maschinenlesbaren Schemata.
   - *Services & Applications publizieren und konsumieren Data Products (Tier 4):* Der analytische und operative Mehrwert wird über versionierte, vertraglich zugesicherte Datenprodukte bereitgestellt.

### 5.2 Gateway-Schnittstellen (Übergänge des operativen Kerns)
Die beiden Gateways steuern und schützen die Interaktionsübergänge an den Domänen- und Systemgrenzen und verankern diese im semantischen und vertraglichen Fundament des Data Layers (Tier 4):
- **Experience-Gateway (Kanal- und Nutzerentkopplung):** Entkoppelt menschliche Akteure und Agenten in den Zugangskanälen (Tier 2) von technischen Systemdetails (Tier 3). Interaktionen erfolgen über klar geschnittene Geschäftsfähigkeiten und Data Products auf Basis der jeweiligen Domänensemantik (Tier 4), unabhängig von Endgeräten, UI-Frameworks oder physischen Kanälen.
- **Integration-Gateway (System- und Partnerentkopplung):** Kapselt die maschinelle Interaktion zwischen Systemen, Domänen und Drittanbietern (Tier 3) und bindet den Datenaustausch verbindlich an maschinenlesbare Data Contracts (Tier 4), API-Management und Event-Broker, unabhängig vom technischen Übertragungsprotokoll (REST, Event-Driven, Messaging).

### 5.3 Domänenübergreifende Interaktion und Entkopplungsregeln
Während die Schichten-Interaktionsmatrix (Abschnitt 5.5) die vertikalen Beziehungen zwischen den fünf Tiers regelt, gelten für die horizontale Interaktion über Domänen- und Systemgrenzen hinweg drei verbindliche Entkopplungsregeln:
- **Vertragsgebundene Kommunikation:** Domänenübergreifende Systemaufrufe und Datenflüsse erfolgen ausschließlich über explizite, maschinenlesbare Schnittstellen- und Datenverträge (`DataContract` in Tier 4), die als Anti-Corruption Layer zwischen den jeweiligen Domänenmodellen fungieren.
- **Kapselung der Datenhaltung:** Systeme greifen niemals an der zuständigen Domänenlogik vorbei direkt auf fremde operative Datenbestände zu. Auch bei physisch geteilten Kernsystemen (z. B. ERP-Monolithen) erfolgt der domänenübergreifende Zugriff ausschließlich über logisch gekapselte Schnittstellen oder publizierte Datenprodukte (`DataProduct`).
- **Schutz der Außengrenzen über Gateways:** Kanal-, Agenten- und Partnerzugriffe sowie domänenübergreifende Systemintegrationen werden über die jeweiligen Gateways (`ExperienceGateway` bzw. `IntegrationGateway`) geführt, um Authentifizierung, Schema-Validierung und Ratenbegrenzung durchzusetzen.

### 5.4 Rückkopplungsbeziehungen (Feedback-Schleifen)
Architekturbeziehungen sind keine Einbahnstraße. Aggregierte Informationen, Telemetrie und Evidenzen fließen strukturiert zurück, um operative Ausführung, fachliche Weiterentwicklung und strategisch-regulatorische Steuerung zu speisen:
- **Data Products (Tier 4) steuern Workflows & Orchestration (Tier 3):** Analytische und inferierende Datenprodukte (z. B. Scoring-Modelle, Klassifikatoren) werden von Workflow-Engines konsumiert, um Verzweigungen automatisiert und datenbasiert in Echtzeit zu steuern (*operative Rückkopplung*).
- **Data Products (Tier 4) informieren und optimieren den Business Layer (Tier 2):** Aggregierte Datenprodukte (Reporting-Marts, Nutzungs- und KPI-Analysen) liefern die empirische Basis für Prozessanpassungen, Touchpoint-Optimierungen (Experience) und Capability-Investitionen (*fachlich-analytische Rückkopplung*).
- **Observability & Resilience (Tier 5) optimiert Business Processes und Workflows (Tier 2/3):** Laufzeitmetriken zu Durchlaufzeiten, Fehlerraten und Systemlatenzen decken operative Engpässe auf und treiben die kontinuierliche Fehlerbeseitigung (*diagnostische Rückkopplung*).
- **Data Products (Tier 4) speisen Tier 1 (Guidance) mit verdichteter Steuerungs- und Compliance-Evidenz:** Operative Ergebnisse aus Wertströmen und Systemen (Tier 2/3) sowie Laufzeit-, Sicherheits- und Resilienz-Telemetrie aus der Foundation (Tier 5) werden im Data Layer (Tier 4) mit fachlicher Semantik verknüpft und als qualitätsgesicherte Datenprodukte bereitgestellt. Diese befähigen (`enables`) in Tier 1 die faktenbasierte Strategie- und Portfolio-Steuerung (`Vision & Strategy`), die Überprüfung von Leitplanken (`Policies, Guardrails & Blueprints`) und die kontinuierliche Risiko- und Compliance-Nachweisführung (`Trust, Risk & Compliance`) (*strategische und regulatorische Rückkopplung*).

### 5.5 Schichten-Interaktionsmatrix

Die zulässigen Interaktionsbeziehungen zwischen den fünf Schichten des Referenzmodells werden über eine formale Kantenmatrix gesteuert. Während die Relation `owns` (Abschnitt 2.2) die schichtenübergreifende Eigentumsklammer der Domäne bildet (Abschnitt 5.1), projiziert die Matrix die drei gerichteten Schichtenrelationen (`guides`, `enables`, `utilizes`) auf das Zusammenspiel der Tiers. Jede Zelle bildet die dominierende Primärrelation von der Quellschicht (Zeile) in Richtung der Zielschicht (Spalte) ab; dabei stehen die Nutzungsrichtung von oben nach unten (`utilizes`) und die Befähigungsrichtung von unten nach oben (`enables`) komplementär zueinander. Nicht unmittelbar miteinander interagierende Schichten sind als `n/a` gekennzeichnet:

| Quelle (Zeile) \ Ziel (Spalte) | Tier 1: Guidance | Tier 2: Business | Tier 3: System | Tier 4: Data | Tier 5: Foundation |
|---|---|---|---|---|---|
| **Tier 1: Guidance** | — | guides | guides | guides | guides |
| **Tier 2: Business** | n/a | — | utilizes | utilizes | n/a |
| **Tier 3: System** | n/a | enables | utilizes | utilizes | utilizes |
| **Tier 4: Data** | enables | enables | enables | — | utilizes |
| **Tier 5: Foundation** | n/a | n/a | enables | enables | — |

**Projektion der Metamodell-Kanten auf die Schichten:**
- `guides`: Tier 1 (Guidance) leitet und rahmt die darunterliegenden Schichten über zwei komplementäre Achsen: Strategische Ziele und Organisationsschnitt (`StrategicObjective`, `OrganizationalUnit`) richten primär Tier 2 (Business), Tier 4 (Data Ownership & Semantik) und die Domänen aus, während verbindliche Leitplanken sowie Risiko- und Compliance-Anforderungen (`EnterpriseGuardrail`, `ComplianceRequirement`) durchgängig von den Geschäftsprozessen und kritischen Funktionen (Tier 2) über Systemdesign (Tier 3), Datenverträge und Datenprodukte (Tier 4) sowie Domänen bis in die technischen Kontrollen der Foundation (Tier 5) wirken.
- `enables`: Jede dienende Schicht befähigt die darüberliegenden Ebenen: Plattformfähigkeiten (Tier 5) befähigen Systeme und Daten mit Laufzeit-, Speicher-, Sicherheits- und Telemetrieressourcen; der Data Layer (Tier 4) befähigt Software-Ausführung (Tier 3) und Fachlichkeit (Tier 2) mit verlässlicher Information und Semantik sowie Tier 1 (Guidance) mit aggregierten, semantisch kontextualisierten Steuerungs-, Risiko- und Compliance-Datenprodukten; Applikationen und Workflows (Tier 3) befähigen die Geschäftsprozesse und Business Capabilities (Tier 2).
- `utilizes`: Komplementäre Nutzungsrichtung zu `enables`: Fachprozesse (Tier 2) nutzen Applikationen und Datenprodukte; Applikationen (Tier 3) nutzen andere Applikationen (z. B. Workflows nutzen Services), Datenprodukte und Plattformdienste; Datenprodukte (Tier 4) nutzen physische Persistenz-, Telemetrie- und Kataloginfrastrukturen der Foundation (Tier 5).
