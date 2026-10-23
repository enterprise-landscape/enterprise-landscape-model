# Thematisches Overlay: AI-Readiness von Systemlandschaften

**Typ:** Thematisches Overlay  
**Version:** 0.4  
**Status:** Pilotierung  
**Übergeordnetes Referenzmodell:** [Enterprise Landscape Model (ELM)](../../model/specification.md)  
**Kompatibilität:** Enterprise Landscape Model >= v0.8  
**Autor:** Julia Senner (Enterprise & Solution Architecture)  
**Relevante Materialien:** [ai-readiness-overlay.pptx](assets/ai-readiness-overlay.pptx) (Präsentationsvorlage)  

---

## 1. Zweck, Geltungsbereich und Abgrenzung

### 1.1 Zweck

Dieses Dokument definiert, welche architektonischen Voraussetzungen eine Systemlandschaft erfüllen muss, damit KI-Komponenten und autonome Agenten wirtschaftlich, sicher und ohne wiederkehrende Kernumbauten betrieben werden können.

Es erfüllt drei Funktionen:
1. **Normativ:** Definiert die hersteller- und kundenneutralen Soll-Eigenschaften, die eine Landschaft zwingend aufweisen muss, um als tragfähig für KI zu gelten.
2. **Diagnostisch:** Liefert ein operationalisiertes Prüfraster aus binär prüfbaren Kriterien und geforderten Evidenzen zur objektiven Zustandsbewertung.
3. **Kommunikativ:** Schafft einen einheitlichen Begriffs- und Orientierungsrahmen, um Handlungsbedarfe und Architekturentscheidungen transparent und begründet zu vermitteln.

### 1.2 Geltungsbereich

Dieses Overlay fokussiert auf Systemlandschaften, in die operative KI-Komponenten und autonome Agenten eingebunden werden, um nahtlos mit Geschäftsfähigkeiten, Kernprozessen und Datenbeständen zu interagieren.

- **Primäre Hebelwirkung:** Seine größte diagnostische und steuernde Wirkung entfaltet das Overlay in komplexen und heterogenen Systemlandschaften mit hoher Transaktionsdichte und regulatorischen Anforderungen an Nachvollziehbarkeit und Compliance.
- **Fachliche Abgrenzung:** Der Fokus liegt auf der **architektonischen Tragfähigkeit der Systemlandschaft zur Integration, Orchestrierung und Absicherung von KI**. Nicht Gegenstand dieses Overlays ist das isolierte ML-Engineering (Modelltraining, Feature-Engineering auf Chipebene, Hyperparameter-Optimierung oder GPU-Cluster-Management).

### 1.3 Bewusste Abgrenzungen

- **Keine Produkt- oder Technologiebindung:** Definiert werden herstellerneutrale Soll-Eigenschaften, Schnittstellenmuster und Kontrollmechanismen, unabhängig von konkreten Software-Produkten, Cloud-Providern oder KI-Frameworks.
- **Keine pauschale Reifegradmaximierung:** Ziel ist nicht eine flächendeckende Maximierung, sondern die bedarfsgerechte Auswahl nötiger Maßnahmen entlang des relevanten Einsatzprofils.
- **Keine Kompensation durch Modellqualität:** Mängel in Datenstrukturen, Schnittstellen und Prozesskontrollen lassen sich nicht durch leistungsfähigere KI-Modelle ausgleichen. Die Voraussetzungen müssen in der Systemlandschaft selbst geschaffen werden.

### 1.4 Klassifizierung der Kriterien

Alle Kriterien in diesem Dokument weisen ihre Verbindlichkeit und Verlässlichkeit transparent aus:

| Kennzeichen | Bedeutung | Konsequenz für die Bewertung |
|---|---|---|
| **[E]** | Etablierte Praxis. In Standards (ISO, IEEE, TOGAF), anerkannter Fachliteratur oder Regulatorik (EU AI Act, DORA, DSGVO) verankert. | Verbindlich, darf in der Zielarchitektur nicht unterschritten werden. |
| **[A]** | Abgeleitet. Aus wiederkehrenden Fehlermustern realer Transformationsprojekte gewonnen, nicht als formaler Standard belegt. | Empirisch fundiert, im konkreten Kontext begründbar anpassbar. |
| **[H]** | Hypothese. Plausibel und schlüssig, aber noch nicht empirisch abgesichert. | Diskursiv, darf keine alleinige Basis für verbindliche Entscheidungen bilden. |

### 1.5 Bezug zum Enterprise Landscape Referenzmodell

Dieses Dokument ist ein **thematisches Overlay** über dem [Enterprise Landscape Reference Model](../../model/specification.md). Ein thematisches Overlay führt kein isoliertes Schichtenmodell ein, sondern projiziert eine themenspezifische Fragestellung (hier die dauerhafte, sichere und wirtschaftliche KI-Readiness) transversal über die kanonischen Ebenen der Unternehmenslandschaft:

- **Verankerung in den 5 Tiers:** Jede Anforderung dockt an eine bestehende architektonische Ebene an (Tier 1 bis 5: Guidance, Business Layer, System Layer, Data Layer, Foundation).
- **Nutzung der Gateway-Schnittstellen:** Die Interaktion zwischen Menschen, Partnersystemen und KI-Akteuren wird über die definierten Gateways an den Übergängen des Modells kontrolliert (Experience für Mensch/Agent ↔ Business & Data, Integration für Tools/Systeme ↔ System & Data).
- **Spezialisierung der Guiding Principles:** Übergreifende Gestaltungsrichtlinien (z. B. Data as a Product, Zero Trust, Loose Coupling) werden für die Besonderheiten stochastischer und autonomer Komponenten geschärft.

---

## 2. Qualitative Reifestufen der Systemlandschaft

Der Begriff KI-ready wird in der Praxis häufig unscharf verwendet. Dieses Overlay unterscheidet drei qualitative Zustandsklassen, die grundlegend unterschiedliche architektonische Anspruchsniveaus und Integrationsmuster beschreiben:

| Zustand | Definition | Ausprägung in der Systemlandschaft |
|---|---|---|
| **AI-enabled** | KI wird punktuell für unterstützende Aufgaben eingesetzt, ohne direkte Integration in Kernsysteme oder zentrale Geschäftsprozesse. | Isolierte Insellösungen oder Frontend-Assistenten (z. B. Chatbots, RPA-Skripte) mit manuellen oder Ad-hoc-Datenzugriffen. Kein gemeinsames Fundament. |
| **AI-ready** | KI-Anwendungsfälle können ohne strukturelle Anpassungen der Systemlandschaft in Kernsysteme und Geschäftsprozesse integriert werden. Daten und Schnittstellen sind semantisch beschrieben und verfügbar, Prozesse sind explizit modelliert, Aufrufe sind überwachbar und regulatorisch eingeordnet. | Strukturierte APIs und maschinenlesbare Datenverträge verbinden KI-Dienste stabil mit Kernsystemen. Laufzeitverhalten, Drift und Kosten werden kontinuierlich überwacht. |
| **AI-native** | KI-Komponenten und Agenten sind eigenständige Systemakteure mit eigenen Service-Identitäten, Berechtigungen und Rückfallebenen. Prozesse sind so aufgebaut, dass Aufgaben nahtlos zwischen Mensch und Agent übergeben und gleichermaßen ausgeführt werden können. | Agenten sind im IAM mit eigenen Service-Identitäten hinterlegt, im Prozessmodell als eigenständige Akteure geführt und in einer zentralen Tool-Registry deklariert. |

### 2.1 Operationalisierung der Grenze von AI-enabled zu AI-ready

Ob für die Integration von KI strukturelle Anpassungen der Systemlandschaft erforderlich sind, lässt sich nur anhand konkreter Anwendungsfälle objektiv beurteilen. Das Prüfverfahren umfasst drei Schritte:

1. **Referenzfall auswählen:** Einen fachlich relevanten und realistischen Anwendungsfall der Organisation bestimmen.
2. **Bedarfskette analysieren:** Alle benötigten Datenobjekte, Zugriffswege, semantischen Kontrakte, Prozessübergaben, Entscheidungsregeln, Telemetriepfade, Audit-Trails und Rückfallebenen isolieren.
3. **Bedarfe klassifizieren:** Jeden identifizierten Teilbedarf einer von vier Klassen zuordnen:
   - **Vorhanden:** Funktional und technisch verfügbar.
   - **Konfigurierbar:** Über bestehende Parameter oder Werkzeuge ohne Code-Änderung aktivierbar.
   - **Entwicklungsaufwand:** Normale Feature-Entwicklung im bestehenden Architekturrahmen.
   - **Strukturelle Anpassung:** Durchbrechen von Schichtengrenzen, Neuschneiden von Schnittstellen, fehlende Entkopplung, neue Governance oder ungelöste Datenhoheit.

> **Entscheidungskriterium:** Führt die Analyse mindestens einen Teilbedarf als **strukturelle Anpassung** auf, ist die Systemlandschaft für diesen Anwendungsfall nicht AI-ready.

### 2.2 Operationalisierung der Grenze von AI-ready zu AI-native

Während AI-ready die stabile Integration von KI-Funktionen ohne strukturelle Anpassungen beschreibt, markiert AI-native den Übergang zu eigenständigen Systemakteuren im regulären Prozessbetrieb. Dieser Zustand erfordert drei zwingende architektonische Eigenschaften:

