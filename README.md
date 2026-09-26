# SongBox Download

Statische Downloadseite für SongBox-MP3s. Sie lädt eine CORS-fähige MP3 direkt im Browser,
versucht anschließend automatisch den Download und zeigt immer einen Download-Button als Fallback.
Es gibt keinen Server, Proxy oder Upload auf einen weiteren Dienst.

## Lokal testen

Im Repository starten:

```bash
python3 -m http.server 8080
```

Danach `http://localhost:8080` öffnen und eine MP3-URL in das Testformular einfügen. Alternativ
kann direkt ein fertiger Link geöffnet werden:

```text
http://localhost:8080/#url=https%3A%2F%2Fexample.com%2Fsong.mp3&title=Mein+Song
```

Wichtig: Die MP3-Quelle muss Browserzugriffe über CORS erlauben. Die aktuell von Suno API
gelieferten Domains `tempfile.aiquickdraw.com` und `audiostream.api.box` erlauben dies.

## Veröffentlichen

Das Repository kann ohne Build-Schritt auf GitHub Pages oder Cloudflare Pages veröffentlicht
werden. Für QR-Codes sollte die URL im Fragment stehen:

```text
https://DEINE-SEITE.example/#url=URL_ENCODED&title=TITEL_ENCODED
```

Alles hinter `#` wird nur im Browser verarbeitet und nicht als Anfrage an den Seitenhost gesendet.
