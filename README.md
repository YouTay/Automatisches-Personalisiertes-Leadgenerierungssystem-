# Automatisiertes Leadgenerierungssystem — syro-ai

Ein automatisiertes, KI-gestütztes Cold-Email-System auf Basis von n8n, das tausende personalisierte E-Mails pro Woche generiert und versendet — ohne manuellen SDR-Aufwand.

---

## Demo

[![Automatisiertes Leadgenerierungssystem // syro-ai](https://cdn.loom.com/sessions/thumbnails/411dc114edfd4de8aafc3df1e1967fce-with-play.gif)](https://www.loom.com/share/411dc114edfd4de8aafc3df1e1967fce)

> Demo-Video von **Ramy Tichy**, Co-Founder von syro-ai

---

## Was das System macht

Das System liest eine Lead-Liste aus einem Google Sheet, nutzt ein LLM um das jeweilige Unternehmen zu recherchieren und einen personalisierten Icebreaker (2–3 Sätze) zu generieren — und übergibt jeden Lead mit seinem Icebreaker an [Instantly.ai](https://instantly.ai) für den automatischen Versand.

**Ergebnis:** 500+ hochwertige, personalisierte Cold-E-Mails pro Woche — per Knopfdruck, während du schläfst.

---

## Das Problem

Manuelle Cold-Email-Personalisierung skaliert nicht:

- Ein SDR verbringt 5–15 Minuten pro Lead allein für die Recherche
- Die Qualität sinkt, sobald das Volumen steigt
- Menschliche Konsistenz schwankt — gute Tage, schlechte Tage
- Keine einheitliche Vorlage bedeutet keine Möglichkeit, zu messen, was funktioniert

Dieses System ersetzt diesen Flaschenhals durch einen konsistenten, skalierbaren Wachstumsmotor, der täglich dieselbe Qualität und Präzision liefert.

---

## Backend-Workflow (n8n)

```
[Manueller Trigger] → [Google Sheets: Zeilen lesen] → [Loop Over Items (Batch: 50)]
                                                                ↓
                                                    [OpenAI: Icebreaker generieren]
                                                                ↓
                                                    [HTTP Request: POST an Instantly.ai]
```

### Node-Übersicht

| Schritt | Node | Beschreibung |
|---------|------|--------------|
| 1 | **Manueller Trigger** | „Workflow ausführen"-Button — startet die gesamte Pipeline auf Knopfdruck |
| 2 | **Get row(s) in sheet** | Liest Leads aus Google Sheets (unterstützt 1.000+ Zeilen) |
| 3 | **Loop Over Items** | Iteriert durch Leads in 50er-Batches, um API-Limits einzuhalten |
| 4 | **Message a model** | Sendet Unternehmensdaten an ein LLM (OpenAI) — extrahiert relevante Infos, identifiziert den richtigen Ansprechpartner (CMO, Vertriebsleiter, Geschäftsführer) und schreibt einen personalisierten Icebreaker |
| 5 | **HTTP Request** | Übergibt jeden Lead + Icebreaker per POST an die Instantly.ai API für Planung und Versand |

---

## Kernkonzepte

### Icebreaker
Eine 2–3-seitige personalisierte Einleitung, die sich auf etwas Spezifisches über das Unternehmen des Interessenten bezieht. Sie wird vom LLM automatisch auf Basis öffentlich zugänglicher Unternehmensdaten generiert. Genau das lässt die E-Mail handgeschrieben wirken — in großem Maßstab.

### Google Sheets als Lead-Quelle
Das Sheet fungiert als zentrale Datenbasis. Jede Zeile ist ein Lead. Die Spalte `Icebreaker` wird vom System befüllt, bevor der Lead an Instantly weitergegeben wird.

### Instantly.ai-Integration
[Instantly.ai](https://instantly.ai) übernimmt E-Mail-Versand, Postfach-Aufwärmung, Inbox-Rotation und Zustellbarkeit. Der n8n-Workflow übergibt Leads über die Instantly-API direkt in eine Kampagne.

---

## Ausführung

1. Den n8n-Workflow öffnen
2. Sicherstellen, dass das Google Sheet verbunden und mit Leads befüllt ist
3. **„Workflow ausführen"** klicken
4. Das System läuft im Hintergrund — neue Leads erscheinen automatisch in der Instantly-Kampagne

Nach dem Trigger ist kein manueller Eingriff erforderlich. Das System übernimmt Recherche, Personalisierung und Übergabe vollständig.

---

## Tech Stack

| Tool | Funktion |
|------|----------|
| **n8n** | Workflow-Automatisierung |
| **Google Sheets** | Lead-Datenbank |
| **OpenAI (GPT)** | Icebreaker-Generierung & Unternehmensrecherche |
| **Instantly.ai** | E-Mail-Outreach, Versand und Kampagnenverwaltung |

---

## Datenschutz

Das System ist DSGVO-konform ausgelegt. Stelle sicher, dass deine Lead-Quelle und deine Outreach-Nachrichten den rechtlichen Anforderungen deines Zielmarkts entsprechen, bevor du Kampagnen startest.

---

## Ergebnisse

| Kennzahl | Wert |
|----------|------|
| Lead-Generierung | Per Knopfdruck |
| E-Mails pro Woche | 500+ personalisiert |
| Zeit bis 500 E-Mails | Vor der Mittagspause |
| SDR-Zeitersparnis | 5–15 Min/Lead eliminiert |
| Konsistenz | Täglich gleiche Qualität, unabhängig von der Teamverfügbarkeit |

---

## Über das Projekt

Entwickelt von **Youssef Tayachi**, Gründer von [syro-ai](https://syro-ai.com).  
Demo-Video erstellt von **Ramy Tichy**, Co-Founder von syro-ai.

Dieses System zeigt, was möglich ist, wenn KI die Recherche- und Personalisierungsebene der Kaltakquise übernimmt — und Vertriebsteams sich auf echte Gespräche konzentrieren können, statt auf Copy-Paste.