1. **Autonome Identität und Least Privilege:** KI-Agenten agieren nicht unter generischen Dienstkonten, sondern verfügen über eigenständige, nachvollziehbare Service-Identitäten mit feingranular beschränkten Berechtigungen.
2. **Duale Kontrollschranken:** Probabilistische Modellentscheidungen sind im primären Ausführungspfad durch deterministische Regelwerke oder Freigabeschranken gekapselt. Autonome Zustandsänderungen an Kern- und Transaktionssystemen ohne deterministische Invariantenprüfung sind strikt unzulässig.
3. **Adaptive Prozessführung und Zustandssicherheit:** Prozesse sind für die nicht-deterministische Ausführung ausgelegt und persistieren ihren Zustand auditfest, um Unterbrechungen, Planungszyklen und dynamische Fehlerkompensationen abzufangen.

> **Entscheidungskriterium:** Eine Systemlandschaft ist erst dann AI-native, wenn alle drei Bedingungen kumulativ erfüllt sind: Autonome Agenten agieren unter eigenständigen Service-Identitäten, deterministische Kontrollschranken fangen fehlerhafte Modellentscheidungen vor der Zustandstransformation ab, und Kernprozesse sind zustandssicher für nicht-deterministische Ausführungszyklen und Kompensationen ausgelegt.

### 2.3 Projektion der Zustandsklassen auf die operativen Einsatzprofile

Die drei qualitativen Zustandsklassen beschreiben den makro-architektonischen Reifegrad der Systemlandschaft als Ganzes. Für konkrete Transformationsvorhaben und Reviews übersetzen die vier Einsatzprofile (Profil A bis D in Abschnitt 6.3) diesen Zustand in messbare Soll-Niveaus:

- **AI-enabled entspricht Profil A (Explorativ):** Punkthafte Assistenzfunktionen ohne direkten Eingriff in Kernprozesse genügen bereits mit basalen Anforderungen (Level 1 bis 2).
- **AI-ready umfasst Profil B (Operativ) und Profil C (Skalierend):** Für einen einzelnen, geführten Freigabeprozess genügt AI-Readiness im fokussierten Pfad (Profil B). Sobald KI-Vorhaben jedoch portfolio-weit skalieren und Hochrisikoprozesse berühren (Profil C), müssen alle sechs Dimensionen durchgängig auf mindestens Level 3 gehärtet sein.
- **AI-native entspricht Profil D (Autonom):** Der Einsatz autonomer Agenten als eigenständige Systemakteure erfordert das Spitzenlevel (Level 4) in den Integrations-, Prozess- und Kontrollschichten.

---

## 3. Definition der Prüfdimensionen

Das Overlay hebt diejenigen Segmente und Eigenschaften einer Systemlandschaft hervor, die für die kontrollierte Integration von KI-Komponenten und autonomen Agenten entscheidend sind. Um diese Anforderungen strukturiert zu bewerten, gliedert das Modell die Landschaft in sechs Prüfdimensionen (D1 bis D6):

| Dimension | Fokus | Kernanforderung |
|---|---|---|
| **D1: Handlungsraum** | Fachliche Domänen und Capabilities | Eindeutig abgegrenzte Business Capabilities und Domänen mit dokumentierter fachlicher Ownership. |
| **D2: Wissensbasis** | Daten und Semantik | Formalisierte Semantik, maschinenlesbare Data Contracts und kuratierte Datenprodukte. |
| **D3: Werkzeuge** | Ausführbare Services und Tools | Idempotente, maschinenlesbare Schnittstellenverträge mit strikter Rechtebegrenzung. |
| **D4: Prozessführung** | Abläufe und Kontrollschranken | Deterministische Kapselung probabilistischer Schritte und Absicherung kritischer Zustandsänderungen. |
| **D5: Telemetrie** | Laufzeitüberwachung und Ausfallschutz | Kontinuierliche Überwachung von Inferenz, Drift und Kosten sowie erprobte Notabschaltungen. |
| **D6: Leitplanken** | Regulatorik und Souveränität | Lückenlose Audit-Trails für Modellentscheidungen, regulatorische Konformität und Schutz vor Plattformabhängigkeiten. |

---

## 4. Projektion auf das Referenzmodell

Das Overlay verankert die Anforderungen für KI direkt in den fünf Tiers, den Gateways und den Leitprinzipien des Enterprise Landscape Referenzmodells:

### 4.1 Schichten-Projektion

| Tier im Referenzmodell | KI-spezifische Soll-Eigenschaften und Bausteine | Prüfdimension |
|---|---|---|
| **Tier 1: Guidance** | Zentrales Use-Case- und Modellregister, Risikoklassifizierung nach EU AI Act, Zweckbindung by Design, manipulationssicherer Audit-Trail für Entscheidungen, definierte Rollen für menschliche Aufsicht. | **D6: Leitplanken** |
| **Tier 2: Business Layer** | Business Capabilities als Träger von KI-Potenzial, langlebiger Domänenschnitt vor Automatisierung, explizite Übergabepunkte für menschliche Aufsicht, Gateway Experience als adaptives Mensch-Maschine-Interface mit Konfidenzanzeige. | **D1: Handlungsraum**<br>**D4: Prozessführung** |
| **Tier 3: System Layer** | Workflow-Engine zur Kapselung probabilistischer Inferenz, deterministische Rule- und Decision-Services, maschinenlesbare Schnittstellenverträge, Tool-Registry mit Rechtebegrenzung, Gateway Integration mit Event-Backbone, Idempotenz und Rate Limiting. | **D3: Werkzeuge**<br>**D4: Prozessführung** |
| **Tier 4: Data Layer** | Domänenverantwortung für Daten und Semantik je Bounded Context, maschinenlesbare Ontologien, Schemata und Data Contracts, kuratierte operative und analytische Datenprodukte, Feature Stores und Vektorindizes. | **D2: Wissensbasis** |
| **Tier 5: Foundation** | KI-spezifische Telemetrie für Token, Kosten und Latenzen, Ende-zu-Ende-Tracing über Agentenaufrufe, Disaster Recovery für Datenströme, Notabschaltungen und definierte Degradationsmodi, Zero-Trust-Architektur und Service-Identitäten mit Least-Privilege-Berechtigungen. | **D5: Telemetrie** |

### 4.2 Architektonische Invarianten der Schichten-Integration

Eine tragfähige Integration von KI entscheidet sich an den Übergängen zwischen den Schichten. Für das Zusammenspiel der Tiers gelten vier verbindliche Invarianten:

1. **Duale Ausführungsgrenze (Tier 2 und Tier 3):**
   - **Invariante:** Probabilistische Agenten liefern ausschließlich strukturierte Handlungsvorschläge. Zustandsänderungen an Kernsystemen werden zwingend durch deterministische Workflow-Engines und Regelwerke validiert und persistiert.
   - **Anti-Pattern:** Ein Modell oder Agent führt autonome Schreiboperationen per API oder Datenbankverbindung direkt im Kernsystem aus.

2. **Semantische Kapselung (Tier 3 und Tier 4):**
   - **Invariante:** Agenten und KI-Services greifen auf Daten und Wissen ausschließlich über kuratierte Datenprodukte und maschinenlesbare Schnittstellenverträge der zuständigen Domäne zu.
   - **Anti-Pattern:** RAG-Pipelines oder Agenten umgehen die Domänenlogik und binden rohe Datenbank-Replikate oder unstrukturierte Dateispeicher direkt an.

3. **Resilienz durch Gateway-Schutz (Tier 3 Gateway):**
   - **Invariante:** Jeder Werkzeugaufruf eines Agenten passiert das Integration Gateway mit Least-Privilege-Autorisierung, Ratenbegrenzung und Idempotenz-Tokens.
   - **Anti-Pattern:** Unkontrollierte Agentenschleifen oder parallele Tool-Aufrufe fluten ungeschützte interne Schnittstellen und führen zur Blockade operativer Systeme.

4. **Geschlossene Kontroll- und Feedbackschleifen (Tier 5 an Tier 3 und Tier 2 an Tier 4):**
   - **Invariante:** Plattform-Telemetrie kann fehlerhafte Inferenzpfade deterministisch unterbrechen (Schutzschalter und Notbetrieb), während Anwenderkorrekturen geordnet zur Qualitätsverbesserung in Domänendatenprodukte zurückfließen.
   - **Anti-Pattern:** Ein fehlerhaft agierender Agent läuft ohne Notabschaltung im Produktivbetrieb weiter, während Fehlerkorrekturen von Nutzern ungenutzt verpuffen.

### 4.3 Leitprinzipien bei architektonischen Zielkonflikten

Architekturprinzipien entfalten ihren Nutzen dort, wo im Projektverlauf zwei legitime Ziele kollidieren. Wenn Teams zwischen schneller Umsetzung, Modellfähigkeiten und Systemstabilität abwägen, gelten drei nicht verhandelbare Heuristiken:

1. **Schnittstellendisziplin vor Modellkompensation:**  
   Architektur- und Semantikmängel in den Datenbeständen dürfen niemals durch größere Modelle oder aufwendiges Prompt-Engineering kompensiert werden. Die Investition in maschinenlesbare Schnittstellenverträge, strukturierte Datenprodukte und explizite Schemata hat immer Vorrang vor dem Wechsel auf leistungsfähigere Inferenzmodelle.

2. **Domänenverantwortung vor Plattformzentralismus:**  
   Die zentrale Plattform stellt Werkzeuge, Basisinfrastruktur und Sicherheitsleitplanken als Service bereit. Die fachliche Verantwortung, das Feintuning von Modellen, die Qualität der Datenprodukte und die Freigabe von Prozessschritten verbleiben ausnahmslos in den zuständigen Fachdomänen.

3. **Deterministische Resilienz vor maximaler Autonomie:**  
   Im Zweifel entscheidet das Gesamtsystem für den kontrollierten Abbruch, die Aktivierung von Schutzschaltern oder die Übergabe an menschliche Sachbearbeiter. Der Schutz von Kernsystemen und die Datenintegrität haben strikten Vorrang vor einer unterbrechungsfreien End-to-End-Automatisierung.

