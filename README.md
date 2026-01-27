# Cindy_S_Kommunale_Messstellen

Dieses Projekt wurde geschaffen von Matthias Lochmann, HLNUG.
Ziel ist es, Daten von kommunalen Fluglärm-Messstellen zu analysieren.
Fokus sind Maximalpegelverteilungen.

# Technische Vorbereitung zur Verwendung dieses Projektes

## DuckDB: ICU-Extension für Zeitzonen (Firmenrechner / Proxy)

Für die Verwendung von `TIMESTAMPTZ` und `AT TIME ZONE 'Europe/Berlin'` benötigt DuckDB
die **ICU-Extension**.  
Auf Firmenrechnern mit Proxy schlägt der automatische Download oft fehl.
Diese Anleitung beschreibt eine **vollständig offline-fähige Lösung**.

---

### 1. Verzeichnisstruktur anlegen

Im Projekt-Root diese Ordner anlegen:

`duckdb_extensions/v1.4.3/windows_amd64_mingw/`
**Wichtig**
> - Version (`v1.4.3`) und Plattform müssen zur DuckDB-Version passen

---

### 2. ICU-Extension manuell herunterladen (einmalig)

Im Browser (nicht aus R):

https://extensions.duckdb.org/v1.4.3/windows_amd64_mingw/icu.duckdb_extension.gz


Datei entpacken und in das oben genannte Verzeichnis kopieren. Die Datei muss
`icu.duckdb_extension`
heißen. Die Datei muss **entpackt** sein (kein `.gz`).


---

### 3. DuckDB mit Extension-Pfad starten (R)

Der Extension-Pfad **muss beim dbConnect() gesetzt werden**.
Umgebungsvariablen wie `DUCKDB_EXTENSION_PATH` sind im R-Binding nicht zuverlässig. Sollte im Code berücksichtigt sein.