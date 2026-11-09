# SFOS-apps

Unofficial apps for **Sailfish OS 5**, built with the **Jolla Phone 2026** in mind
(aarch64, MediaTek, Sailfish OS 5.2). This repository holds ready-to-install RPM
packages, one folder per app.

> [!WARNING]
> **These apps were made with AI**: Claude (Anthropic) and Grok (xAI), with a human
> testing them on a real Jolla Phone 2026. Some are well used and quite usable, others
> are early or experimental. Expect bugs, rough edges and missing features.
> **Use at your own discretion**: back up anything that matters, and read the notes
> for each app before installing.

The apps are not in the Jolla Store (Harbour), and none of them are affiliated with
Jolla or with the services they connect to.

## Installing

1. Enable **Developer mode** on the phone (Settings → Developer tools), and allow
   **untrusted software** (Settings → Untrusted software) if you install by tapping
   the file.
2. Download the RPM(s) of the app to the phone.
3. Install, either by tapping the file in the file manager, or in a terminal:

   ```
   devel-su pkcon install-local ~/Downloads/harbour-<app>-<version>.aarch64.rpm
   ```

   Install an app and its add-on packages (`-cores`, `-helper`, `-hud`, `-psp`) in
   the same command. To update, install the newer RPMs the same way.

Other phones on Sailfish OS 5 (aarch64) may work too, but the apps are only tested
on the Jolla Phone 2026.

## The apps

| App | What it is | Sailjail |
|---|---|---|
| [Acta](harbour-acta/) | Ampparit.com news headline reader (Finnish news) | Sandboxed: internet, web view |
| [Arena](harbour-arena/) | Game launcher and performance monitor, with game mode and an optional HUD | **Off**: lists Android games |
| [Calor](harbour-calor/) | Adult video catalog client. **18+ only** | Sandboxed: internet, audio |
| [Collegium](harbour-collegium/) | Discord client: servers, direct messages, notifications | Sandboxed: internet, audio, web view, Secrets |
| [Fluxus](harbour-fluxus/) | Stremio add-on client with optional torrent streaming | Sandboxed: internet, audio, memory card |
| [Interpres](harbour-interpres/) | On-device AI translator (Qwen2.5 models, text stays on the phone) | Sandboxed: internet |
| [Ludus](harbour-ludus/) | Classic games player (libretro emulators) with RomM support | **Off**: controllers, games in any folder |
| [Oraculum](harbour-oraculum/) | On-device AI chat (Qwen2.5 models with llama.cpp) | Sandboxed: internet, Documents, Downloads, Pictures |
| [Scintilla](harbour-scintilla/) | Twitch client with chat | Sandboxed: internet, audio, Secrets |
| [Statio](harbour-statio/) | Offline public-transport timetables for Finnish cities | Sandboxed: internet, location |
| [Tabula](harbour-tabula/) | Manga reader (MangaDex) | Sandboxed: internet, Documents, Downloads |
| [Torrens](harbour-torrens/) | Anime catalog (AniList) with optional torrent streaming | Sandboxed: internet, audio, memory card |
| [Tubus](harbour-tubus/) | YouTube client | **Off**: browser session, local proxy |
| [Volatus](harbour-volatus/) | Live flight tracker (ADS-B) on a map | Sandboxed: internet, location |

### Acta
Headlines from Ampparit.com: top stories, most read, most voted and latest, with
category filters and search. Articles open in an in-app web view.

### Arena
Collects native and Android games into one launcher and shows CPU, temperature,
battery and memory while you play, with session reports afterwards. Game mode can
turn on Do Not Disturb, the silent profile, keep the screen on and lock brightness.
- `harbour-arena-helper` (optional): CPU performance and battery-saver profiles
  during games. Runs a small root service.
- `harbour-arena-hud` (optional, needs **Patchmanager**): an on-screen overlay with
  FPS, CPU, GPU, temperature and battery over any app, Android games included.
  Activate "Arena performance HUD" in Patchmanager afterwards.