---

## 5. Kriterienkatalog der Prüfdimensionen

Der Kriterienkatalog operationalisiert die sechs Dimensionen für die architektonische Bewertung. Jede Dimension folgt einem einheitlichen Aufbau aus Mindestanforderungen je Baustein, binär prüfbaren Reifegradstufen (Level 0 bis 4) und konkreten Evidenznachweisen für Reviews:

---

### D1: Handlungsraum (Fachliche Domänen und Capabilities)

**Architektonische Relevanz:** KI operiert auf fachlichen Fähigkeiten, nicht auf Organigrammen oder Bestandssystemen. Ohne klar abgegrenzte Bounded Contexts und verantwortete Business Capabilities fehlt probabilistischen Komponenten der verlässliche Handlungs- und Entscheidungsraum.

**Verankerung im Referenzmodell:** Tier 2 (Business Layer), Tier 4 (Data Layer)  
**Geltungseinschränkung [A]:** Diese Dimension ist keine zwingende Voraussetzung für einen einzelnen, isolierten KI-Anwendungsfall. Sie ist jedoch zwingende Voraussetzung für Priorisierung, Entkopplung und Kollisionsfreiheit bei mehreren parallelen Anwendungsfällen. Das geforderte Zielniveau skaliert mit der Portfoliogröße.

#### Bausteine und Mindestanforderungen

| Baustein | Mindestanforderung für AI-Readiness | Klassifizierung |
|---|---|---|
| Business Capability Map | Liegt als eigenständiges, gepflegtes Artefakt über mindestens zwei Ebenen vor, technologie- und organisationsneutral formuliert. | [E] |
| Domänenschnitt | Domänen sind aus Capabilities abgeleitet, Grenzen sind dokumentiert und Änderungen nachvollziehbar. | [A] |
| Systemzuordnung | Jede Capability ist mindestens einem System oder Service zugeordnet, Mehrfach- und Lückenzuordnungen sind transparent. | [E] |
| Ownership | Fachliche Verantwortlichkeiten für Prozesse, Daten und Schnittstellen sind eindeutig geregelt und entscheidungsfähig hinterlegt. | [E] |
| Prozessmodell | Kernprozesse sind Ende-zu-Ende dokumentiert, Entscheidungspunkte, Systemübergaben und Prozessvarianten sind explizit ausgewiesen. | [E] |
| KI-Potenzial-Bewertung | Potenziale sind je Capability systematisch bewertet (Anhang A), sodass die Roadmap begründet statt opportunistisch priorisiert wird. | [A] |

#### Architektonische Reife

| Stufe | Prüfkriterium | Indikator |
|---|---|---|
| **Level 0** | Keine Capability-Sicht vorhanden. | Fachliche Strukturen werden primär entlang des Organigramms, von Bestandssystemen oder gelebten Prozessen gegliedert. |
| **Level 1** | Eigenständige Business Capability Map vorhanden. | Geschäftsfähigkeiten sind organisations- und technologieneutral in einem eigenständigen Modell hinreichend detailliert beschrieben. |
| **Level 2** | Capabilities sind Domänen und Systemen zugeordnet. | Jede relevante Capability ist einem Bounded Context und führenden Systemen zugeordnet. Mehrfach- und Lückenzuordnungen sind transparent. |
| **Level 3** | Fachliche Ownership geregelt und Map aktiv gepflegt. | Fachliche Verantwortlichkeiten über Scope und Schnittstellen sind dokumentiert. Änderungen an Capabilities folgen einem geregelten Pflegeprozess. |
| **Level 4** | Capability Map steuert Investitionen und KI-Potenziale. | Die Capability Map dient als aktives Steuerungsinstrument für Portfolio- und Architekturentscheidungen. KI-Roadmaps basieren auf systematischen Potenzialbewertungen je Capability. |

#### Prüffragen und Evidenzen

| Prüffrage im Review | Geforderte Evidenz | Stufe |
|---|---|---|
| Existiert eine formal gepflegte Business Capability Map unabhängig von reinen Strategieunterlagen? | Gepflegtes Modell im EAM-Tool oder Architektur-Repository, dokumentierter Versionsstand und geregelter Pflegeprozess. | **Level 1** |
| Sind Bounded Contexts und Domänengrenzen nachvollziehbar aus den Geschäftsfähigkeiten abgeleitet? | Dokumentierte Domänenarchitektur, Metamodell-Verknüpfung zwischen Capabilities und Domänen. | **Level 2** |
| Ist transparent dokumentiert, welche Kernsysteme und Services die jeweiligen Capabilities unterstützen? | Capability-zu-System-Matrix im EAM-Tool oder Bebauungsplan, zugeordnete Kernprozesse mit Systemgrenzen. | **Level 2** |
| Sind für alle betroffenen Domänen fachliche Verantwortliche mit dokumentierter Entscheidungsbefugnis hinterlegt? | Rollenmodell, RACI-Matrix, dokumentierte Freigabeprozesse der Architektur-Governance. | **Level 3** |
| Werden Investitionen und KI-Roadmaps nachweisbar über methodische Potenzialbewertungen der Capabilities gesteuert? | Bewertete Capability Map (Heatmap oder Potenzial-Assessment), dokumentierte Architekturbeschlüsse (ADRs). | **Level 4** |
| Wie viele KI-Vorhaben sind portfolioübergreifend geplant und wie hoch ist der Überschneidungsgrad? | Use-Case-Portfolio zur Kalibrierung des benötigten Zielniveaus (Einzel-Use-Case vs. paralleles Portfolio). | **Kontext** |

---

### D2: Wissensbasis (Daten und Semantik)

**Architektonische Relevanz:** Modellintelligenz ist zukaufbar, organisationsspezifische Datensemantik nicht. Ohne formalisierte Semantik und verlässliche Datenprodukte führen probabilistische Modelle zu Halluzinationen, Datenlecks und Prozessbrüchen.

**Verankerung im Referenzmodell:** Tier 4 (Data Layer: Semantics & Ontology, Data Contracts, Data Products)  

#### Bausteine und Mindestanforderungen

| Baustein | Mindestanforderung für AI-Readiness | Klassifizierung |
|---|---|---|
| Datendomänenmodell | Geschäftsobjekte sind eindeutig Domänen zugeordnet. Für jedes Objekt ist genau ein führendes Quellsystem (Single Source of Truth) verbindlich definiert, abgeleitete Sekundärspeicher werden synchronisiert. | [E] |
| Semantikschicht | Fachbegriffe und Geschäftskonzepte sind definiert, versioniert und maschinenlesbar mit Datenfeldern und Schnittstellen verknüpft (Ubiquitous Language). | [E] |
| Unstrukturierte Daten | Textdokumente, Verträge und Multimediabestände sind versioniert, mit Quellmetadaten angereichert und unter Beibehaltung der Zugriffsbeschränkungen maschinell abrufbar (z. B. für RAG). | [A] |
| Datenprodukte | Operative und analytische Datenbestände werden als eigenständige Produkte mit maschinenlesbaren Schnittstellenverträgen (Data Contracts mit Schema und SLAs) bereitgestellt. | [A] |
| Datenkatalog | Datenquellen, Schemata und Herkunft (Lineage) sind zentral dokumentiert, durchsuchbar und für autorisierte Komponenten maschinell auffindbar. | [E] |
| Datenqualität | Verbindliche Qualitätskriterien (Vollständigkeit, semantische Konsistenz, Aktualität, Genauigkeit) sind formal definiert und werden automatisiert an Schwellwerten überwacht. | [E] |
| Datenklassifizierung | Jedes Datenobjekt trägt Schutzbedarf, Vertraulichkeitsstufe und zulässige Nutzungszwecke als maschinenlesbares Attribut zur Durchsetzung der Zweckbindung. | [E] |
| Auditierbarkeit | Zustandsänderungen und Kontextdaten sind unveränderlich gespeichert und abfragbar, um historische Datenkontexte für Prüfungen und Rekonstruktionen bereitzustellen. | [E] |

#### Architektonische Reife

| Stufe | Prüfkriterium | Indikator |
|---|---|---|
| **Level 0** | Keine domänenübergreifende Datensicht vorhanden. | Daten liegen isoliert in System-Silos. Datenmodelle sind proprietär und ihre Semantik ist nicht formal dokumentiert. |
| **Level 1** | Datendomänenmodell und führende Systeme dokumentiert. | Kanonische Geschäftsobjekte sind Domänen zugeordnet. Das führende System (Source of Truth) ist für Kernobjekte verbindlich benannt. |
| **Level 2** | Datenkatalog und Datenklassifizierung etabliert. | Schemata, Metadaten und Schutzklassen sind in einem zentralen Katalog auffindbar. Unstrukturierte Dokumente für den KI-Einsatz sind formal erfasst und rechtegeprüft. |
| **Level 3** | Automatisierte Datenqualitätsmessung und API-Zugriff aktiv. | Definierte Qualitätskriterien werden automatisiert an Schwellwerten überwacht. KI-Komponenten beziehen Daten über dokumentierte Schnittstellen statt direkter Datenbankabfragen. |
| **Level 4** | Formalisierte Datenprodukte mit Data Contracts operativ. | Datenprodukte werden über versionierte Data Contracts mit definierten Schemata und SLAs bereitgestellt. Zweckbindung und Zugriffskontrolle sind technisch am Datenobjekt durchgesetzt. |

#### Prüffragen und Evidenzen

