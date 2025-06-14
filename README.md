# yaccfe

**yaccfe** is a minimalist Android frontend for a heavily optimized, custom-built fork of `ccminer Verushash2.2 v3.8.3`, targeting a wide range of ARM CPUs. It’s not a generic miner application — it’s a focused, high-performance wrapper around a locked-in mining core.

---

## TL;DR

A lean, no-frills Android frontend for a custom ARM-optimized `ccminer` build. One pool, one purpose — squeeze every hash out of your ARM chip.

https://github.com/user-attachments/assets/91138b7a-4d97-410a-b5b1-72e101c39bdc

---

## Why

* Built as a fun benchmarking project
* Needed full control over ARM optimizations
* Custom build pipeline for fine-tuned control
* Targeted builds for specific microarchitectures
* Minimal Android interface to native backend

---

## Features

* ARM-optimized `ccminer` backend with microarchitecture-specific tweaks
* Statically linked toolchain and dependencies
* URL-based config support: `yaccfe://config?...`
* No root required (may be restricted on newer Android versions)
* No Google Services or similar dependencies

---

## Install

Download the APK:
[https://github.com/arlsson//yaccfe/releases](https://github.com/arlsson//yaccfe/releases)

---

## Supported Architectures

Supports over 50 ARMv8+ microarchitectures, including:

* Cortex-A53/A55/A57/A72/A73/A75/A76/A78/A710/A715/A720
* Cortex-X1/X2/X3/X4
* Neoverse N1/N2/V1/V2
* Ampere Altra, AmpereOne
* Qualcomm Falkor, Kryo
* ThunderX, ThunderX2, ThunderX3
* HiSilicon Kunpeng
* Samsung Exynos M3–M5
* NVIDIA Carmel
* ...and more

---

## Technical Notes

* Based on: `ccminer Verushash2.2 v3.8.3`
* Changes include:

  * Custom API interface
  * Patched stratum protocol
  * Static linking for embedded deployment
* CPU-only (no GPU backend)
* No thermal or throttling management
* No background scheduling hooks

---

## Limitations

* No GUI config — one static config per install
* Only supports one `-o` pool/URL (use your own proxy if needed)
* CPU-only; GPU not supported

---

## Tested On

* Android 9

  * Cortex-A53
* Android 10

  * Cortex-A76

---

## Supported URI Schema

`yaccfe://config?...` — the app accepts configuration via URI with the following parameters:

| Parameter | Description                   | Example Value                            |
| --------- | ----------------------------- | ---------------------------------------- |
| `algo`    | Algorithm to use              | `verus`                                  |
| `url`     | Connection endpoint           | `stratum+tcp://verusproxy.iron.int:9004` |
| `user`    | Worker/user identifier        | `default.autobalance`                    |
| `threads` | Number of threads to allocate | `8`                                      |

---

### Example URI

```
yaccfe://config?algo=verus&url=stratum+tcp://verusproxy.iron.int:9004&user=default.autobalance&threads=8
```

Paste or scan this URI to launch the app with predefined settings.

Or via ADB:

```bash
adb shell am start -W -a android.intent.action.VIEW \
  -d "yaccfe://config?algo=verus\&url=stratum+tcp://verusproxy.iron.int:9004\&user=default.autobalance\&threads=8" \
  se.mittmoln.yaccfe
```

---

## Release

Still a proof of concept — not all ideas are fully explored.


---

## Roadmap

* Improve microarchitecture-specific optimizations
* Add temperature monitoring logic
* Reduce APK size

---

## Legal & Ethical

Use at your own risk. You’re running mining software — act responsibly.

**Not a lawyer. Not your legal guardian. Don't be stupid.**
