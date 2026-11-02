# Play local audio with explicit native lifetimes

`Import sound`. `New SoundPlayer(file)` loads a local supported audio file without playing it. `Duration` and `IsPlaying` are read-only; `Play()` explicitly starts sound and reports whether NSSound accepted it, `Stop()` stops, and `Close()` is final/idempotent. Creation/controls require the main thread. The player retains its native sound. Worker-thread destruction explicitly queues stop/release on the main thread. No sound plays merely by importing or constructing.

These native operations require macOS; `SoundSupported()` returns False on Windows/Linux, and unsupported operations throw rather than silently emulating an Apple API. All six compiler targets are checked; native execution is verified on macOS arm64.

## Install

From a Buoy consumer project with BPM installed:

```sh
bpm add sound --git https://github.com/BuoyBay/sound.git --rev refs/heads/main
```

BPM records the resolved commit in its lockfile. Keep that lockfile with the
consumer project for reproducible installs.

## Example

```buoy
Import sound

Function LoadAudio(file As FileSystemItem) As SoundPlayer
    If Not SoundSupported() Then Throw New UnsupportedOperationException("Native sound requires macOS")
    Return New SoundPlayer(file)
End Function
```

## Build from source

With the native `build-packages` driver from [devtools](https://github.com/BuoyBay/devtools)
on your `PATH`, run from this checkout:

```sh
build-packages --root "$PWD" --compile-consumer sound
```

The driver checks source targets and compiles an import consumer. See the
[API guide](docs/API.md) for behavior, limits and any host prerequisites.

## Local Buoy setup

On your own machine, install Buoy and run:

```sh
buoy ai init --both
```

## Contributing

[Contributing](CONTRIBUTING.md) · [License](LICENSE)