| Prüffrage im Review | Geforderte Evidenz | Stufe |
|---|---|---|
| Ist für alle geschäftskritischen Datenobjekte das führende Quellsystem verbindlich dokumentiert? | Datendomänenmodell, Verzeichnis führender Systeme (Single Source of Truth). | **Level 1** |
| Sind Datenquellen, Schemata und deren Schutzklassen in einem maschinenlesbaren Katalog erfasst? | Datenkatalog, Metadaten-Repository, Klassifizierungsrichtlinie. | **Level 2** |
| Wie wird sichergestellt, dass Zugriffsbeschränkungen von Dokumenten auch in KI-Suchindizes (RAG) wirksam bleiben? | ACL-Synchronisationskonzept, Sicherheitsarchitektur der Indexierungspipelines. | **Level 2** |
| Werden Datenqualität und Aktualität für KI-relevante Bestände automatisiert und zeitnah überwacht? | Monitoring-Dashboards für Datenqualität, automatisierte Pipeline-Prüfungen. | **Level 3** |
| Erfolgt der Datenzugriff von KI-Komponenten strikt über entkoppelte Schnittstellen statt direkter Datenbankzugriffe? | API-Spezifikationen, Zugriffsarchitektur, Netzwerk- und IAM-Richtlinien. | **Level 3** |
| Werden Daten als Produkte über versionierte Data Contracts mit definierten Schemata und SLAs bereitgestellt? | Formalisierte Data Contracts (z. B. JSON-Schema, Protobuf, OpenAPI), SLA-Definitionen. | **Level 4** |
| Wie wird verhindert, dass veraltete oder abgeleitete Vektordatenbestände zu Falschinformationen führen? | Re-Indexierungs- und Invalidierungsstrategie für abgeleitete Datenprodukte. | **Kontext** |

---

### D3: Werkzeuge (Funktionen und Tools)

**Architektonische Relevanz:** Autonome Agenten agieren über Werkzeuge. Die Reife, Entkopplung und Idempotenz der Integrationsschicht bestimmt den realisierbaren Automatisierungsgrad und schützt operative Kernsysteme vor unkontrollierten Zugriffen.

**Verankerung im Referenzmodell:** Tier 3 (System Layer: Services & Applications, Integration Gateway)  

#### Bausteine und Mindestanforderungen

| Baustein | Mindestanforderung für AI-Readiness | Klassifizierung |
|---|---|---|
| UI-Entkopplung | Geschäfts- und Prozesslogik ist vollständig unabhängig von grafischen Oberflächen über Schnittstellen aufrufbar. | [E] |
| Schnittstellenvertrag | Jede Fähigkeit verfügt über eine versionierte Spezifikation (OpenAPI, AsyncAPI), die vor der Implementierung definiert und maschinell validiert wird. | [E] |
| Tool-Semantik | Schnittstellenspezifikationen enthalten maschinenlesbare fachliche Semantik wie Vorbedingungen, Seiteneffekte, Fehlermuster und Idempotenz. | [A] |
| Idempotenz | Wiederholte Aufrufe schreibender Operationen sind seiteneffektfrei, mehrstufige Abläufe bieten definierte Kompensationsmechanismen. | [E] |
| Legacy-Kapselung | Altsysteme sind hinter wohldefinierten Fassaden und Anti-Corruption Layern gekapselt, direkter Datenbankzugriff durch KI ist ausgeschlossen. | [E] |
| Event-Backbone | Fachliche Ereignisse werden über eine entkoppelte Plattform mit stabilen Schemata und dokumentierten Verträgen asynchron verteilt. | [E] |
| API-Governance | Architekturrichtlinien werden automatisiert erzwungen, insbesondere durch Pipeline-Linter und Policy Enforcement am API-Gateway. | [E] |
| Service-Identität | Technische Identitäten für nicht-menschliche Aufrufer agieren mit minimalem Berechtigungsumfang (Least Privilege), auditierbar und getrennt von Endnutzerkonten. | [E] |
| Tool-Registry | Ein maschinenlesbarer Fähigkeitskatalog stellt Werkzeuge samt Semantik und Berechtigungen für deklarative Agentenaufrufe dynamisch bereit. | [A] |

#### Architektonische Reife

| Stufe | Prüfkriterium | Indikator |
|---|---|---|
| **Level 0** | Punkt-zu-Punkt-Kopplung dominiert. | Daten- und Funktionszugriffe erfolgen direkt über Datenbanken oder Oberflächenautomation. |
| **Level 1** | Dokumentierte APIs für Kernanwendungsfälle vorhanden. | Zentrale Funktionen sind über HTTP- oder RPC-Schnittstellen ansprechbar und syntaktisch dokumentiert. |
| **Level 2** | Einheitliche Schnittstellenrichtlinien und Schemastandards verabschiedet. | Integrationsstandards und API-Guidelines liegen als verabschiedetes Architekturartefakt vor und werden in manuellen Reviews geprüft. |
| **Level 3** | Automatisierte Governance und standardisierte Schnittstellenverträge operativ. | Schnittstellenrichtlinien werden über Pipeline-Linter und Gateway-Policies automatisiert erzwungen. Legacy-Systeme sind über Fassaden gekapselt und asynchrone Ereignisse folgen stabilen Schemata. |
| **Level 4** | Dynamische Tool-Registry mit Semantik und Service-Identitäten produktiv. | Schnittstellen stellen maschinenlesbare Semantik bereit. Autonome Komponenten binden Werkzeuge über eine deklarative Tool-Registry mit minimalen Service-Rechten dynamisch zur Laufzeit an. |

#### Prüffragen und Evidenzen

| Prüffrage im Review | Geforderte Evidenz | Stufe |
|---|---|---|
| Sind Kernfunktionen unabhängig von Benutzeroberflächen über dokumentierte Schnittstellen erreichbar? | API-Inventar, Architekturübersicht zur UI-Entkopplung. | **Level 1** |
| Existieren verbindliche Richtlinien für Schnittstellendesign, Schemata und Fehlermuster? | API-Guidelines, Architekturstandards für synchrone und asynchrone Kommunikation. | **Level 2** |
| Werden Schnittstellenrichtlinien und Schemakontrakte automatisiert in CI/CD-Pipelines oder am API-Gateway erzwungen? | CI/CD-Linter-Konfigurationen, Gateway-Policies, automatisierte Schema-Validierung. | **Level 3** |
| Sind Altsysteme hinter stabilen Fassaden gekapselt, um direkte Datenbankzugriffe durch KI-Komponenten auszuschließen? | Integrationsarchitektur, Spezifikationen von Facaden und Anti-Corruption Layern. | **Level 3** |
| Besitzen schreibende Operationen definierte Idempotenz-Mechanismen für sichere Wiederholungen bei Verbindungsabbrüchen? | API-Spezifikationen mit Idempotency-Keys, Dokumentation von Kompensationslogiken. | **Level 3** |
| Agieren automatisierte Aufrufer unter dedizierten technischen Identitäten mit minimalem Berechtigungsumfang? | IAM-Konfiguration, Service-Principal-Richtlinien, Token-Scopes. | **Level 4** |
| Steht ein maschinenlesbarer Katalog bereit, über den Agenten Werkzeuge samt Semantik und Vorbedingungen dynamisch abrufen können? | Tool-Registry, MCP-Server-Konfiguration, OpenAPI-Semantik-Metadaten. | **Level 4** |
| Wie hoch ist der Anteil proprietärer Protokolle in der Integrationslandschaft? | Schnittstellen-Portfolio zur Bestimmung des Kapselungsaufwands. | **Kontext** |

---

### D4: Prozessführung (Abläufe und Kontrollschranken)

**Architektonische Relevanz:** Probabilistische Inferenz darf niemals unkontrollierte Zustandsänderungen an Kern- und Transaktionssystemen auslösen. Deterministische Workflow-Engines und Kontrollschranken kapseln nicht-deterministische Modellvorschläge und sichern die Prozessintegrität durch definierte Übergabepunkte an den Menschen.

**Verankerung im Referenzmodell:** Tier 3 (System Layer: Workflows & Orchestration) und Tier 2 (Business Layer: Business Processes)  

#### Bausteine und Mindestanforderungen

| Baustein | Mindestanforderung für AI-Readiness | Klassifizierung |
|---|---|---|
| Workflow-Engine | Kernprozesse sind explizit in einer Workflow-Engine modelliert und zur Laufzeit inspizierbar, Prozesslogik liegt nicht implizit im Anwendungscode. | [E] |
| Prozessentkopplung | Eine verbindliche Architekturregel trennt Prozesssteuerung, Service-Logik und Integrationsrouting strukturell voneinander. | [A] |
| Zustandssicherheit | Prozesse sind nach Systemunterbrechungen an definierten Meilensteinen zustandssicher fortsetzbar und nutzen persistente Kompensationsmechanismen. | [E] |
| Entscheidungsservice | Fachliche Regeln liegen in konfigurierbaren Entscheidungsservices (DMN, Rule Engines), versioniert und testbar getrennt von Programmcode. | [E] |
| Duale Kontrollschranke | Probabilistische Inferenzschritte erzeugen strukturierte Handlungsvorschläge, deterministische Workflow- oder Regel-Engines validieren Invarianten und Vorbedingungen vor der finalen Zustandstransformation. | [E] |
| Menschliche Aufsicht | Übergabepunkte an Menschen sind im Prozessmodell explizit definiert mit Trigger, Kontextbereitstellung, Handlungsspielraum und Eskalationspfaden. | [A] |
| Manueller Notbetrieb | Für jeden automatisierten Kernprozess existiert ein dokumentierter und erprobter manueller Ablauf bei Ausfall der KI-Komponenten. | [E] |
| Autonomiestufe | Der Handlungsspielraum jeder KI-Fähigkeit ist je Anwendungsfall verbindlich eingestuft (vorschlagend, ausführend mit Freigabe, autonom mit Stichprobe). | [E] |
| Agentengovernance | Autonome Agenten agieren als benannte Architekturakteure mit deklarierter Tool-Registry, festem Berechtigungskontext und harten Delegationsgrenzen. | [A] |

