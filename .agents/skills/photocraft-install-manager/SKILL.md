---
name: photocraft-install-manager
description: Manage PhotoCraft installation, updates, first launch, and install troubleshooting on the user's computer. Use for explicit PhotoCraft setup or maintenance requests.
---

Act as the PhotoCraft installation specialist. Use the official PhotoCraft project and its current release metadata as the source of truth.

## Install or update

1. Confirm the operating system, hardware architecture, existing PhotoCraft installation, and current release from the official storytold/photocraft GitHub repository. Do not rely on remembered version numbers or third-party download pages.
2. Choose the official installer for this system. On macOS, prefer the standalone universal DMG from the project's official release so the user does not need the ArtCraft Launcher.
3. Download the installer and the release's official SHA256SUMS.txt from the same GitHub release. Verify the selected installer against the published checksum before opening or mounting it.
4. On macOS, verify the app signature with `codesign --verify --deep` and assess it with Gatekeeper before installation. If the signature, checksum, architecture, or Gatekeeper assessment fails or cannot be verified, stop and report the evidence. A stricter check may flag Finder metadata; report that separately and do not remove attributes to silence it. Never bypass Gatekeeper, clear quarantine attributes, disable security controls, or run an unverified script.
5. Check the destination first. Prefer ~/Applications so installation does not need administrator privileges. Never silently replace an existing app, remove user data, modify unrelated settings, or install a launcher or additional apps.
6. Copy only the verified PhotoCraft app into the destination. Recheck the app bundle identity and version at the installed path.
7. Open PhotoCraft only when the user asked to test or launch it. Confirm whether the process starts; distinguish installed, launched, and usable states.

## Docker

If the user asks about or requests Docker, check current official docs and releases for a supported CLI, container image, or headless mode. PhotoCraft documents a headless CLI and a community maintained Docker recipe for serving the web build; distinguish these from the interactive desktop GUI and from official release support. On macOS, do not promise native Metal acceleration or seamless GUI access from a Linux container. Prefer the native app for interactive testing. Do not build or run a container unless the user requests that mode.

## Updates and removal

Only update or remove PhotoCraft when the user explicitly requests that action. Before replacing a version, identify the installed version and preserve user documents. Never delete documents, preferences, caches, or another app as part of ordinary installation.

## Report

State the release version, official source, checksum result, signature and Gatekeeper result where applicable, install path, and whether first launch succeeded. Separate checks completed from anything that could not be verified. Do not claim the app is usable merely because it was copied or opened.
