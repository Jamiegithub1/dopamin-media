# Instagram-Workflow für @dopamin.mind.reset

Dieses Repo ist nur eine kurzlebige Ablage, damit Instagram Videos per öffentlichem Link abholen kann. Es soll fast immer leer sein.

## Zugang
- Instagram: `graph.instagram.com` (Token setzt der Proxy ein), Konto-ID in `INSTAGRAM_USER_ID`.
- Facebook-Seite: `graph.facebook.com`, Seiten-ID in `FACEBOOK_PAGE_ID`. Seitenbeiträge und Seiten-Insights brauchen den Seiten-Token: über `GET /me/accounts?fields=access_token` holen und als `access_token` mitschicken.
- Meta-App `dopamin.mind.reset` (ID 1640279707283417) ist veröffentlicht (Live). Datenschutzerklärung als öffentliches Google Doc in Drive „Dopamin-Projekt/05 Orga“.

## Reel posten
1. Video erst direkt vor dem Posten hochladen, unter einem zufälligen, nicht erratbaren Namen (z. B. `reels/<uuid>.mp4`), auf `main` pushen.
2. Container anlegen: `POST /{INSTAGRAM_USER_ID}/media` mit `media_type=REELS`, `video_url=https://raw.githubusercontent.com/jamiegithub1/dopamin-media/main/reels/<uuid>.mp4`, `caption`.
3. `status_code` abfragen, bis `FINISHED`.
4. `POST /{INSTAGRAM_USER_ID}/media_publish` mit `creation_id`.
5. Sofort danach das Video aus dem Repo entfernen, auch aus dem Verlauf (Orphan-Commit nur mit README und CLAUDE.md, Force-Push auf `main`).

Bilder genauso, mit `image_url` statt `video_url`.

## Regeln
- Echte Beiträge nur nach Jamies Freigabe posten. Löschen per Schnittstelle geht bei Instagram nicht, nur in der App.
- Keine Rohfassungen oder unfertigen Videos ins Repo legen.
- Video-Links von Facebook (fbcdn) und Googles Beispiel-Buckets nimmt Instagram nicht an; raw.githubusercontent.com funktioniert.
- Reels: Hochformat 1080×1920, H.264 + AAC, mindestens 3 Sekunden.