#### Architektonische Reife

| Stufe | Prüfkriterium | Indikator |
|---|---|---|
| **Level 0** | Prozessabläufe sind implizit in Systemen oder Skripten verteilt. | Vorgänge werden durch manuelle Einzelschritte, verteilte Skripte oder Punkt-zu-Punkt-Aufrufe gesteuert. |
| **Level 1** | Workflow-Engine für einzelne Kernprozesse produktiv im Einsatz. | Mindestens ein zentraler Geschäftsprozess wird durch eine Workflow-Engine gesteuert und ist zur Laufzeit technisch inspizierbar. |
| **Level 2** | Standardisierte Workflow-Plattform und modellierte Prozesslandschaft etabliert. | Eine zentrale Workflow-Engine ist als Standardplattform für Kernprozesse verankert. Prozessmodelle definieren synchrone und asynchrone Meilensteine. |
| **Level 3** | Duale Kontrollschranke, Entscheidungsservices und Übergabepunkte operativ. | Probabilistische Inferenz ist über duale Kontrollschranken gekapselt. Fachregeln sind als versionierte Entscheidungsservices ausgelagert, Übergabepunkte an Menschen sind formal modelliert und Notbetriebspläne liegen vor. |
| **Level 4** | Autonome Agenten mit formaler Governance und adaptiver Steuerung integriert. | Autonome Agenten agieren mit deklarierter Autonomiestufe als reguläre Prozessteilnehmer. Eskalationspfade, Delegationsgrenzen und Wirkungsmessungen sind im laufenden Betrieb automatisiert verankert. |

#### Prüffragen und Evidenzen

| Prüffrage im Review | Geforderte Evidenz | Stufe |
|---|---|---|
| Sind Kernprozesse in einer zentralen Workflow-Engine modelliert und zur Laufzeit technisch inspizierbar? | BPMN-Modelle in der Workflow-Engine, Prozessinstanz-Logs. | **Level 1** |
| Existiert eine verbindliche Architekturregel zur sauberen Trennung von Prozesssteuerung, Geschäftslogik und Integrationsrouting? | Architekturrichtlinie zur Prozessentkopplung, Service-Design-Standards. | **Level 2** |
| Sind Prozesse bei Systemunterbrechungen an definierten Meilensteinen zustandssicher fortsetzbar? | Persistenz- und Saga-Konzepte, Konfiguration der Workflow-Transaktionsgrenzen. | **Level 2** |
| Werden fachliche Regeln über versionierte Entscheidungsservices statt fest im Anwendungscode gepflegt? | DMN-Entscheidungsmodelle, Regelwerksinventar, Testsuiten für Fachregeln. | **Level 3** |
| Werden Zustandsänderungen von Kernsystemen durch deterministische Workflow-Engines oder Gateways validiert, bevor probabilistische Inferenz wirksam wird? | Architekturkonzept der Dualen Kontrollschranke, Validierungsgates am API-Gateway. | **Level 3** |
| Sind Übergabepunkte an menschliche Sachbearbeiter mit Kontext, Handlungsspielraum und Fristen im Prozessmodell explizit hinterlegt? | BPMN-Modelle mit User Tasks, Spezifikation der Freigabe- und Eskalationsschritte. | **Level 3** |
| Liegt für jeden automatisierten Kernprozess ein dokumentierter und erprobter manueller Ablauf bei Ausfall der KI-Komponenten vor? | Notfallbetriebshandbuch, BCM-Testprotokolle für Prozessrückfallebenen. | **Level 3** |
| Sind autonome Agenten mit deklarierter Autonomiestufe, Berechtigungsrahmen und Delegationsgrenzen in die Workflow-Engine eingebettet? | Agenten-Spezifikationen, Tool-Berechtigungskonzepte, Audit-Logs der Agentenaktionen. | **Level 4** |
| Welcher Anteil der Prozessinstanzen erfordert aktuell manuelle Nachbearbeitung oder Klärfälle? | Prozess-Telemetrie und Clearing-Statistiken zur Bestimmung des Automatisierungspotenzials. | **Kontext** |

---

### D5: Telemetrie (Laufzeitüberwachung und Ausfallschutz)

**Architektonische Relevanz:** Nicht-deterministische Komponenten ohne kontinuierliche Messung sind im Unternehmenseinsatz nicht beherrschbar. Klassisches Infrastruktur-Monitoring reicht nicht aus, denn stochastisches Modellverhalten, fachliche Prozesswirkung und Notabschaltungen müssen zur Laufzeit lückenlos beobachtbar sein.

**Verankerung im Referenzmodell:** Tier 5 (Foundation: Observability & Resilience)  

#### Bausteine und Mindestanforderungen

| Baustein | Mindestanforderung für AI-Readiness | Klassifizierung |
|---|---|---|
| System-Monitoring | Latenz, Fehlerraten, Durchsatz und Verfügbarkeit werden je Service, Modell-Endpunkt und Integrationsstrecke kontinuierlich gemessen. | [E] |
| Prozess-Monitoring | Durchlaufzeiten, Abbruchquoten, Eskalationsraten und Dunkelverarbeitungsquoten werden je Geschäftsprozess in Echtzeit aggregiert. | [E] |
| Distributed Tracing | Kontextbezogene Traces korrelieren Vorgänge über Systemgrenzen, asynchrone Ereignisse und Agenten- oder Modellaufrufe hinweg (OpenTelemetry). | [E] |
| KI-Telemetrie | Modell- und Promptversionen, Tokenverbrauch, Inferenzkosten, Latenzen und Konfidenzintervalle werden strukturiert erfasst. | [A] |
| Drift-Erkennung | Sensorik überwacht statistische Abweichungen der Eingabedaten, semantische Verschiebungen und Konfidenzverluste vor dem Auftreten von Fachfehlern. | [A] |
| Wirkungsmessung | Fachliche Erfolgskennzahlen (KPIs) werden vor dem Produktivgang definiert und kontinuierlich gegen die manuelle Vergleichsbasis gemessen. | [E] |
| Resilienz-Testing | Definierte Wiederherstellungsziele (RTO und RPO) für Event-Broker, Vektordatenbanken und Zustandsspeicher werden regelmäßig getestet. | [E] |
| Event-Wiederherstellung | Asynchrone Ereignisverläufe und Verarbeitungszustände sind wiederherstellbar, Mechanismen gegen Doppelverarbeitung sind technisch aktiv. | [E] |
| Notabschaltung | Jede KI-Fähigkeit kann über deterministische Schalter deaktiviert werden, ohne den Prozess zu stoppen, der degradierte Modus ist technisch erprobt. | [E] |

#### Architektonische Reife

| Stufe | Prüfkriterium | Indikator |
|---|---|---|
| **Level 0** | Systemüberwachung erfolgt manuell oder reaktiv. | Fehlerzustände werden primär über manuelle Prüfungen oder Rückmeldungen von Anwendern erkannt. |
| **Level 1** | Technisches System-Monitoring für Kernkomponenten operativ. | Grundlegende Metriken zu Latenz, Verfügbarkeit und Fehlerraten werden für zentrale Infrastrukturkomponenten erhoben und visualisiert. |
| **Level 2** | Prozess-Monitoring und fachliche Kennzahlen aktiv. | Durchlaufzeiten und Vorgangsmengen von Kernprozessen werden automatisiert gemessen. BCM-Konzepte für Kernsysteme liegen verabschiedet vor. |
| **Level 3** | Distributed Tracing, KI-Telemetrie und Resilienztests etabliert. | Tracing verknüpft Systemaufrufe über Komponentengrenzen hinweg. KI-Telemetrie erfasst Token, Kosten und Modellversionen, während Wiederherstellungstests für Integrationsstrecken erfolgreich protokolliert sind. |
| **Level 4** | Drift-Erkennung, Notabschaltung und adaptive Kostensteuerung produktiv. | Drift-Erkennung schlägt bei semantischen Abweichungen automatisiert Alarm. Notabschaltungen und degradierte Betriebsmodi sind im operativen Betrieb technisch erprobt und FinOps-Steuerung steuert Modellaufrufe nach Kosten-Nutzen-Verhältnis. |

#### Prüffragen und Evidenzen

| Prüffrage im Review | Geforderte Evidenz | Stufe |
|---|---|---|
| Werden technische Metriken wie Latenz, Verfügbarkeit und Fehlerraten für alle beteiligten Schnittstellen erhoben? | Monitoring-Dashboards, Alerting-Konfigurationen der Infrastruktur. | **Level 1** |
| Werden Durchlaufzeiten, Abbruchquoten und Prozessbestände in Echtzeit aggregiert und überwacht? | Process-Mining-Dashboards, Kennzahlenberichte der Workflow-Engine. | **Level 2** |
| Schließt das Distributed Tracing externe Modellaufrufe und asynchrone Ereignisse über Systemgrenzen hinweg ein? | OpenTelemetry-Traces, Tracing-Konfigurationen in API-Gateways und Services. | **Level 3** |
| Werden Tokenverbrauch, Inferenzkosten und Latenzen strukturiert als betriebliche Standardmetriken erfasst? | Observability-Dashboards für KI-Workloads, FinOps-Berichte. | **Level 3** |
| Liegt ein erfolgreich protokolliertes Disaster-Recovery-Testprotokoll für asynchrone Event-Streams und Vektordatenbanken vor? | BCM-Testprotokolle, RTO- und RPO-Nachweise. | **Level 3** |
| Sind fachliche Erfolgskennzahlen vor Produktivgang definiert und wird die Wirkung gegen eine historische Baseline gemessen? | KPI-Definitionen, Vorher-Nachher-Wirkungsanalysen. | **Level 3** |
| Erkennt eine automatisierte Sensorik statistische Abweichungen in Prompts oder Daten vor dem Auftreten von Fachfehlern? | Drift-Monitoring-Dashboards, Schwellwert-Konfigurationen. | **Level 4** |
| Existiert ein technisch erprobter Notabschaltungs-Mechanismus, der KI-Fähigkeiten sofort deaktiviert und den Prozess im Notbetrieb weiterführt? | Notfallbetriebshandbuch, Konfiguration und Testnachweis des Circuit Breakers. | **Level 4** |
| Wie verteilt sich das Inferenzvolumen auf interne Modelle und externe Cloud-Dienste? | Betriebsstatistik zur Bemessung von Abhängigkeiten und Latenzrisiken. | **Kontext** |

