# AniTV updates

Official Windows installer releases for AniTV.

## Download

Use the **[Releases page](https://github.com/siddhesh-69/AniTV-updates/releases)** to download a published `AniTV-Setup.msi`.

The first updater-enabled installer is being prepared. There is no downloadable release yet.

## App updates

Updater-enabled versions check this repository in the background when the app opens. When a newer stable release is verified, AniTV requires the update before playback can continue. The app shows download progress, verifies the installer, then opens the standard Windows installer. Windows installation consent still applies.

Older installations need the first updater-enabled installer installed manually. Creating this repository alone does not add updating to older installations.

## Release contract

Each stable release must contain both assets before publication:

- `AniTV-Setup.msi` — the Windows installer with the same ProductVersion as the release.
- `update.json` — a manifest containing `version`, `asset`, `size`, and `sha256`.

Use the tag `vX.Y.Z`, with `asset` set to `AniTV-Setup.msi`, `size` set to the installer's byte length, and `sha256` set to its lowercase SHA-256 digest. The version must match the tag and MSI ProductVersion. AniTV ignores drafts and prereleases.

Prepare and test the installer in the private/local development workspace, then use its `publish-update.ps1 -Version X.Y.Z -Publish` script. It uploads both files to a draft, verifies the uploaded assets, and only then publishes the release as latest. Publishing a newer stable version makes it required for updater-enabled clients.

Never replace a published installer's bytes or reuse its version. Publish a newer version for fixes.

This repository is for release information and installer assets. Do not commit app user data, credentials, development caches, or the private application source.
