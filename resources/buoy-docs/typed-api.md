---
title: "sound typed API"
summary: "Source-derived public signatures, properties, parameters, defaults, and return values."
category: "Reference"
order: 21
types: ["SoundPlayer"]
dependencies: []
symbols: ["SoundPlayer"]
related: ["api.md", "getting-started.md", "index.md"]
---

# sound typed API

Generated from the package source declarations. Platform guards are shown where present; inherited members are documented on the base type. See the [API contracts](api.md) for behavior and limitations.

## Sound functions

### SoundSupported

`Public Function SoundSupported() As Boolean`

No parameters.

#### Returns

| Type |
| --- |
| `Boolean` |

## SoundPlayer

`Public Class SoundPlayer`

### Properties

| Name | Type | Read-Only | Shared | Default | Description |
| --- | --- | --- | --- | --- | --- |
| `Duration` | `Double` | Yes | No | — | — |
| `IsPlaying` | `Boolean` | Yes | No | — | — |

### Constructor

`Public Sub Constructor(file As FileSystemItem)`

#### Parameters

| Name | Type | Passing | Default |
| --- | --- | --- | --- |
| `file` | `FileSystemItem` | `ByVal` | Required |

Returns: no value.

### Play

`Public Function Play() As Boolean`

No parameters.

#### Returns

| Type |
| --- |
| `Boolean` |

### Stop

`Public Sub Stop()`

No parameters.

Returns: no value.

### Close

`Public Sub Close()`

No parameters.

Returns: no value.

### Destructor

`Public Sub Destructor()`

No parameters.

Returns: no value.