---

### D6: Leitplanken (Regulatorik und Souveränität)

**Architektonische Relevanz:** Regulatorische Konformität und Datensouveränität sind harte Architekturanforderungen und keine nachgelagerten Governance-Audits. Nachträgliche Härtung erfordert bei produktiven Systemen regelmäßig den vollständigen Neubau der Daten- und Entscheidungspfade.

**Verankerung im Referenzmodell:** Tier 1 (Guidance) und Leitprinzipien (Platform & Security)  

#### Bausteine und Mindestanforderungen

| Baustein | Mindestanforderung für AI-Readiness | Klassifizierung |
|---|---|---|
| Modellregister | Ein zentrales Verzeichnis aller KI-Systeme erfasst Zweckbestimmung, Datenkategorien, Risikoklasse, Verantwortliche und Lebenszyklusstatus. | [E] |
| Risikoklassifizierung | Jeder Anwendungsfall durchläuft eine formale Einstufung nach regulatorischen Risikoklassen (EU AI Act) mit definierten Prüfpfaden. | [E] |
| Zweckbindung | Datenzugriffe von KI-Systemen sind technisch auf den dokumentierten Verarbeitungszweck limitiert und am Datenobjekt überprüfbar. | [E] |
| Entscheidungs-Audit | Für jede automatisierte Entscheidung sind Eingangsdaten, Modell- und Promptversion, Regelstand und Ausgabe manipulationssicher rekonstruierbar. | [E] |
| Menschliche Aufsicht | Definierte Aufsichtsrollen verfügen über das organisatorische und technische Instrumentarium zur wirksamen Intervention und Freigabe. | [E] |
| Release-Governance | Prompts, Modelle, RAG-Kontexte und Regeln unterliegen einer versionierten Freigabepipeline mit Testnachweis und Rollback-Mechanismen. | [E] |
| Datensouveränität | Für jede Verarbeitung ist verbindlich definiert, wo Daten verarbeitet werden und welche Datenbestände die eigene Infrastruktur niemals verlassen dürfen. | [E] |
| Anbieterabstraktion | Inferenzschnittstellen sind herstellerneutral abstrahiert, sodass alternative Anbieter oder On-Premises-Rückfallebenen ohne Refactoring anbindbar sind. | [A] |
| Angriffsresilienz | Technische Schutzmaßnahmen sichern Modelle und RAG-Pipelines gegen Prompt Injection, unautorisierte Werkzeugaufrufe und Datenexfiltration. | [A] |
| FinOps | Laufende Token- und Inferenzkosten werden kontinuierlich Anwendungsfällen und Kostenstellen zugeordnet und dem erzielten Geschäftswert gegenübergestellt. | [A] |

#### Architektonische Reife

| Stufe | Prüfkriterium | Indikator |
|---|---|---|
| **Level 0** | Informelle Nutzung von KI-Werkzeugen. | Der Einsatz von KI-Tools erfolgt dezentral und bedarfsgerecht innerhalb einzelner Fachbereiche. |
| **Level 1** | Regulatorischer Rahmen in Governance-Dokumenten verankert. | Rechtliche und regulatorische Anforderungen für KI und Datenschutz sind in zentralen Richtlinien und Architekturleitlinien formal beschrieben. |
| **Level 2** | Zentrales Modellregister und Risikoeinstufung aktiv. | Alle KI-Anwendungsfälle sind in einem zentralen Register erfasst und nach Risikoklassen eingestuft. Fachliche Rollen für Freigaben sind dokumentiert. |
| **Level 3** | Manipulationssicheres Entscheidungs-Audit und Release-Governance operativ. | Entscheidungen von produktiven KI-Systemen sind über unveränderliche Logs lückenlos rekonstruierbar. Prompts und Modelle durchlaufen automatisierte Test- und Freigabepipelines, während Datensouveränität und Anbieterabstraktion vertraglich und technisch geregelt sind. |
| **Level 4** | Technische Zweckbindung, Angriffsresilienz und FinOps automatisiert. | Zweckbindung und Zugriffsrechte sind am Datenobjekt technisch durchgesetzt. Sicherheitsguardrails schützen vor Prompt Injections und FinOps-Steuerung optimiert Kosten und Geschäftswert in Echtzeit. |

#### Prüffragen und Evidenzen

| Prüffrage im Review | Geforderte Evidenz | Stufe |
|---|---|---|
| Sind regulatorische Leitplanken und Sicherheitsvorgaben für KI-Systeme in verbindlichen Unternehmensrichtlinien definiert? | Governance-Richtlinie für KI, Datenschutzkonzept. | **Level 1** |
| Existiert ein tagesaktuelles Verzeichnis aller KI-Systeme mit Zweckbestimmung, Risikoklasse und verantwortlichen Rollen? | KI-Modellregister, Anwendungsfall-Inventar. | **Level 2** |
| Sind für alle Hochrisiko-Anwendungsfälle formale Kriterien zur Risikobewertung nach EU AI Act dokumentiert? | Risikobewertungsberichte, Konformitätsbewertungsdokumentation. | **Level 2** |
| Sind Eingangsdaten, Modell- und Promptversionen sowie Ausgaben für jede automatisierte Entscheidung auditfest rekonstruierbar? | Audit-Trail-Logdateien, Rekonstruktionsberichte, unveränderliche Speicherprotokolle. | **Level 3** |
| Welche Datenbestände dürfen Cloud-Infrastrukturen keinesfalls verlassen und wie wird dies netzwerk- und identitätsseitig durchgesetzt? | Datensouveränitätskonzept, Data-Loss-Prevention-Regeln, Netzwerktopologie. | **Level 3** |
| Unterliegen Prompts, Modelle und RAG-Pipelines einer automatisierten CI/CD-Release-Governance mit Rollback-Fähigkeit? | Deployment-Pipelines, Testberichte für Modellversionen, Release-Freigaben. | **Level 3** |
| Wie schützt sich die Systemlandschaft technisch gegen Prompt Injection, unautorisierte Werkzeugaufrufe und Datenexfiltration? | Sicherheitskonzept, Guardrail-Konfigurationen, Penetrationstest-Berichte. | **Level 4** |
| Sind Zweckbindung und Zugriffsfilter am Datenobjekt technisch implementiert, um unautorisierte Modellnutzung zu verhindern? | Token-basierte Filterregeln, ABAC-Richtlinien, Durchsetzungsnachweise. | **Level 4** |
| Werden Token- und Inferenzkosten automatisiert je Fachbereich und Anwendungsfall erfasst und dem Geschäftswert gegenübergestellt? | FinOps-Dashboards, Kostenstellen-Zuordnungen, ROI-Auswertungen. | **Level 4** |
| Welche regulatorischen Fristen und Aufbewahrungspflichten gelten für die jeweiligen Geschäftsfälle? | Compliance-Matrix und regulatorische Dokumentationsanforderungen. | **Kontext** |

---

## 6. Bewertungsmodell & Assessment-Methodik

### 6.1 Die zwei Bewertungsachsen

Jede Prüfdimension (D1 bis D6) wird anhand von zwei strikt voneinander getrennten Achsen bewertet:

| Achse | Wertebereich | Methodische Bedeutung |
|---|---|---|
| **Reifegrad (Maturity)** | Level 0, Level 1, Level 2, Level 3, Level 4 | Zustand der Systemlandschaft bezogen auf das jeweilige **binäre Stufenkriterium**. Bereichswerte (z. B. "Level 2–3") sind unzulässig. |
| **Konfidenz (Belastbarkeit)** | Hoch, Mittel, Niedrig | Grad der empirischen Absicherung der Bewertung. Zwischenwerte sind unzulässig. |

**Konfidenz-Kriterien:**
- **Hoch:** Befund ist durch mindestens ein verifiziertes Laufzeit- oder Konfigurationsartefakt *und* eine unabhängige Stakeholder-Aussage belegt.
- **Mittel:** Befund stützt sich auf ein offizielles, verabschiedetes Dokument oder eine schlüssige Expertenaussage ohne Zweitbeleg.
- **Niedrig:** Einzelaussage ohne schriftliche Evidenz, oder Dokumente im reinen Entwurfsstatus.

### 6.2 Evidenzhierarchie

Die Aussagekraft von Befunden richtet sich nach ihrer Position in der Evidenzhierarchie:

| Rang | Evidenzklasse | Tragweite für die Bewertung |
|---|---|---|
| **1** | Laufzeit-, Code- und Konfigurationsnachweis (CI/CD-Pipelines, API-Gateway-Configs, Traces, Testprotokolle). | Trägt Bewertungen bis **Level 4** mit Konfidenz **Hoch**. |
| **2** | Verabschiedetes Architektur- und Governance-Artefakt mit Versionsstand und Owner. | Trägt Bewertungen bis **Level 3** mit Konfidenz **Mittel bis Hoch**. |
| **3** | Arbeitsdokument oder Konzept im Entwurfsstatus. | Trägt höchstens **Level 2** mit Konfidenz **Mittel**. |
| **4** | Mündliche Interviewaussage einer zuständigen Führungskraft. | Belegt Zielbild und Absicht, trägt höchstens Konfidenz **Mittel**. |
| **5** | Mündliche Aussage Dritter über andere Bereiche. | Dient ausschließlich als Prüfhinweis, keine Bewertungsgrundlage. |

### 6.3 Ableitung des Zielniveaus (Einsatzprofile)

Das anzustrebende Zielniveau wird nicht willkürlich vorgegeben, sondern aus dem geplanten Einsatzprofil abgeleitet. Die Profile operationalisieren die qualitativen Zustandsklassen aus Kapitel 2 für konkrete Transformationsvorhaben:

| Einsatzprofil | Zustandsklasse | Fachlicher Zuschnitt | Risikoklasse und Kontrollschranken | D1 | D2 | D3 | D4 | D5 | D6 |
|---|---|---|---|---|---|---|---|---|---|
| **Profil A: Explorativ** | **AI-enabled** | Spezifische Assistenzlösungen zur Wissensaggregation und Entscheidungsvorbereitung. | Geringe Risikoklasse, rein vorschlagend, keine Schreibrechte an Kern- oder Transaktionssystemen. | Level 1 | Level 2 | Level 2 | Level 1 | Level 1 | Level 1 |
| **Profil B: Operativ** | **AI-ready** | Fokussierte Prozessassistenz und strukturierte Aufgabenausführung in operativen Kernprozessen. | Mittlere Risikoklasse, deterministische Kontrollschranke mit obligatorischer menschlicher Freigabe. | Level 2 | Level 3 | Level 3 | Level 2 | Level 2 | Level 2 |
| **Profil C: Skalierend** | **AI-ready** | Organisationsweites Portfolio produktiver KI-Dienste über mehrere Geschäftsbereiche und Domänen. | Hohe Risikoklasse bei geschäftskritischen Prozessen, erfordert durchgängige duale Kontrollschranken und lückenlose Audit-Trails. | Level 3 | Level 3 | Level 3 | Level 3 | Level 3 | Level 3 |
| **Profil D: Autonom** | **AI-native** | Eigenständige Agentensysteme mit adaptiver Planung, Tool-Nutzung und dynamischer Handlungsabfolge. | Kritische Risikoklasse mit stochastischen Kaskadeneffekten, erfordert maschinelle Schranken und Least-Privilege-Kapselung. | Level 3 | Level 4 | Level 4 | Level 4 | Level 4 | Level 4 |

### 6.4 Falsifizierbarkeit

Zur Sicherung der methodischen Qualität muss jeder Kernbefund eine explizite **Widerlegungsbedingung** enthalten: Welcher konkrete Fund (z. B. ein funktionierendes Gateway-Log oder ein verabschiedeter Data Contract) würde die Einschätzung invalidieren? Befunde ohne Widerlegungsbedingung gelten als unzulässige Deutungen.

---

## 7. Visuelles Overlay (Visual Layer Guide)

Zur Kommunikation und Visualisierung in Architecture Boards wird die abgeleitete visuelle Präsentationsvorlage des Enterprise Landscape Reference Models verwendet:

```
┌─────────────────────────────────────────────────────────────────────────────────────────────┬───────────────────────────┐
│ Guidance (Tier 1)                                                                           │ Guiding Principles        │
│   [ D6: Leitplanken (Regulatorik und Souveränität) ]                                        │                           │
├────────────────────────────────────────┬────────────────────────────────────────────────────┤  Business & Organization  │
│ Business Layer (Tier 2)                │ Experience (Gateway)                               │  - Domain Autonomy        │
│   Value Streams                        │   [ Human-in-the-Loop, Adaptive UI, Explainability]│  - Conway's Law           │
│   Business Capabilities                ├───────────────┐                                    │                           │
│   Business Processes                   │    Domains    │ Data Layer (Tier 4)                │                           │
│   [ D1: Handlungsraum (Fachliche       │   (Bounded    │   Semantics & Ontology             ├───────────────────────────┤
│         Domänen und Capabilities) ]    │   Contexts)   │   Data Contracts                   │  Application & Data       │
├─────────────────── Alignment ──────────┤               │   Data Products                    │  - Data as a Product      │
│ System Layer (Tier 3)                  │               │   [ D2: Wissensbasis (Daten und    │  - Contract-First         │
│   Workflows & Orchestration            ├───────────────┘         Semantik) ]                │                           │
│   Services & Applications              │ Integration (Gateway)                              ├───────────────────────────┤
│   [ D4: Prozessführung (Abläufe und    │   [ D3: Werkzeuge (Funktionen und Tools) ]         │  Platform & Security      │
│         Kontrollschranken) ]           │                                                    │  - Zero Trust             │
├────────────────────────────────────────┴────────────────────────────────────────────────────┤  - Observability          │
│ Foundation (Tier 5)                                                                         │  - Adversarial Defense    │
│   [ D5: Telemetrie (Laufzeitüberwachung und Ausfallschutz) ]                                │                           │
└─────────────────────────────────────────────────────────────────────────────────────────────┴───────────────────────────┘
```

### 7.1 Heatmap-Farbcodierung

Auf den Boxen der visuellen Präsentationsvorlage ([enterprise-landscape-model.png](../../model/assets/enterprise-landscape-model.png) / [enterprise-landscape-model.pptx](../../model/assets/enterprise-landscape-model.pptx)) werden Statusfarben aufgetragen. Die Bewertung ist stets relativ zum gewählten Einsatzprofil (Profil A bis D aus Abschnitt 6.3) zu interpretieren:

- **Rot (Blockierender Mangel):** Unterschreitet das für das Zielprofil definierte Soll-Niveau signifikant (Ist-Zustand liegt zwei oder mehr Stufen unter Soll oder auf Level 0 bei Soll ab Level 2) und blockiert den sicheren Betrieb.
- **Gelb (Handlungsbedarf):** Liegt genau eine Stufe unter dem definierten Soll-Niveau für das Zielprofil, oder Voraussetzungen sind zwar vorhanden, aber noch nicht durchgängig automatisiert und formalisiert.
- **Grün (Target-Ready):** Erfüllt oder übertrifft das für das gewählte Einsatzprofil geforderte Soll-Niveau (Ist-Zustand entspricht mindestens dem Soll-Wert der jeweiligen Dimension aus Abschnitt 6.3).
- **Blau (AI-Native / Enabler):** Übertrifft das Soll-Niveau des Zielprofils signifikant oder realisiert fortgeschrittene AI-Native-Eigenschaften auf Level 4 (z. B. deklarative Laufzeit-Tool-Registry, adaptive Agentengovernance).

---

## 8. Offene Punkte dieser Referenz

Folgende methodische Arbeitspakete sind für die Weiterentwicklung vorgesehen:

1. **Belegtiefe der [A]- und [H]-Kriterien:** Empirische Härtung der Capability-Map-Forderung in D1 und des KI-Potenzial-Scorings über reale Transformationsfälle in Mandanten-Reviews.
2. **Einsatzprofil-Validierung:** Abgleich der Schwellwerte in Matrix 6.3 mit weiteren Transformationsprojekten in geschäftskritischen, heterogenen Unternehmenslandschaften im Produktiveinsatz.

---

## Anhang A: KI-Potenzial-Scoring auf Capability-Ebene

Sechs Dimensionen zur objektiven Bewertung des KI-Hebels je Business Capability auf einer Skala von 1 bis 5. Dient der begründeten Priorisierung von Anwendungsfällen statt opportunistischem Aktionismus:

### A.1 Übersicht der Dimensionen

| Dimension | Prüffrage | Fokus |
|---|---|---|
| **1. Wissensnutzung** | Wie stark basiert die Fähigkeit auf kodifizierbarem Fachwissen? | Kodifizierungsgrad und Formalisierung |
| **2. Prozessstandardisierung** | Wie regelbasiert und variantenarm läuft die Fähigkeit ab? | Deterministische Prozessführung |
| **3. Datenverfügbarkeit** | Wie verfügbar und qualitativ tragfähig sind die Eingangsdaten? | Schnittstellen, Data Contracts und Semantik |
| **4. Entscheidungsunterstützung** | Lassen sich Entscheidungen vorbereiten oder delegieren? | Strukturierbarkeit von Ermessensspielräumen |
| **5. Personalisierung** | Wie wertstiftend ist ein individueller Zuschnitt des Ergebnisses? | Differenzierung im Kunden- oder Partnerkontakt |
| **6. Repetitivität** | Wie hoch sind Transaktionsvolumen und Gleichartigkeit der Fälle? | Skaleneffekt bei Automatisierung |

### A.2 Stufenkriterien (1 bis 5) je Dimension

#### 1. Wissensnutzung
- **Stufe 1:** Wissen existiert ausschließlich implizit in den Köpfen einzelner Experten (Silo-Wissen, Bauchgefühl, keinerlei Dokumentation).
- **Stufe 2:** Fragmentierte Notizen, veraltete Wikis oder individuelle Dokumentenablagen vorhanden, stark widersprüchlich und inkonsistent.
- **Stufe 3:** Offizielle Richtlinien, Handbücher oder Standard Operating Procedures (SOPs) existieren, sind jedoch rein textbasiert und unstrukturiert.
- **Stufe 4:** Strukturierte Wissensbasis vorhanden (maschinenlesbar verschlagwortete Verträge, semantisch annotierte Richtlinien, FAQs).
- **Stufe 5:** Vollständig formalisiertes und versioniertes Wissen (formale Ontologien, Wissensgraphen, maschinenlesbare Taxonomien, kuratierte Vektorindizes).

