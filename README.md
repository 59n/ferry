<p align="center">
  <img src="./assets/ferry-icon.png" alt="Ferry" width="128">
</p>

# Ferry

A macOS menu-bar app that backs up your Apple Photos library and chosen folders to an [Immich](https://immich.app) server, to a date-organised folder, or both. This repository holds Ferry's releases, update feed and issue tracker.

<p align="center">
  <img src="./assets/ferry-settings.png" alt="Ferry's settings" width="760">
</p>

Each backup only adds what's missing: anything already on the server, whether Ferry, the Immich phone app or anything else put it there, is recognised by its checksum and never uploaded twice.

Ferry is a Rust and Tauri rewrite of [ImmiBridge](https://github.com/emerysilb/immibridge) by Emery Silberman: a ~10 MB app instead of a SwiftUI one, and compatible with everything ImmiBridge already backed up.

## Features
- Back up Photos and folders to Immich, a folder, or both.
- Never re-uploads: SHA-1 checks against the server, and fingerprints remembered between runs so later backups read only new or edited photos from Photos.
- Never deletes from Immich. The one opt-in exception, replacing photos you edited since they were uploaded (Immich v2), uploads the new version before trashing the old one.
- Backup modes: Smart incremental, Full, and Mirror (moves what you deleted from Photos out of the backup folder into the Trash; never touches Immich).
- Albums, favourites, locations and keywords kept in step with Immich.
- Live Photos, edited versions, hidden photos, date ranges and selected albums.
- iCloud originals downloaded as needed, with progress.
- Pause and resume, even across restarts; dry runs.
- Schedules (every few hours, or daily at a time) with catch-up after sleep.
- Light and dark themes, notifications and self-updates.
- Import of settings from ImmiBridge.

## Tech stack
- Rust and Tauri
- Apple silicon macOS builds

## Getting started

### Install
1. Download `Ferry-<version>.zip` from the [latest release](../../releases/latest), unzip it and move Ferry.app to Applications. Builds are for Apple silicon.
2. Builds aren't notarized: the first time, right-click Ferry.app and choose Open.
3. Click the ferry in the menu bar, then Open Settings. Choose what to back up and where, and enter your Immich server address and an API key (Immich, Account Settings, API Keys).

Ferry updates itself: Settings, General, Check now.

### Coming from ImmiBridge
Settings, General, Import... brings over your choices, schedule and ImmiBridge's Immich device id, so earlier uploads are recognised. macOS protects other apps' data: if the import asks for it, give Ferry Full Disk Access for the import (there's a button) and turn it off afterwards. The API key has to be entered again, because ImmiBridge kept it in the Keychain.

### Permissions
- Photos: to read your library.
- Local Network: if your Immich server is on your network.
- Automation (Photos): only for keywords. Apple offers no other way to read them, so Ferry starts Photos hidden and quits it again. Turn off Immich, Keywords as tags and Photos is never opened.

To change a permission later: System Settings, Privacy & Security.

### Immich versions
Ferry works with Immich v2 and v3. Every release is tested against real Immich servers, currently v2.5.6 through v3.3.3, and new Immich releases are tested weekly.

## Project structure
```
assets/              Icon and screenshot used in this README
LICENSE-ImmiBridge   License of the ImmiBridge code Ferry builds on
```

Builds and the update feed are published as [GitHub releases](../../releases). Ferry is closed source for now while it is tested on real libraries; the source is planned to be published here once it is ready. If something goes wrong, [open an issue](../../issues).

## Status
Active, early releases (0.1.x).

## License
Ferry builds on [ImmiBridge](https://github.com/emerysilb/immibridge), (c) 2025 Emery Silberman, used under the MIT License: see [LICENSE-ImmiBridge](LICENSE-ImmiBridge). Ferry's own license will come with its source.
