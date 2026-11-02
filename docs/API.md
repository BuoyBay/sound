# Native audio-file playback · 0.1.0

`Import sound`. `New SoundPlayer(file)` loads a local supported audio file without playing it. `Duration` and `IsPlaying` are read-only; `Play()` explicitly starts sound and reports whether NSSound accepted it, `Stop()` stops, and `Close()` is final/idempotent. Creation/controls require the main thread. The player retains its native sound. Worker-thread destruction explicitly queues stop/release on the main thread. No sound plays merely by importing or constructing.

These native operations require macOS; `SoundSupported()` returns False on Windows/Linux, and unsupported operations throw rather than silently emulating an Apple API. All six compiler targets are checked; native execution is verified on macOS arm64.

Inspired by [macoslib’s Cocoa examples](https://github.com/macoslib/macoslib); implemented independently against [Apple’s API](https://developer.apple.com/documentation/appkit/nssound).
