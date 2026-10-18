# Ferry

Ferry backs up Apple Photos (and folders) to an [Immich](https://immich.app) server and/or a
folder, from the macOS menu bar. Each backup only adds what's missing: anything already on the
server is recognised by its checksum and never uploaded twice.

This repository holds the builds. Ferry updates itself from here (Settings → General → Check now).

## Install

Download `Ferry-<version>.zip` from the [latest release](../../releases/latest), unzip it and move
`Ferry.app` to Applications. Builds are for Apple silicon, and aren't notarized: the first time,
right-click Ferry.app → Open.

Every release is tested against the Immich versions it lists in its notes, back to v2.5.6.
