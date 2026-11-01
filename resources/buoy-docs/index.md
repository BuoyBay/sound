---
title: "Native audio playback"
summary: "Load and explicitly play an owned local audio file."
category: "Overview"
order: 0
keywords: ["audio", "sound", "playback", "NSSound"]
related: ["getting-started.md", "api.md", "typed-api.md"]
---

# Native audio playback

The `sound` package wraps native `NSSound` playback for a local audio file. Construction loads the file without playing it. Playback begins only when the application calls `Play()`, making it suitable for user-selected previews and sound cues.

## Platform support

Requires macOS. `SoundSupported()` returns False on Windows and Linux; construction on unsupported platforms throws `UnsupportedOperationException`.

## Ownership and lifetime

Create and control the player on the main thread and retain it while playback is active. `Close()` is final and idempotent, stopping and releasing native playback. Worker-thread destruction queues stop/release to the main thread; keep the application loop alive for cleanup. Properties and playback controls reject a closed player.

## Read next

- [Getting started](getting-started.md)
- [API reference](api.md)
