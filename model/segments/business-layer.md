# Segment-Architektur: Business Layer & Capabilities

**Typ:** Segment-Architektur (Vertikaler Zoom-in)  
**Version:** 0.1  
**Status:** Entwurf  
**Übergeordnetes Referenzmodell:** [Enterprise Landscape Model](../specification.md) (Tier 2)  
**Autor:** Julia Senner (Enterprise & Solution Architecture)  

---

## 1. Zweck und Einordnung

Dieses Dokument bildet den vertikalen Zoom-in in den **Business Layer (Tier 2)** des Enterprise Landscape Referenzmodells. Es formalisiert das Zusammenspiel zwischen geschäftlicher Wertschöpfung, stabilen Geschäftsfähigkeiten (Capabilities) und der softwarearchitektonischen Domänengliederung (Bounded Contexts).

### Epistemische Einordnung
- **`[E]` Wertströme & Capabilities:** Standard nach TOGAF und Business Architecture Guild (BIZBOK). Trennung von *Was* getan wird (Capability) und *Wie/Wer* es tut (Prozess/Organisation).
- **`[A]` Strategische Differenzierung (Core vs. Supporting vs. Generic):** Ableitung aus Domain-Driven Design (Core Domains) und Wardley Mapping zur Steuerung von Sourcing- und Investitionsentscheidungen.
- **`[H]` Bounded Context als primäre Schnittstelle:** Hypothese, dass eine 1:n-Zuordnung von Bounded Contexts zu Capabilities die langlebigste Entkopplung von Fach- und IT-Strukturen darstellt.

---

## 2. Strukturschema des Business Layer Zoom-in

```
┌────────────────────────────────────────────────────────────────────────┐
│ 1. Value Stream (End-to-End Wertschöpfung)                             │
│    [Bedarf / Trigger] ────► [Bewertung / Decision] ────► [Abwicklung]  │
└───────────────────────────────────┬────────────────────────────────────┘
                                    │ operationalisiert durch
┌───────────────────────────────────▼────────────────────────────────────┐
│ 2. Business Capability Map (L1 / L2)                                   │
│    ┌─────────────────────────┬───────────────────┬───────────────────┐ │
│    │ Core / Differentiating  │ Supporting        │ Generic/Commodity │ │
│    │ (Wettbewerbsvorteil)    │ (Operative Pflicht)│ (Standardsoftware)│ │
│    │ z.B. Dynamic Pricing    │ z.B. Claims Intake│ z.B. Accounting   │ │
│    └─────────────────────────┴───────────────────┴───────────────────┘ │
└───────────────────────────────────┬────────────────────────────────────┘
                                    │ definiert Grenzen für
┌───────────────────────────────────▼────────────────────────────────────┐
│ 3. Schnittstelle zu Tier 4 (Data Layer): Domänen (DDD)                 │
│    [ Bounded Context A ]  ◄── (Contract/API) ──►  [ Bounded Context B ]│
└────────────────────────────────────────────────────────────────────────┘
```

---

## 3. Offene Punkte & Parkdeck

- [ ] Kriterienkatalog zur Trennung von Core, Supporting und Generic Capabilities definieren.
- [ ] Granularitätsleitfaden für L1- vs. L2-Capabilities erstellen.
- [ ] Muster für das Mapping von Capabilities auf Bounded Contexts formalisieren.

*(Inhaltliche Arbeit pausiert gemäß Architekturentscheidung vom 2026-09-30; Wiederaufnahme über `!backlog` steuerbar).*
