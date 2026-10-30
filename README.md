# Port Menu

**localhost, organized.**

A tiny macOS menu bar app that tracks your dev servers across projects.

No config. No setup. It just works.

> **About this fork.** A personal build of [wieandteduard/port-menu](https://github.com/wieandteduard/port-menu) with two changes:
>
> - Dev runtimes that macOS launched with cwd `/` aren't listed, so "Kill all" no longer stops apps like Raycast that bundle `node` (branch `fix/skip-runtimes-launched-by-macos`).
> - Sparkle auto-update is off, because the feed points at upstream releases, which would replace this build. To pick up upstream changes, merge `upstream/main` and rebuild.
>
> Build and install (signed for this Mac only; hardened runtime is off because it rejects the self-signed Sparkle framework): `xcodebuild -project Porter.xcodeproj -scheme Porter -configuration Release -derivedDataPath build/DerivedData CODE_SIGN_IDENTITY=- DEVELOPMENT_TEAM= CODE_SIGN_STYLE=Manual ENABLE_HARDENED_RUNTIME=NO build`, then copy `build/DerivedData/Build/Products/Release/Port Menu.app` to `/Applications`.

---

## What it does

Port Menu sits in your menu bar and automatically detects local development servers running on your machine. One click to see what's running, which project it belongs to, and on which port.

- **Auto-detection** — scans for running dev servers every few seconds
- **Project context** — shows Git repo name, current branch, port, and uptime
- **Kill or open** — stop a server or open it in your browser directly from the menu
- **Copy URL** — right-click to copy the localhost URL

## Download

**[Download for macOS →](https://portmenu.dev)**

Requires macOS 14 (Sonoma) or later.

1. Download and open the DMG
2. Drag `Port Menu.app` into `Applications`
3. Open Port Menu from `Applications`
4. Click the icon in your menu bar to get started

## Build from source

```bash
git clone https://github.com/wieandteduard/port-menu.git
cd Porter
open Porter.xcodeproj
```

Requires Xcode 15+.

## Release

Signed and notarized macOS builds are published on the [GitHub Releases](https://github.com/wieandteduard/port-menu/releases) page.

Maintainers can follow the release process in `docs/releasing.md`.

## Testing

```bash
xcodebuild test -project "Porter.xcodeproj" -scheme "Porter" -destination "platform=macOS"
```

## License

MIT
