---
title: "Dev snapshot: Godot 4.7 dev 4"
excerpt: Howdy, neighbor!
categories: [pre-release]
author: Thaddeus Crews
image: /storage/blog/covers/dev-snapshot-godot-4-7-dev-4.jpg
image_caption_title: Poke ALL Toads
image_caption_description: A game by SpaceMatra
date: 2026-04-09 12:00:00
---

As we edge ever closer to feature freeze, many of our contributors have been hard at work to get their highly-anticipated features in hopes of Godot 4.7 integration. Fortunately for them, we've managed to accomodate several of these proposals, and are excited to showcase them today! Your testing will be crucial to ensure that everything listed *stays* in scope for a 4.7 release, so be sure to give this latest build a spin after the highlights

Please consider [supporting the project financially](#support), if you are able. Godot is maintained by the efforts of volunteers and a small team of paid contributors. Your donations go towards sponsoring their work and ensuring they can dedicate their undivided attention to the needs of the project.

[Jump to the **Downloads** section](#downloads), and give it a spin right now, or continue reading to learn more about improvements in this release. You can also try the [**Web editor**](https://editor.godotengine.org/releases/4.7.dev4/), the [**XR editor**](https://www.meta.com/s/3yJ7i8kop), or the [**Android editor**](https://play.google.com/store/apps/details?id=org.godotengine.editor.v4) for this release. If you are interested in the latter, please request to join [our testing group](https://groups.google.com/g/godot-testers) to get access to pre-release builds.

---

*The cover illustration is from* [**Poke ALL Toads**](https://store.steampowered.com/app/2302320/Poke_ALL_Toads/?curator_clanid=41324400), *a puzzle game starring mischievous fairies on a queat to poke ALL toads. You can buy the game on [Steam](https://store.steampowered.com/app/2302320/Poke_ALL_Toads/?curator_clanid=41324400), and follow the developer on [Bluesky](https://bsky.app/profile/pokealltoads.bsky.social), [YouTube](https://www.youtube.com/@PokeALLToads), or [itch.io](https://itch.io/profile/la-fafafa).*

## Highlights

### Rendering: Add nearest-neighbor scaling

We're starting things out with one of the most anticipated integrations for our rendering system: nearest-neighbor scaling for 3D viewports. Over the course of nearly three years, [Hugo Locurcio](https://github.com/Calinou) has been refining [GH-79731](https://github.com/godotengine/godot/pull/79731) to ensure that 3D titles with pixel-art aesthetics or lower resolution scaling will still look crisp without any compromise to performance:

#### Bilinear

<img src="/storage/blog/dev-snapshot-godot-4-7-dev-4/rendering-comparison-bilinear.webp" alt="A sample scene with bilinear filtering, results are blurry"/>

#### Nearest (new behavior)

<img src="/storage/blog/dev-snapshot-godot-4-7-dev-4/rendering-comparison-nearest.webp" alt="A sample scene with nearest-neighbor filtering, results are crisp"/>

### GUI: Add `custom_maximum_size` property to `Control`

Our previous development snapshot had a large focus on GUI improvements, and that QOL continues with the new `custom_maximum_size` property for `Control`. [Enzo Novoselic](https://github.com/StarryWorm) in [GH-116640](https://github.com/godotengine/godot/pull/116640) has at last brought us the maximal equivalent to the existing `custom_minimum_size`, enabling the fine-tuning of GUI element sizes to their full potential.

### GUI: Improve drag and drop in `Tree`

[vaner](https://github.com/vaner-org) spear-headed [GH-112993](https://github.com/godotengine/godot/pull/112993) in order to improve the overall usability and intuitiveness of `Tree` drag-and-drop functionality. Now when performing a drag-and-drop operation, there will be an always-present vertical indicator showing the potential parental chain, leveraging a standalone `CanvasItem` to prevent StyleBox occlusion.

| Old                                                                                   | New                                                                                   |
| ------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------- |
| <img src="/storage/blog/dev-snapshot-godot-4-7-dev-4/tree-old.webp" alt="Original drag-and-drop behavior"/> | <img src="/storage/blog/dev-snapshot-godot-4-7-dev-4/tree-new.webp" alt="Updated drag-and-drop behavior"/> |

What's more, this operation will now consider the x-position of the cursor while determining a to-be parent when in indent space (leftmost, empty space), whereas item space largely retains current behavior. This implementation mirrors what one would commonly find in vector design software.

<video autoplay loop muted playsinline title="Showcase of new x-position logic in indent space of a sample tree">
  <source src="/storage/blog/dev-snapshot-godot-4-7-dev-4/tree-showcase.mp4?1" type="video/mp4">
</video>

### Editor: Increase available space for array properties

Have you ever wondered why the inspector takes up so much negative space when working with arrays? Turns out it wasn't done deliberately; it just so happened to be using the default offset of 0.5! [Tomasz Chabora](https://github.com/KoBeWi) rightfully found this quite silly, and whipped up [GH-118008](https://github.com/godotengine/godot/pull/118008) to rectify this oversight.

| Old                                                                                   | New                                                                                   |
| ------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------- |
| <img src="/storage/blog/dev-snapshot-godot-4-7-dev-4/inspector-array-old.webp" alt="Original inspector array display"/> | <img src="/storage/blog/dev-snapshot-godot-4-7-dev-4/inspector-array-new.webp" alt="Updated inspector array display"/> |

### And more!

There are too many exciting changes to list them all here, but here's a curated selection:

- 2D: Rework TileSet editor proxy objects ([GH-117574](https://github.com/godotengine/godot/pull/117574)).
- 3D: Add vector components to 3D ruler tool ([GH-106785](https://github.com/godotengine/godot/pull/106785)).
- Editor: Add folding to the Visual Profiler tree ([GH-118120](https://github.com/godotengine/godot/pull/118120)).
- Editor: Add type filters to create dialog ([GH-111518](https://github.com/godotengine/godot/pull/111518)).
- Editor: Hide renderer selector in main editor window and add editor setting ([GH-117754](https://github.com/godotengine/godot/pull/117754)).
- Editor: Make right-clicking on unfocused scene tabs possible ([GH-112919](https://github.com/godotengine/godot/pull/112919)).
- GDExtension: Allow viewing GDExtensions from inside project settings ([GH-118063](https://github.com/godotengine/godot/pull/118063)).
- GDScript: LSP: Calculate simple string insertions on the server-side ([GH-117710](https://github.com/godotengine/godot/pull/117710)).
- Particles: Fix angular velocity ([GH-117861](https://github.com/godotengine/godot/pull/117861)).
  - **NOTE:** This is technically compatibility-breaking, but it's bringing the functionality in-line with how its always been documented.
- Particles: Fix particles moving when timescale is 0 ([GH-109911](https://github.com/godotengine/godot/pull/109911)).
- Platforms: Android: Allow implementing java interfaces from GDScript ([GH-115498](https://github.com/godotengine/godot/pull/115498)).
- Platforms: Windows: Implement OneCore TTS support using C++/WinRT (no deps) ([GH-116349](https://github.com/godotengine/godot/pull/116349)).
- Platforms: Windows: Use OneCore/WinRT emoji picker when available ([GH-116351](https://github.com/godotengine/godot/pull/116351)).

## Changelog

**88 contributors** submitted **188 fixes** for this release. See our [**interactive changelog**](https://godotengine.github.io/godot-interactive-changelog/#4.7-dev4) for the complete list of changes since [4.7-dev3](/article/dev-snapshot-godot-4-7-dev-3/). You can also review [all changes included in 4.7](https://godotengine.github.io/godot-interactive-changelog/#4.7) compared to the previous [4.6 feature release](/releases/4.6/).

This release is built from commit [`755fa449c`](https://github.com/godotengine/godot/commit/755fa449c4aa94fdf2c58e2b726fd62efde07e09).

## Downloads

{% include articles/download_card.html version="4.7" release="dev4" article=page %}

**Standard build** includes support for GDScript and GDExtension.

**.NET build** (marked as `mono`) includes support for C#, as well as GDScript and GDExtension.

{% include articles/prerelease_notice.html %}

## Known issues

With every release we accept that there are going to be various issues, which have already been reported but haven't been fixed yet. See the GitHub issue tracker for a complete list of [known bugs](https://github.com/godotengine/godot/issues?q=is%3Aissue+is%3Aopen+label%3Abug).

There are currently no known issues introduced by this release.

## Bug reports

As a tester, we encourage you to [open bug reports](https://github.com/godotengine/godot/issues) if you experience issues with this release. Please check the [existing issues on GitHub](https://github.com/godotengine/godot/issues) first, using the search function with relevant keywords, to ensure that the bug you experience is not already known.

In particular, any change that would cause a regression in your projects is very important to report (e.g. if something that worked fine in previous 4.x releases, but no longer works in this snapshot).

## Support

Godot is a non-profit, open-source game engine developed by hundreds of contributors in their free time, as well as a handful of part and full-time developers hired thanks to [generous donations from the Godot community](https://fund.godotengine.org/). A big thank you to everyone who has contributed [their time](https://github.com/godotengine/godot/blob/master/AUTHORS.md) or [their financial support](https://github.com/godotengine/godot/blob/master/DONORS.md) to the project!

If you'd like to support the project financially and help us secure our future hires, you can do so using the [Godot Development Fund](https://fund.godotengine.org/) platform managed by the [Godot Foundation](https://godot.foundation/). There are also several [alternative ways to donate](/donate) which you may find more suitable.

<a class="btn" href="https://fund.godotengine.org/">Donate now</a>
