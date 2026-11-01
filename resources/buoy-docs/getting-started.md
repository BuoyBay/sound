---
title: "Native audio playback getting started"
summary: "Install sound and use its native API with explicit ownership."
category: "Guides"
order: 10
keywords: ["audio", "sound", "playback", "NSSound"]
related: ["index.md", "api.md", "typed-api.md"]
---

# Getting started

Copy the sealed `sound` package into `packages/` and import it. This helper opens the file without playing it. Keep the returned player in your UI owner, call `Play()` only for a user-requested action, and close it when the owner closes. Check the Boolean from `Play()` to learn whether the native backend accepted playback.

```buoy
Import sound

Function LoadAudio(file As FileSystemItem) As SoundPlayer
    If Not SoundSupported() Then Throw New UnsupportedOperationException("Native sound requires macOS")
    Return New SoundPlayer(file)
End Function
```

## Handle native constraints

The file must be non-Nil, exist locally, and have a supported audio format; invalid inputs throw `InvalidArgumentException`. `Duration` is measured in seconds. Native acceptance of `Play()` does not report end-of-playback completion or ensure the output device is audible. Constructing or importing the package never plays sound.

[Package overview](index.md) · [API reference](api.md)
