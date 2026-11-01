---
title: "Native audio playback API"
summary: "Public symbols and contracts for the sound package."
category: "Reference"
order: 20
keywords: ["audio", "sound", "playback", "NSSound"]
symbols: ["SoundSupported", "SoundPlayer", "SoundPlayer.Duration", "SoundPlayer.IsPlaying", "SoundPlayer.Play", "SoundPlayer.Stop", "SoundPlayer.Close"]
related: ["index.md", "getting-started.md", "typed-api.md"]
---

# API reference

Import `sound` from the sealed package. The signatures below describe its public surface.

| Symbol | Contract |
| --- | --- |
| `SoundSupported() As Boolean` | Report native platform support. |
| `New SoundPlayer(file As FileSystemItem)` | Load an existing supported local file without playing. |
| `Duration As Double` | Read-only duration in seconds; requires an open player. |
| `IsPlaying As Boolean` | Read-only native playback observation; requires an open player. |
| `Play() As Boolean` | Start playback explicitly and report native acceptance. |
| `Stop()` | Stop playback; requires an open player. |
| `Close()` | Stop/release playback and permanently close the player. |

## Errors and lifecycle

The file must be non-Nil, exist locally, and have a supported audio format; invalid inputs throw `InvalidArgumentException`. `Duration` is measured in seconds. Native acceptance of `Play()` does not report end-of-playback completion or ensure the output device is audible. Constructing or importing the package never plays sound.

Create and control the player on the main thread and retain it while playback is active. `Close()` is final and idempotent, stopping and releasing native playback. Worker-thread destruction queues stop/release to the main thread; keep the application loop alive for cleanup. Properties and playback controls reject a closed player.

## Platform support

Requires macOS. `SoundSupported()` returns False on Windows and Linux; construction on unsupported platforms throws `UnsupportedOperationException`.

[Getting started](getting-started.md) · [Package overview](index.md)


[Full typed API: properties, parameters, defaults, and returns](typed-api.md)
