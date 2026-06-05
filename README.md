# Automatisiertes Personalisiertes Leadgenerierungssystem - syro-ai

Cold-Email-Personalisierung auf Knopfdruck. Das System übernimmt die komplette Recherche und schreibt für jeden Lead eine individuelle E-Mail-Einleitung — automatisch, konsistent, skalierbar.

## System-Erklärung

Co-Founder Ramy Tichy erklärt und zeigt in diesem 6-minütigen Video das gesamte System - vom Icebreaker bis zum fertigen E-Mail-Versand:

[![Automatisiertes Personalisiertes Leadgenerierungssystem // syro-ai](https://cdn.loom.com/sessions/thumbnails/411dc114edfd4de8aafc3df1e1967fce-with-play.gif)](https://www.loom.com/share/411dc114edfd4de8aafc3df1e1967fce)

## Das Problem mit manueller Personalisierung

Personalisierung ist der entscheidende Faktor in der Kaltakquise, aber sie skaliert nicht:

- Ein SDR verbringt 5-15 Minuten pro Lead allein für die Recherche
- Bei steigendem Volumen sinkt die Qualität zwangsläufig
- Inkonsistenz macht es unmöglich zu messen, was wirklich funktioniert

Teams müssen zwischen Qualität und Volumen wählen. Dieses System macht diesen Kompromiss überflüssig.

## Die Lösung: Automatisierte Personalisierung

Das System analysiert für jeden Lead das jeweilige Unternehmen, identifiziert die richtige Ansprechperson (Marketingleiter, Vertriebsleiter, Geschäftsführer) und generiert automatisch einen personalisierten Icebreaker - 2 bis 3 Sätze, die sich direkt auf das Unternehmen beziehen.

Diese Einleitung wird als Einstieg in jede Cold-E-Mail eingebettet. E-Mails, die sich handgeschrieben anfühlen - bei hunderten oder tausenden Leads gleichzeitig.

**500+ personalisierte E-Mails pro Woche. Vor der Mittagspause.**

## Backend-Workflow (n8n)

```
[Manueller Trigger] → [Google Sheets: Zeilen lesen] → [Loop Over Items (Batch: 50)]
                                                                ↓
                                                    [OpenAI: Icebreaker generieren]
                                                                ↓
                                                    [HTTP Request: POST an Instantly.ai]
```

| Schritt | Node | Beschreibung |
|---------|------|--------------|
| 1 | **Manueller Trigger** | Startet die gesamte Pipeline per Knopfdruck |
| 2 | **Get row(s) in sheet** | Liest die Lead-Liste aus Google Sheets |
| 3 | **Loop Over Items** | Verarbeitet Leads in 50er-Batches |
| 4 | **Message a model** | Sendet Unternehmensdaten an OpenAI, recherchiert, findet den richtigen Kontakt und schreibt den personalisierten Icebreaker |
| 5 | **HTTP Request** | Übergibt Lead + Icebreaker an Instantly.ai für den automatischen E-Mail-Versand |

## Tech Stack

| Tool | Funktion |
|------|----------|
| **n8n** | Workflow-Automatisierung |
| **Google Sheets** | Lead-Datenbank |
| **OpenAI (GPT)** | Personalisierung & Unternehmensrecherche |
| **Instantly.ai** | E-Mail-Versand und Kampagnenverwaltung |

## Über das Projekt

Dieses System ist eine von mehreren Automatisierungen, die **Youssef Tayachi**, Gründer von [syro-ai](https://syro-ai.com), entwickelt hat. syro-ai hat mit diesem System nicht nur selbst erfolgreich Kunden gewonnen, sondern hilft damit auch anderen Unternehmen, ihre Leadgenerierung zu automatisieren und zu skalieren.

Demo-Video erstellt von **Ramy Tichy**, Co-Founder von syro-ai.
