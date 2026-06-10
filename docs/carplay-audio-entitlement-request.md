# CarPlay-Entitlement-Antrag (ShelfPlayer)

**Entitlement:** `com.apple.developer.carplay-audio` (CarPlay **audio** app).

**Antrag stellen:** Das CarPlay-Audio-Entitlement ist **von Apple verwaltet** (kein
Self-Service-Häkchen — es erscheint NICHT in der App-ID-Capability-Liste, bevor Apple es zuweist).
Antragsformular (eingeloggt): **`https://developer.apple.com/contact/carplay/`**
(über `developer.apple.com/carplay/` → *„Request CarPlay app entitlement"*). Dort App-Name +
Bundle-ID (die du tatsächlich signierst, z. B. `atlan.arkon.shelfplayer…`), Kategorie **„Audio"**,
untenstehende Begründung einreichen, CarPlay-Bedingungen zustimmen. Das Entitlement **bindet die
App auf die Kategorie Audio** (Template-Set `com.apple.developer.carplay-audio`). Bearbeitung durch
Apple: keine zugesicherte Frist, Erfahrungswerte wenige Tage bis mehrere Wochen.

**Nach der Freigabe:** Entitlement am App-ID aktivieren → **Provisioning-Profil neu erzeugen** →
in der Build-Config volle Entitlements + `ENABLE_CENTRALIZED` (siehe README unten).

---

## Begründung (English, zum Einreichen)

**App name:** ShelfPlayer

**App category:** Audio

**Description of CarPlay functionality:**

ShelfPlayer is an audiobook and podcast player. It is a client for a self-hosted Audiobookshelf
media server: it streams or plays downloaded audiobooks and podcast episodes, with chapter
navigation, variable playback speed, sleep timer and progress sync back to the server.

On CarPlay it is a hands-free **audio** app built entirely from Apple's CarPlay audio templates:

- A **CPTabBarTemplate** with browsable sections (Listen Now, Library) backed by
  **CPListTemplate**/**CPListItem** lists for libraries, authors, series, audiobooks and podcasts.
- A **CPNowPlayingTemplate** for the current title with play/pause and skip, chapter navigation,
  a playback-rate button and album art, driven by the same playback engine as the phone app and
  the system Now Playing / lock-screen controls (MPNowPlayingInfoCenter / MPRemoteCommandCenter).

CarPlay is appropriate because the app is used while driving: the driver selects a title and
controls playback from the car's built-in display using only Apple's audio templates, with no
custom on-screen UI, keeping attention on the road.

**Why the carplay-audio entitlement:** ShelfPlayer is a pure audio playback app (audiobooks /
podcasts) and uses only the CarPlay audio template set, so it requires the CarPlay **audio**
entitlement to present its browse and Now Playing UI on CarPlay.
