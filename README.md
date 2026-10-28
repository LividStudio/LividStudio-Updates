# LividStudio-Updates

Official public update distribution for **Livid Studio**, a Windows video editor. This repository is for approved installers and update metadata, **not private source code**.

## Release channels

| Channel | Tag | GitHub release | Required assets |
| --- | --- | --- | --- |
| Official (stable) | `vX.Y.Z` | Normal release | `LividStudio-X.Y.Z-Setup.exe` and `LividStudio-X.Y.Z-Setup.exe.sha256` |
| Dev | `vX.Y.Z-dev` | Prerelease | `LividStudio-X.Y.Z-dev-Setup.exe` and its matching `.sha256` |

Official and Dev must remain separately installed and only receive their own channel. **Nothing is promoted to Official without owner approval.**

## Before publishing Official

1. Build the actual Windows Official installer against the stable app identity and installation path; do **not** simply rename or upload a Dev ZIP.
2. Validate startup, all six workspaces, saving and reopening projects, original media, Undo/Redo, video/audio playback, rendered exports, clean upgrade and rollback.
3. Sign the installer with the approved Windows publisher certificate. Validate the Authenticode signature and app-pinned publisher, and generate the matching SHA-256 checksum.
4. Publish the signed EXE and checksum together as a **normal GitHub Release**, using a higher version than the installed Official build. Include accurate release notes.
5. Verify the Official updater can securely check the release, display the popup and complete the install while preserving user projects.

**Never** publish API tokens, source ZIPs, secret keys, internal test files, personal data or unverified installers.

## Certificate error diagnosis

`SSL: CERTIFICATE_VERIFY_FAILED: unable to get issuer certificate` is a TLS trust-chain failure on the installed app or machine. Making this repository public does not fix certificate trust. Verify Windows root/intermediate certificates and Python's bundled CA configuration; do **not** disable SSL verification.

[View Official releases](https://github.com/LividStudio/LividStudio-Updates/releases)
