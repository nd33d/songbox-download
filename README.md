# SongBox Download

Statische Downloadseite für SongBox-MP3s. Sie lädt eine CORS-fähige MP3 direkt im Browser,
versucht anschließend automatisch den Download und zeigt immer einen Download-Button als Fallback.
Es gibt keinen Server, Proxy oder Upload auf einen weiteren Dienst.

## Lokal testen

Im Repository starten:

```bash
python3 -m http.server 8080
```

Danach einen vollständigen Link mit den gleichen Parametern öffnen, die später im QR-Code stehen:

```text
http://localhost:8080/#url=https%3A%2F%2Fexample.com%2Fsong.mp3&title=Mein+Song
```

Wichtig: Die MP3-Quelle muss Browserzugriffe über CORS erlauben. Die aktuell von Suno API
gelieferten Domains `tempfile.aiquickdraw.com` und `audiostream.api.box` erlauben dies.

Aus Sicherheitsgründen akzeptiert die Seite ausschließlich UUID-basierte MP3-Pfade dieser beiden
Domains. Die Antwort muss den MIME-Typ `audio/mpeg` oder `audio/mp3` tragen und darf höchstens
30 MiB groß sein. Das Größenlimit wird vor und während des Downloads geprüft.

## Veröffentlichen

Das Repository kann ohne Build-Schritt auf GitHub Pages oder Cloudflare Pages veröffentlicht
werden. Für QR-Codes sollte die URL im Fragment stehen:

```text
https://DEINE-SEITE.example/#url=URL_ENCODED&title=TITEL_ENCODED
```

Alles hinter `#` wird nur im Browser verarbeitet und nicht als Anfrage an den Seitenhost gesendet.
Ein Aufruf ohne vollständige Parameter zeigt bewusst nur einen neutralen Fehlerhinweis; die Seite
besitzt keine Eingabefelder für beliebige URLs.