#### 2. Prozessstandardisierung
- **Stufe 1:** Vollständig ad hoc getriebener Ablauf, fast jeder Vorgang ist ein Sonderfall mit manueller Einzelfallbehandlung.
- **Stufe 2:** Ablauf grob verabredet bei hoher Ausnahmequote (> 50 %) und informellen Umgehungspfaden.
- **Stufe 3:** Kernprozess in BPMN oder Prozesslandkarte dokumentiert, Ausnahmen geregelt, manuelle Abzweigungen vorhanden.
- **Stufe 4:** Hoher Standardisierungsgrad, Prozesse laufen überwiegend in Workflow-Engines mit standardisierter Ausnahmebehandlung.
- **Stufe 5:** Deterministischer Ende-zu-Ende-Prozess ohne Medienbrüche, Varianten sind vollständig modelliert und regelbasiert steuerbar.

#### 3. Datenverfügbarkeit und Datenqualität
- **Stufe 1:** Daten liegen primär analog (Papier), in isolierten Tabellen oder Freitextfeldern vor, keine maschinellen Schnittstellen.
- **Stufe 2:** Daten sind digital vorhanden, aber in proprietären Legacy-Silos eingeschlossen, Abruf erfordert manuelle Exporte oder SQL-Skripte.
- **Stufe 3:** Daten sind über standardisierte Schnittstellen (REST, SOAP) abrufbar, grundlegende Schemavalidierung vorhanden bei möglichen Inkonsistenzen.
- **Stufe 4:** Strukturierte Datenprodukte mit dokumentierten Data Contracts und kontinuierlicher Qualitätsmessung verfügbar.
- **Stufe 5:** Vollständig kuratierte, echtzeitfähige Datenprodukte (Event Streams, Feature Stores, Vektorindizes) mit garantierter SLA und Lineage.

#### 4. Entscheidungsunterstützung (Delegierbarkeit)
- **Stufe 1:** Komplexe, unstrukturierte Einzelfallentscheidungen mit starkem strategischem oder rechtlichem Ermessensspielraum, nicht delegierbar.
- **Stufe 2:** Entscheidungen erfordern fundierte Senior-Expertise, Kriterien sind nur teilweise operationalisierbar.
- **Stufe 3:** Wiederkehrende Entscheidungen mit klarem Regelrahmen, Vorprüfung oder Scoring durch KI als Vorbereitung für Sachbearbeiter aktiv (Vorschlagssystem).
- **Stufe 4:** Schwellwertbasierte Entscheidungen mit eindeutigen Kriterien, automatisierte Entscheidung bei hoher Konfidenz und Eskalation bei Grenzfällen.
- **Stufe 5:** Standardisierte Klassifikations- und Routing-Entscheidungen mit geringer Fehlertoleranz, vollständige Dunkelverarbeitung produktiv.

#### 5. Personalisierung
- **Stufe 1:** Einheitliche Standardabwicklung ohne Differenzierung (One-size-fits-all), Personalisierung bietet keinen geschäftlichen Mehrwert.
- **Stufe 2:** Geringe Differenzierung nach wenigen statischen Kundengruppen oder Standardsegmenten.
- **Stufe 3:** Kontextuelle Anpassung (z. B. branchenspezifische Klauseln, segmentierte Ansprache) stiftet spürbaren Mehrwert.
- **Stufe 4:** Dynamische Anpassung an Vorgangshistorie, Präferenzen und Risikoprofil für maßgeschneiderte Interaktionen oder Berichte.
- **Stufe 5:** Hyperpersonalisierung in Echtzeit als zentraler Wettbewerbsvorteil (individuelle Verträge, dynamische Konditionen, adaptive Dialoge).

#### 6. Repetitivität und Transaktionsvolumen
- **Stufe 1:** Sehr geringes Fallaufkommen (< 100 Fälle pro Jahr), Automatisierung amortisiert sich wirtschaftlich nicht.
- **Stufe 2:** Geringes bis mittleres Volumen (Hunderte bis wenige Tausend Fälle pro Jahr), manuelle Abarbeitung dominiert.
- **Stufe 3:** Mittleres Volumen (mehrere 10.000 Fälle pro Jahr), spürbare Kapazitätsbindung durch Routineaufgaben.
- **Stufe 4:** Hohes Volumen (> 100.000 Fälle pro Jahr) mit hoher Gleichartigkeit der Geschäftsfälle, wesentlicher Effizienzhebel.
- **Stufe 5:** Massengeschäft und Hochfrequenz (> 1.000.000 Transaktionen pro Jahr), Automatisierung ist geschäftskritische Voraussetzung für Skalierung.

### A.3 Aggregationsmatrix und Portfolio-Quadranten

Die Bewertung je Business Capability wird in zwei übergeordneten Koordinaten aggregiert:

$$\text{Machbarkeit (Feasibility)} = \frac{\text{Datenverfügbarkeit} + \text{Prozessstandardisierung}}{2}$$

$$\text{Wirtschaftlicher Hebel (Impact)} = \frac{\text{Repetitivität} + \text{Entscheidungsunterstützung} + \text{Personalisierung} + \text{Wissensnutzung}}{4}$$

| Portfolio-Quadrant | Schwellenwert | Empfohlene architektonische Handlungsstrategie |
|---|---|---|
| **Quick Wins** | Machbarkeit $\ge 3{,}5$, Hebel $\ge 3{,}5$ | **Sofortige Pilotierung:** Anwendungsfall kann auf bestehendem Fundament zügig umgesetzt und skaliert werden. |
| **Strategic Transformations** | Machbarkeit $< 3{,}5$, Hebel $\ge 3{,}5$ | **Fundamentsanierung vor KI:** Hoher wirtschaftlicher Nutzen, aber fehlende Daten- oder Prozessreife. Zunächst Bounded Contexts und Datenprodukte aufbauen. |
| **Efficiency Fillers** | Machbarkeit $\ge 3{,}5$, Hebel $< 3{,}5$ | **Selektive Standardautomatisierung:** Geringer geschäftlicher Hebel, aber niedrige Einstiegshürde. Nur bei minimalem Zusatzaufwand automatisieren. |
| **De-Prioritize** | Machbarkeit $< 3{,}5$, Hebel $< 3{,}5$ | **Keine Investition:** Weder wirtschaftlich lohnend noch technisch vorbereitet. Verbleibt in manueller Bearbeitung. |

---

## Änderungshistorie

| Version | Datum | Bearbeitung | Wesentliche Änderungen |
|---|---|---|---|
| 0.1 | 2026-09-25 | Julia | Erstdefinition, enthielt projektspezifische Erstbefüllung und Fremdkundenverweise. |
| 0.2 | 2026-09-28 | Julia | Kundenbezüge und vertrauliche Projektdaten vollständig entfernt. Ergänzt: Herkunftskennzeichnung [E]/[A]/[H], binäre Stufenkriterien, Evidenzhierarchie (Rang 1 bis 5), profilbasierte Zielniveau-Ableitung, Falsifizierbarkeit. |
| 0.3 | 2026-09-30 | Julia (Refine) | Vollständige Harmonisierung auf die 5 kanonischen Tiers des [Enterprise Landscape Reference Model](../../model/specification.md) und das verbindliche [Thematische Overlay Template](../../templates/overlay-template.md). Altes L1–L5-Schichtenmodell vollständig durch Tier-by-Tier Projektion ersetzt. Konsistente Namensgebung für Tier 4 (*Data Layer* mit Elementen *Domänen*, *Semantik*, *Datenprodukte*). Bereinigung von colloquialem Wording hin zu präziser horizontaler und vertikaler Ausrichtung. |
| 0.4 | 2026-10-01 | Julia (Refine) | **Vollständige Schärfung und Harmonisierung auf Architekturstandard:**<br>- Kapitel 1 und 2: Klares Metamodell-Docking, qualitative Reifestufen der Gesamtlandschaft mit K.o.-Kriterium der Dualen Kontrollschranke.<br>- Kapitel 3: Prägnante Taxonomie der Prüfdimensionen D1 bis D6 (Handlungsraum, Wissensbasis, Werkzeuge, Prozessführung, Telemetrie, Leitplanken).<br>- Kapitel 4: Schichtenprojektion auf 5 Tiers, 4 architektonische Invarianten mit expliziten Anti-Patterns, 3 nicht verhandelbare Leitprinzipien bei Zielkonflikten.<br>- Kapitel 5: Vollständige Überarbeitung aller Dimensionen D1 bis D6 mit kanonischen singulären Bausteinen, sauberem Epistemic Tagging ([E] und [A], keine [H]-Kriterien im Audit), rein positiven Reifegrad-Indikatoren ohne Defizitsprache und dreispaltigen Review-Tabellen mit expliziter Stufen-Zuordnung.<br>- Kapitel 6 und 7: Bewertungsmodell mit Evidenzhierarchie, profilbasierter Zielniveau-Ableitung und typografisch bereinigtem visuellem Referenzdiagramm.<br>- Anhang A: Stufenkriterien für alle sechs Potenzialdimensionen vollständig ausformuliert und Aggregationsmatrix mit Portfolio-Quadranten formalisiert.<br>- Formale Härtung: Vollständige Bereinigung von Semicolons, Gedankenstrichen und uneinheitlicher Symbolik gemäß Workspace-Styleguide. |
