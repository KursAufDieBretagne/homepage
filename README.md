# Kurs auf die Bretagne – Homepage

Quellcode der Website [kurs-bretagne.de](https://kurs-bretagne.de) des Vereins "Kurs auf die Bretagne (e.V.)" für einen gelebten Kulturaustausch zwischen Stralsund & Saint-Malo.

---

## Technologie

- **Static Site Generator:** [Hugo](https://gohugo.io/) (v0.102.3)
- **Theme:** [Mainroad](https://github.com/Vimux/Mainroad)
- **Hosting:** GitHub Pages
- **Deployment:** automatisch via GitHub Actions bei jedem Push auf `main`
- **Sprachen:** Deutsch (`de`) und Französisch (`fr`)

## Projektstruktur

```
homepage/
├── .github/workflows/hugo.yml   # CI/CD-Pipeline (automatisches Deployment)
├── .gitmodules                   # Hugo-Themes als Git-Submodule
└── verein-website/               # Das eigentliche Hugo-Projekt
    ├── config.toml               # Seiteneinstellungen, Menüs, Sprachen
    ├── archetypes/               # Vorlagen für neue Inhalte
    │   ├── default.md            # Standardvorlage (Blogposts)
    │   ├── events.md             # Vorlage für Termine
    │   └── impressionen.md       # Vorlage für Impressionen (Galerie & Videos)
    ├── content/
    │   ├── de/                   # Deutsche Inhalte
    │   │   ├── blog/             # Blogbeiträge (Aktuelles)
    │   │   ├── events/           # Termine
    │   │   └── impressionen/     # Fotos & YouTube-Videos
    │   └── fr/                   # Französische Inhalte
    │       ├── blog/
    │       ├── events/
    │       └── impressionen/
    ├── layouts/
    │   └── shortcodes/           # Custom Shortcodes (youtube, gallery, photo, ...)
    ├── static/                   # Bilder (img/), CSS, statische Dateien
    └── themes/                   # Hugo-Themes (als Submodule)
```

---

## Lokale Entwicklung

### Voraussetzungen

- [Hugo](https://gohugo.io/installation/) (Extended Edition, Version 0.102.3)
- [Git](https://git-scm.com/)

### Repository klonen

```bash
git clone --recurse-submodules https://github.com/<org>/homepage.git
cd homepage
```

> **Wichtig:** `--recurse-submodules` ist notwendig, damit das Theme (Mainroad) mitgeladen wird.
> Falls das Theme fehlt: `git submodule update --init --recursive`

### Entwicklungsserver starten

```bash
cd verein-website
hugo server -D
```

Die Website ist dann unter [http://localhost:1313](http://localhost:1313) erreichbar.  
Die Option `-D` zeigt auch Entwürfe (`draft: true`) an.

---

## Deployment

Das Deployment erfolgt **vollautomatisch**: Jeder Push auf den `main`-Branch löst via GitHub Actions den Build aus und veröffentlicht die Seite auf GitHub Pages unter [kurs-bretagne.de](https://kurs-bretagne.de).

Manuell deployen ist nicht notwendig. Workflow-Datei: [`.github/workflows/hugo.yml`](.github/workflows/hugo.yml)

---

## Neuen Content erstellen

### Blogpost (Aktuelles) erstellen

Blogposts erscheinen unter dem Menüpunkt **„Aktuelles"** auf der deutschen Seite (bzw. „Actualités" auf Französisch).

**Option A – Mit Hugo CLI (empfohlen):**

```bash
cd verein-website
hugo new content/de/blog/mein-thema.md
```

**Option B – Datei manuell anlegen:**

Neue Datei in `verein-website/content/de/blog/` erstellen, z. B. `sommerfest-2026.md`:

```markdown
---
title: Sommerfest 2026
date: 2026-06-01
draft: false
translationKey: sommerfest-2026
---

Kurze Einleitung, die in der Übersicht angezeigt wird.

<!--more-->

Vollständiger Beitragstext hier ...
```

**Wichtige Felder im Front Matter:**

| Feld | Bedeutung |
|---|---|
| `title` | Titel des Beitrags |
| `date` | Veröffentlichungsdatum (YYYY-MM-DD) |
| `draft` | `true` = Entwurf (nicht live), `false` = veröffentlicht |
| `translationKey` | Verknüpft den deutschen mit dem französischen Beitrag (gleicher Wert in beiden Sprachdateien) |

**Tipp:** `<!--more-->` trennt die Teasertext (wird in der Übersicht gezeigt) vom vollen Inhalt.

---

### Termin (Event) erstellen

Termine erscheinen unter dem Menüpunkt **„Termine"** (bzw. „Événements").

**Option A – Mit Hugo CLI:**

```bash
cd verein-website
hugo new --kind events content/de/events/mein-termin.md
```

**Option B – Datei manuell anlegen:**

Neue Datei in `verein-website/content/de/events/` erstellen, z. B. `herbsttreffen-2026.md`:

```markdown
---
title: Herbsttreffen 2026
date: 2026-09-01
draft: false
eventDate: "2026-10-15T18:00:00"
location: "KulturDIELE M8, Mönchstr. 8, 18439 Stralsund"
translationKey: herbsttreffen-2026
---

Kurze Beschreibung des Termins.

<!--more-->

Ausführliche Informationen zum Ablauf, Programm, Anmeldung etc.
```

**Wichtige Felder im Front Matter:**

| Feld | Bedeutung |
|---|---|
| `title` | Name des Termins |
| `date` | Datum der Erstellung/Veröffentlichung |
| `draft` | `true` = Entwurf, `false` = sichtbar |
| `eventDate` | **Tatsächliches Datum des Events** (ISO 8601: `YYYY-MM-DDTHH:MM:SS`) |
| `location` | Veranstaltungsort |
| `translationKey` | Verknüpft mit der französischen Version des Termins |

---

### Impressionen (Fotos & YouTube-Videos) erstellen

Impressionen erscheinen unter dem Hauptmenüpunkt **„Impressionen"** (bzw. „Impressions").

**Neuen Impressionen-Beitrag mit Hugo CLI erstellen:**

```bash
cd verein-website
hugo new --kind impressionen content/de/impressionen/mein-event.md
```

**Custom Shortcodes für Medien:**

1. **Galerie-Grid (`gallery`):**
   ```markdown
   {{< gallery cols="2" >}}
   ... Medien-Shortcodes ...
   {{< /gallery >}}
   ```

2. **YouTube-Video einbinden (`youtube`):** (DSGVO-konform via `youtube-nocookie.com`)
   ```markdown
   {{< youtube id="YOUTUBE_VIDEO_ID_ODER_URL" title="Video Titel" caption="Kurze Beschreibung" >}}
   ```

3. **Foto-Karte einbinden (`photo`):**
   ```markdown
   {{< photo src="/img/impressionen/mein-bild.jpg" title="Foto Titel" caption="Kurze Beschreibung" >}}
   ```

4. **Instagram-Beitrag einbinden (`instagram`):**
   ```markdown
   {{< instagram url="https://www.instagram.com/p/BEITRAGS_ID/" title="Instagram Titel" caption="Kurze Beschreibung" mode="card" image="/img/impressionen/preview.jpg" >}}
   ```
   *Optionen:* `mode="embed"` für ein direktes Embed-Iframe oder `mode="card"` (empfohlen für DSGVO-Freiheit mit Vorschaubild und direktem Link zum Instagram-Profil/Beitrag).

---

### Zweisprachige Inhalte (DE + FR)

Alle Inhalte können in beiden Sprachen angelegt werden. Die Verknüpfung erfolgt über das Feld `translationKey` im Front Matter – beide Sprachversionen müssen **denselben Wert** haben.

**Beispiel:**

`content/de/blog/sommerfest-2026.md`:
```yaml
translationKey: sommerfest-2026
```

`content/fr/blog/fete-ete-2026.md`:
```yaml
translationKey: sommerfest-2026
```

*Hinweis zur manuellen Übersetzung (DE/FR):*
Aktuell ist die Anzeige der manuellen französischen Inhalte in der Sidebar deaktiviert, da stattdessen das Google Translate Widget genutzt wird. Die französischen Inhalte (`content/fr/`) sind weiterhin vorhanden.

Um den manuellen Sprachumschalter in der Sidebar wieder zu aktivieren, füge in der Datei `verein-website/config.toml` das Widget `"languages"` wieder der Liste hinzu:

```toml
[params.sidebar]
  widgets = ["search", "recent", "languages"]
```

---

### Bilder einbinden

Bilder kommen in den Ordner `verein-website/static/img/` und werden im Markdown so eingebunden:

```markdown
![Bildbeschreibung](/img/mein-bild.jpg)
```

---

## Veröffentlichen

1. Dateien erstellen/bearbeiten (siehe oben)
2. `draft: false` setzen
3. Änderungen committen und auf `main` pushen:

```bash
git add .
git commit -m "Neuer Blogpost: Sommerfest 2026"
git push origin main
```

GitHub Actions baut die Seite automatisch und veröffentlicht sie innerhalb weniger Minuten.

---

## Lizenz

Dieses Projekt steht unter der [GPL-3.0 License](LICENSE).
