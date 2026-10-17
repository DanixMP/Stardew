<h1 align="center">Stardew</h1>

<p align="center">
  <b>Motion graphics and visual effects: an open-source alternative to Adobe After Effects, written in pure Rust.</b>
</p>

<p align="center">
  Compositions, layers, keyframes, 300+ effects, layer styles, expressions, 3D cameras and lights,
  and a render queue. Native on macOS, Windows and Linux, and in the browser.
</p>

<p align="center">
  <img alt="Status: alpha" src="https://img.shields.io/badge/status-alpha-6b4fd8?style=flat-square">
  <img alt="Written in Rust" src="https://img.shields.io/badge/rust-1.95%2B-b7410e?style=flat-square&logo=rust&logoColor=white">
  <img alt="License: MIT OR Apache-2.0" src="https://img.shields.io/badge/license-MIT%20%2F%20Apache--2.0-555?style=flat-square">
</p>

> [!NOTE]
> Stardew is a fork of [EffectCraft](https://github.com/storytold/effectcraft) by the ArtCraft
> team and community. It's an independent project and isn't made, sponsored or endorsed by the
> ArtCraft team. We build on their work and send fixes upstream where we can.

## What Stardew is

Stardew is for animated titles, motion graphics and compositing: the work people usually open
After Effects for. You build a composition out of layers (solids, shapes, text, footage, other
compositions), animate their properties with keyframes, stack effects on them and render the result.

The panels, menus, shortcuts and keyframe behaviour follow After Effects, so your muscle memory
carries over: Project, Composition, Timeline, Effect Controls, Effects & Presets, Character,
Paragraph, Align, Preview, Audio and the Render Queue.

- **Layers of every kind:** solids, shapes, text, footage, nested compositions, nulls, adjustment
  layers, cameras and lights; parenting, track mattes, 38 blend modes, motion blur.
- **Keyframes:** linear, Bezier, hold, auto and continuous Bezier, roving keys, Easy Ease, and a
  Graph Editor with value and speed graphs.
- **Effects:** 306 effects across blur, color correction, distort, generate, keying, simulation
  (particles, shatter, caustics), stylize, time, audio and more, plus all nine Layer Styles.
- **Expressions:** JavaScript with the After Effects object model (`wiggle`, `loopOut`,
  `thisComp.layer("…")`), an inline editor and the pick-whip.
- **3D:** 3D layers, one- and two-node cameras with depth of field, lights with soft shadows.
- **Export:** H.264, ProRes, HEVC, AV1, WebM (VP9/AV1), image sequences (PNG, JPEG, TIFF, EXR),
  GIF and audio; all encoders are pure Rust, with no FFmpeg inside.
- **Lottie** import and export built in.
- **Readable projects:** versioned JSON (`.ecproj`) that diffs cleanly in version control.
- **Scriptable:** every action is a command with an id, reachable from the command line, a JSON
  control channel and an MCP server for agents ([docs/agents.md](docs/agents.md)).

## Get started

You need [Rust](https://rustup.rs/) 1.95 or newer.

```sh
git clone https://github.com/DanixMP/Stardew
cd Stardew
cargo run --release -p effectcraft          # the app (add `-- --demo` to open the demo project)
cargo run --release -p effectcraft-cli -- render --out intro.mp4    # render the demo headless
cargo xtask web --serve 8765                # the browser build on http://127.0.0.1:8765/
```

The crates and binaries keep their upstream `effectcraft` names for now, which keeps merging
improvements from EffectCraft simple.

To work on it: `cargo test --workspace`, and `cargo xtask ci` before every commit (format, lints,
tests, layering, asset attribution and the WebAssembly build). See [CONTRIBUTING.md](CONTRIBUTING.md),
[docs/architecture.md](docs/architecture.md) and [docs/testing.md](docs/testing.md).

## Where it stands

Stardew is **alpha**. Nearly every After Effects feature exists, but existing isn't the same as
behaving exactly like After Effects. What we're working on first:

1. **Stability:** crash fixes and the basic interaction bugs on Linux and Windows.
2. **Opening After Effects projects:** `.aep` / `.aepx` import, the biggest gap today.
3. **Performance:** preview and render speed on real-world compositions.
4. **More effects and systems.**

[docs/gaps.md](docs/gaps.md) lists every known shortfall inherited from upstream, and
[ROADMAP.md](ROADMAP.md) the plan. [Bug reports](https://github.com/DanixMP/Stardew/issues) are
the most useful thing you can send.

## How it's made

- **Engine first.** A stack of small crates with strict layering. The interface (egui) sits on
  top and nothing underneath depends on it.
- **Clean room.** We work from After Effects' public documentation and how it behaves, never
  from Adobe's files, icons, presets or code. No code is copied from GPL projects. The full rules
  are in [AGENTS.md](AGENTS.md).
- **Private by default.** No telemetry, and no network access unless you ask for it.

## License and credits

Stardew is dual-licensed under [MIT](LICENSE-MIT) or [Apache-2.0](LICENSE-APACHE), at your option,
like EffectCraft, which it's based on. Required notices are in [NOTICE](NOTICE). Bundled fonts,
icons and other assets keep their own open licenses; each one is listed in
[ATTRIBUTION.md](ATTRIBUTION.md).

<sub>Adobe and After Effects are trademarks or registered trademarks of Adobe Inc. in the United
States and/or other countries. ArtCraft and EffectCraft are names of the ArtCraft team's projects.
Stardew is an independent, open-source project and is not affiliated with, sponsored by or endorsed
by Adobe Inc. or the ArtCraft team; these names are used only to describe compatibility and origin.</sub>