### Calor
**Adults only (18+).** Browses public catalogs of adult video sites and plays videos
with hardware decoding.

### Collegium
Unofficial Discord client: servers, channels, direct messages, pictures, GIFs,
attachments, replies and notifications. No voice. **Third-party Discord clients are
against Discord's terms of service and can get an account flagged or banned: use it
at your own risk.**

### Fluxus
A client for Stremio add-ons: Cinemeta catalogs, optional Torrentio, and playback of
HTTP or torrent streams with libmpv. Make sure what you stream is legal where you live.

### Interpres
Translates text on the phone with a downloaded Qwen2.5 Instruct model (1.5B or 3B).
Nothing is sent to a server. The model download is large, and translation is slower
than online services.

### Ludus
A player for classic console games with built-in emulators: NES, SNES, Mega Drive,
Master System, Game Gear, Game Boy, Game Boy Color, Game Boy Advance, PC Engine and
PlayStation. Touch controls you can move and resize, Bluetooth controllers, save
states, cheats, box art, and a client for a self-hosted RomM server with save sync.
- `harbour-ludus-cores` (required): the emulators for the classic systems. Install
  it together with `harbour-ludus`:
  ```
  devel-su pkcon install-local harbour-ludus-0.6.0-1.aarch64.rpm harbour-ludus-cores-0.6.0-1.aarch64.rpm
  ```
- `harbour-ludus-psp` (optional): PlayStation Portable support (PPSSPP, GPU rendered).

**No games are included: play only games you own.** Some bundled emulators (snes9x,
Genesis Plus GX) are licensed for non-commercial use only.

### Oraculum
A chat assistant running fully on the phone with llama.cpp and Qwen2.5 Instruct
models. Private and offline, but small models make mistakes and answers take time.

### Scintilla
Unofficial Twitch client: browse and search live channels, hardware-decoded playback
(720p/1080p) and chat. The login token is kept in Sailfish Secrets.

### Statio
Download a city pack (HSL, Nysse, Föli, Waltti cities and more), see nearby stops by
GPS and the next departures offline. Live times need a Digitransit API key of your
own. Not a journey planner or a ticket app.

### Tabula
Browse and search MangaDex, keep a library, download chapters and read them.

### Torrens
Browse anime from AniList. With an optional torrent source pack it plays torrent
streams on the phone (libtorrent + libmpv with software HEVC decoding). Make sure what
you stream is legal where you live.

### Tubus
Unofficial YouTube client: home, Shorts, channels, playlists, history and downloads.
Can use the YouTube session from the Sailfish Browser. yt-dlp is optional (downloaded
from Settings, not bundled).

### Volatus
Nearby aircraft on an OpenStreetMap view from community ADS-B data (adsb.lol, with
OpenSky Network as a fallback): details, routes, search, favourites and emergency
squawks. **Not for navigation.**

## Notes

- Apps marked unofficial use public or undocumented interfaces of the services they
  connect to. They can stop working whenever those services change.
- **Sailjail** is the Sailfish OS app sandbox. Most apps run inside it with only the
  permissions in the table above. Arena, Ludus and Tubus turn it off: Arena to list
  and launch Android games, Ludus to read game controllers and games from any folder,
  Tubus to use the Sailfish Browser's YouTube session and a local playback proxy.
  Outside the sandbox an app can read and write all your files.
- These are RPM packages only; no source code is in this repository.

## Source code

The apps are **source-available**: every RPM here has a matching source RPM
(`.src.rpm`), attached to this repository's
[releases](https://github.com/ahjolinna/SFOS-apps/releases). A source RPM contains
the app's code, the shared code it uses, and the sources of the third-party
libraries and emulators it bundles, so it rebuilds on its own in the Sailfish OS
SDK:

```
rpmbuild --rebuild harbour-<app>-<version>-1.src.rpm
```

The third-party parts keep their own licences (GPL, LGPL, MPL, and the
non-commercial licences of snes9x and Genesis Plus GX); see each package.
