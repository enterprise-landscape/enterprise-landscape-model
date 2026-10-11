# Enterprise Landscape Model (ELM)

> A pragmatic, open reference architecture for modern enterprise landscapes.

[![Version: v0.8](https://img.shields.io/badge/version-v0.8%20(Public%20Preview)-blue.svg)](model/specification.md)
[![Lizenz: CC BY 4.0](https://img.shields.io/badge/license-CC%20BY%204.0-green.svg)](LICENSE.md)

**Klassifikation:** Enterprise Architecture Framework (nach ISO/IEC/IEEE 42010)  
**Kern-Artefakt:** Kanonisches Referenzmodell  

Hersteller- und branchenneutrales Referenzmodell, methodisches Diagnoseraster und praxistauglicher Ordnungsrahmen für nachhaltige, evolvierbare und zukunftsfähige Unternehmens- und Systemlandschaften.

---

## 1. Das Kernmodell auf einen Blick

Das **Enterprise Landscape Model (ELM)** definiert einen verbindlichen strukturellen, semantischen und organisatorischen Ordnungsrahmen. Es überwindet Silos zwischen Fachbereich, Software-Engineering und Plattformbetrieb, ohne in die administrative Bürokratie schwerfälliger Großframeworks zu verfallen.

![Enterprise Landscape Reference Model](model/assets/enterprise-landscape-model.png)

- **Spezifikation (SSoT):** [model/specification.md](model/specification.md)
- **Vektor-Präsentationsvorlage:** [model/assets/enterprise-landscape-model.pptx](model/assets/enterprise-landscape-model.pptx)

---

## 2. Inhaltskatalog & Navigator

| Artefakt | Typ | Beschreibung & Nutzen | Quelle / Ablage | Status / Reife |
|---|---|---|---|---|
| **[Kernmodell: Spezifikation](model/specification.md)** | Referenzmodell | ELM Lean Metamodel (Formale Ontologie), fünf Tiers, Entkopplungsgateways, $5 \times 5$ Interaktionsmatrix und Guiding Principles | `model/specification.md` | v0.8 (Public Preview) |
| **[Segment: Business Layer](model/segments/business-layer.md)** | Segment-Spezifikation | Vertikaler Zoom-in in Tier 2: Wertströme, Capabilities und Bounded Contexts | `model/segments/business-layer.md` | v0.1 (Entwurf) |
| **[Thematisches Overlay: AI-Readiness](overlays/ai-readiness/ai-readiness-overlay.md)** | Thematisches Overlay | Transversale Projektion über alle 5 Tiers: Prüflinse entlang D1 bis D6 mit K.o.-Kriterien | `overlays/ai-readiness/` | v0.4 (Pilotierung) |
| **[Architekturreview — Canvas](canvases/review-canvas.md)** | Canvas | Interaktive Arbeitsfläche für strukturierte Architektur-Reviews | `canvases/review-canvas.md` | v0.1 (Arbeitsvorlage) |
| **[Baustein-Vorlage](templates/baustein-template.md)** | Vorlage | Standard-Template für neue Segmente, Methoden und Linsen | `templates/baustein-template.md` | Standard |
| **[Overlay-Vorlage](templates/overlay-template.md)** | Vorlage | Standard-Template für relationale Overlays mit Tier-Projektion | `templates/overlay-template.md` | Standard |
| **[Case Review Vorlage](templates/case-review-template.md)** | Vorlage | Strukturierte Vorlage für konkrete, anonymisierte Mandanten-Reviews | `templates/case-review-template.md` | Standard |

---

## 3. Repository-Struktur

```text
enterprise-landscape-model/
├── README.md                                  # Repository-Einstieg, Navigator & Modell-Übersicht
├── LICENSE.md                                 # 100 % CC BY 4.0 Lizenzvereinbarung
│
├── model/                                     # Das Kernmodell (Enterprise Landscape Model)
│   ├── specification.md                       # Normative Spezifikation (Lean Metamodel, 5 Tiers, Gateways, Invarianten)
│   ├── segments/                              # Schichten-Vertiefungen (z. B. business-layer.md)
│   └── assets/                                # Grafiken & Präsentationsvorlagen
│       ├── enterprise-landscape-model.png
│       └── enterprise-landscape-model.pptx
│
├── overlays/                                  # Thematische Querschnitts-Zielbilder
│   └── ai-readiness/
│       ├── ai-readiness-overlay.md            # Spezifikation & Dimensionen (D1 bis D6)
│       └── assets/
│           └── ai-readiness-overlay.pptx
│
├── canvases/                                  # Anwendungs- & Workshop-Hilfen
│   └── review-canvas.md
│
└── templates/                                 # Standardisierte Vorlagen für Erweiterungen & Reviews
    ├── baustein-template.md
    ├── overlay-template.md
    └── case-review-template.md
```

---

## 4. Methodische Grundprinzipien

1. **Die funktionale Triade:** Jedes Artefakt trennt explizit zwischen *Normativ* (Zielzustand), *Diagnostisch* (Evidenzen & Reifegrade) und *Kommunikativ* (Verständlichkeit für Entscheider).
2. **Epistemische Disziplin:** Aussagen und Kriterien sind transparent ausgewiesen (`[E]` Etablierte Praxis, `[A]` Abgeleitet aus Praxisbefunden, `[H]` Diskursiv zu prüfende Hypothese; das kanonische Kernmodell spezifiziert ausschließlich gesicherte `[E]`- und `[A]`-Bausteine).
3. **Das Modell ist die Single Source of Truth (Modell vor Folie):** Textuelle Spezifikationen in Markdown sind verbindlich. Folien (PPTX) und Diagramme (PNG) sind abgeleitete Präsentationssichten.
4. **Strikte Mandantentrennung (Struktur vs. Instanz):** Das Modell ist 100 % hersteller- und kundenneutral. Mandantenspezifische Bewertungen und vertrauliche Befunde verbleiben in separaten Projekt-Repositories.

---

## 5. Status & Weiterentwicklung

Dieses Repository befindet sich im Status **v0.8 (Public Preview)**. Der strukturelle Kern ist stabil und wird auf Basis von Praxiserfahrungen kontinuierlich verfeinert.

Vorschläge, Erweiterungen und Diskussionen werden transparent über GitHub Issues und Discussions geführt.

---

## 6. Lizenz

Dieses Repository steht unter der Lizenz **[Creative Commons Attribution 4.0 International (CC BY 4.0)](LICENSE.md)**.
