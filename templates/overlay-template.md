# Thematisches Overlay: [Name des Themas, z. B. Cloud-Native / Zero-Trust]

**Typ:** Thematisches Overlay  
**Version:** [z. B. 0.1]  
**Status:** [Entwurf / Pilotierung / Stabil]  
**Übergeordnetes Referenzmodell:** [Link zum Referenzmodell eintragen, z. B. `../../model/specification.md`]  
**Kompatibilität:** Enterprise Landscape Model >= v0.8  
**Autor:** [Name / Rolle]  
**Abgeleitete Dokumente:** Projektbezogene Bewertungen werden in eigenständigen Dokumenten oder Mandanten-Repositories geführt und referenzieren dieses Overlay über Versionsnummern.  

---

## 1. Zweck, Geltungsbereich und Abgrenzung

### 1.1 Zweck
Welche themenspezifische Zielarchitektur oder Prüflinse spannt dieses Overlay auf? Welche Anforderungen müssen Landschaften erfüllen, um für dieses Thema tragfähig zu sein?

### 1.2 Geltungsbereich & Grenzen
- **Gilt für:** [z. B. Transaktionale Kernsysteme, hybride Landschaften, reguliertes Umfeld]
- **Gilt nicht für:** [Bewusste Abgrenzungen, z. B. isolierte Tool-Evaluationen, experimentelle Prototypen]
- **Verhältnis zur Umsetzungsfähigkeit:** [Trennung zwischen Architektureigenschaften und organisatorischer Lieferfähigkeit]

### 1.3 Epistemische Kennzeichnung
Alle Prinzipien und Mindestkriterien müssen transparent nach Herkunft ausgewiesen werden:
- **`[E]` Etablierte Praxis:** In Standards, Fachliteratur oder Regulatorik verankert.
- **`[A]` Abgeleitet:** Aus empirischen Projektbefunden und Transformationsmustern gewonnen.
- **`[H]` Hypothese:** Plausibel, aber diskursiv abzusichern.

---

## 2. Thematische Reifestufen / Klassifikation

Definition von 2–3 qualitativen Zustandsklassen zur Vermeidung von Begriffsunschärfe (z. B. *Enabled* vs. *Ready* vs. *Native*):

| Zustand | Definition | Typisches Erkennungsmerkmal |
|---|---|---|
| **Stufe A (z. B. Enabled)** | Punktuelle Nutzung an den Rändern, keine fundamentale Landschaftsanpassung. | [Merkmal eintragen] |
| **Stufe B (z. B. Ready)** | Landschaft stellt Voraussetzungen bereit, sodass neue Use Cases ohne Umbau konfigurierbar sind. | [Merkmal eintragen] |
| **Stufe C (z. B. Native)** | Das Thema ist integraler First-Class-Bestandteil aller Schichten und Prozesse. | [Merkmal eintragen] |

---

## 3. Taxonomie der Prüfdimensionen (Meso-Ebene)

Definition der themenspezifischen Handlungs- und Prüffelder (D1 bis Dn), die die gemeinsame Bewertungssprache aufspannen:

| Dimension (Kurzanker) | Fachlicher Scope | Architektonische Kernanforderung (Leitsatz) |
|---|---|---|
| **D1 [Kurzlabel]** | [z. B. Fachliche Strukturen & Domänen] | [Kernanforderung / unumstößlicher Leitsatz] |
| **D2 [Kurzlabel]** | [z. B. Daten & Semantik] | [Kernanforderung / unumstößlicher Leitsatz] |
| **D3 [Kurzlabel]** | [z. B. Funktionen & Tools] | [Kernanforderung / unumstößlicher Leitsatz] |

---

## 4. Projektion auf das Referenzmodell (Tier-by-Tier Spezialisierung)

Ein Overlay erfindet kein eigenes Schichtenmodell, sondern dockt direkt an die Tiers des übergeordneten Referenzmodells an:

| Tier im Referenzmodell | Spezifische Soll-Eigenschaften / Bausteine | Prüfdomäne |
|---|---|---|
| **Tier 1: Governance** | [z. B. Compliance-by-Design, Risikoklassen, Rollenmodelle, Standards] | [D...] |
| **Tier 2: Business Layer** | [z. B. Capability-Zuschnitt, Human-in-the-Loop, Wertstromgrenzen, Experience] | [D...] |
| **Tier 3: System Layer** | [z. B. Service-Autonomie, Workflow-Orchestrierung, Integration & APIs] | [D...] |
| **Tier 4: Data Layer** | [z. B. Domänen-Ownership (DDD), Semantik (Data Contracts, Schemata), Datenprodukte (operativ & analytisch)] | [D...] |
| **Tier 5: Foundation** | [z. B. Runtime, Observability, Telemetrie, Secrets & Identity, Storage] | [D...] |
| **Guiding Principles (Pillar)** | [Themenspezifische Schärfung der Entscheidungsleitplanken] | [Querschnitt] |

---

## 5. Diagnostisches Messgitter (Reifegrade & Evidenzen)

Für jede Prüfdomäne werden stufenweise, **binär prüfbare Stufenkriterien** definiert (Vermeidung von meinungsbasierten Audits):

### Domäne 1: [Name der Domäne, z. B. Daten & Semantik]
- **KI-/Target-Ready Mindestkriterium [E/A/H]:** [Konkrete Bedingung]
- **Reifegradleiter:**
  - **Level 1 (Initial):** [Stufenkriterium]
  - **Level 2 (Wiederholbar):** [Stufenkriterium]
  - **Level 3 (Target-Ready):** [Stufenkriterium — Mindestanforderung]
  - **Level 4 (Optimiert/Native):** [Stufenkriterium]
- **Benötigte Evidenzarten:** [z. B. Datenverträge im Git-Repo, Schemata, CI/CD-Pipelines, Monitoring-Dashboards]

---

## 6. Visuelles Overlay (Visual Layer Guide)

Hinweise für die visuelle Aufbereitung auf der abgeleiteten Präsentationsvorlage (PPTX/PNG) des Referenzmodells:
- **Betroffene Boxen / Heatmap:** Welche Bereiche der visuellen Präsentationssicht des Referenzmodells werden hervorgehoben?
- **Farbcodierung:** [z. B. Rot = blockierender Mangel, Gelb = Handlungsbedarf, Grün = Target-Ready, Blau = AI-Native]
- **Zusatzsymbole / Badges:** [z. B. spezifische Komponenten-Icons im visuellen Raster]
