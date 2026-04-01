---
title: "Maintenance release: Godot 4.6.2"
excerpt: The second 4.6 maintenance release has arrived; no foolin'!
categories: [release]
author: Thaddeus Crews
image: /storage/blog/covers/maintenance-release-godot-4-6-2.jpg
image_caption_title: Bombun
image_caption_description: A game by Kekitopu
date: 2026-04-01 12:00:00
---

While the majority of our team continues to focus on development snapshots for [Godot 4.7](/article/dev-snapshot-godot-4-7-dev-3/), we still have a commitment to maintenance releases for the latest stable version. Specifically, our [release support policy](https://docs.godotengine.org/en/latest/about/release_policy.html#release-support-timeline) promises active support until the successor's first patch release, so there's still room for yet more maintenance releases in the future. As for now, we'd like to thank everyone who took the time to evaluate and ratify our release candidates for Godot 4.6.2.

Maintenance releases are expected to be safe for an upgrade, but we recommend to always make backups, or use a version control system such as Git, to preserve your projects in case of corruption or data loss.

Please consider [supporting the project financially](#support), if you are able. Godot is maintained by the efforts of volunteers and a small team of paid contributors. Your donations go towards sponsoring their work and ensuring they can dedicate their undivided attention to the needs of the project.

[**Download Godot 4.6.2 now**](/download/archive/4.6.2-stable/) or try the [online version of the Godot editor](https://editor.godotengine.org/4.6.2.stable/).

{% include articles/download_card.html version="4.6.2" release="stable" article=page %}

-----

*The cover illustration is from* [**Bombun**](https://store.steampowered.com/app/3609320/Bombun/?curator_clanid=41324400), *a wholesome 3D platformer where you guide Bombun, a bomb-throwing bunny, on a mission to defend her floating fortress from a friend-turned-foe. You can buy the game on [Steam](https://store.steampowered.com/app/3609320/Bombun/?curator_clanid=41324400), and follow the developer on [Bluesky](https://bsky.app/profile/kekitopu.bsky.social) or [itch.io](https://kekitopu.itch.io/).*

## Changes

**61 contributors** submitted **122 fixes** for this release. See our [**interactive changelog**](https://godotengine.github.io/godot-interactive-changelog/#4.6.2) for the complete list of changes since the [4.6.1-stable release](/article/maintenance-release-godot-4-6-1/).

- 3D: Fix 3D focus selection for subgizmos ([GH-116972](https://github.com/godotengine/godot/pull/116972)).
- 3D: Fix DirectionalLight3D property list ([GH-117189](https://github.com/godotengine/godot/pull/117189)).
- Animation: Check `playback_queue` existance after emit `animation_finished` signal ([GH-116676](https://github.com/godotengine/godot/pull/116676)).
- Animation: Deselect bezier keyframes when switching animations ([GH-116953](https://github.com/godotengine/godot/pull/116953)).
- Animation: Fix timeline cursor following mouse during marker selection ([GH-117634](https://github.com/godotengine/godot/pull/117634)).
- Animation: Fix visual shift of animation editor keys during selection ([GH-117290](https://github.com/godotengine/godot/pull/117290)).
- Core: Fix `String::split_` crash on empty string ([GH-117353](https://github.com/godotengine/godot/pull/117353)).
- Core: Fix editable children state when duplicating instantiated nodes ([GH-117041](https://github.com/godotengine/godot/pull/117041)).
- Core: RingBuffer: Fix `T read()` method reading empty buffer ([GH-117388](https://github.com/godotengine/godot/pull/117388)).
- Core: RingBuffer: Fix overreading on methods that take an offset as an argument ([GH-117151](https://github.com/godotengine/godot/pull/117151)).
- Editor: Fix build profile generator creating bogus profiles ([GH-115410](https://github.com/godotengine/godot/pull/115410)).
- Editor: Fix mute button after pausing and stopping ([GH-116537](https://github.com/godotengine/godot/pull/116537)).
- Editor: Fix theme item inspector tooltips for Window subclasses ([GH-115245](https://github.com/godotengine/godot/pull/115245)).
- Editor: Set accessibility name on Tree inline cell editor when editing ([GH-117135](https://github.com/godotengine/godot/pull/117135)).
- Editor: Stop autocomplete from eating words by default ([GH-117464](https://github.com/godotengine/godot/pull/117464)).
- Export: Android Editor: Copy keystore to temp file during export ([GH-116161](https://github.com/godotengine/godot/pull/116161)).
- GDExtension: Add missing `GDVIRTUAL_BIND(_get_supported_extensions)` on `MovieWriter` ([GH-117479](https://github.com/godotengine/godot/pull/117479)).
- GUI: Fix "Custom" anchor preset being ignored if the parent isn't a `Control` ([GH-117488](https://github.com/godotengine/godot/pull/117488)).
- GUI: Fix RichTextLabel drag selection not working after double-click ([GH-117201](https://github.com/godotengine/godot/pull/117201)).
- GUI: TextEdit: Fix clipping of last character due to right margin rounding ([GH-116850](https://github.com/godotengine/godot/pull/116850)).
- GUI: TextServer: Ignore language of embedded object replacement spans when updating line breaks ([GH-116197](https://github.com/godotengine/godot/pull/116197)).
- Import: Blender attempts should be incremented to avoid endless loop ([GH-116589](https://github.com/godotengine/godot/pull/116589)).
- Physics: Jolt Physics: Make MoveKinematic more accurate when rotating a body by a very small angle ([GH-115327](https://github.com/godotengine/godot/pull/115327)).
- Physics: Jolt Physics: Rework how gravity is applied to dynamic bodies to prevent energy increase on elastic collisions ([GH-115305](https://github.com/godotengine/godot/pull/115305)).
- Physics: Jolt Physics: Swapping vertices of triangle if it is scaled inside out ([GH-115089](https://github.com/godotengine/godot/pull/115089)).
- Platforms: Android: Fix FileAccess crash when using treeUri in Gradle-built apps ([GH-117131](https://github.com/godotengine/godot/pull/117131)).
- Platforms: Fix macOS Steam time tracking lost when opening a project ([GH-117335](https://github.com/godotengine/godot/pull/117335)).
- Platforms: iOS: Add UIScene lifecycle events ([GH-116395](https://github.com/godotengine/godot/pull/116395)).
- Platforms: iOS: Propagate VC UI preferences to SwiftUI hosting controller ([GH-116633](https://github.com/godotengine/godot/pull/116633)).
- Platforms: macOS: Enable wake for events if `Magnet` is running ([GH-116524](https://github.com/godotengine/godot/pull/116524)).
- Platforms: Wayland: Improve mapping robustness and synchronization ([GH-117385](https://github.com/godotengine/godot/pull/117385)).
- Platforms: Windows: Set current driver when ANGLE init fails ([GH-117253](https://github.com/godotengine/godot/pull/117253)).
- Rendering: Apply fixed size properly for mono/stereo rendering ([GH-115147](https://github.com/godotengine/godot/pull/115147)).
- Rendering: Fix accidental write-combined memory reads in canvas renderer ([GH-115757](https://github.com/godotengine/godot/pull/115757)).
- Rendering: Fix Tangent decoding detection when computing vertex skinning ([GH-117401](https://github.com/godotengine/godot/pull/117401)).
- Rendering: Fix viewport debanding not working with spatial scalers ([GH-114890](https://github.com/godotengine/godot/pull/114890)).
- Rendering: macOS: Force ANGLE (GL over Metal) when running in VM ([GH-117371](https://github.com/godotengine/godot/pull/117371)).

This release is built from commit [`001aa128b`](https://github.com/godotengine/godot/commit/001aa128b1cd80dc4e47e823c360bccf45ed6bad).

## Known incompatibilities

As of now, there are no known incompatibilities with the previous Godot 4.6.1 release. **We encourage all users to upgrade to 4.6.2.**

If you experience any unexpected behavior change in your projects after upgrading to 4.6.2, please [file an issue on GitHub](https://github.com/godotengine/godot/issues).

## Bug reports

As a tester, we encourage you to [open bug reports](https://github.com/godotengine/godot/issues) if you experience issues with this release. Please check the [existing issues on GitHub](https://github.com/godotengine/godot/issues) first, using the search function with relevant keywords, to ensure that the bug you experience is not already known.

In particular, any change that would cause a regression in your projects is very important to report (e.g. if something that worked fine in previous 4.x releases, but no longer works in this snapshot).

## Support

Godot is a non-profit, open-source game engine developed by hundreds of contributors on their free time, as well as a handful of part and full-time developers hired thanks to [generous donations from the Godot community](https://fund.godotengine.org/). A big thank you to everyone who has contributed [their time](https://github.com/godotengine/godot/blob/master/AUTHORS.md) or [their financial support](https://github.com/godotengine/godot/blob/master/DONORS.md) to the project!

If you'd like to support the project financially and help us secure our future hires, you can do so using the [Godot Development Fund](https://fund.godotengine.org/).

<a class="btn" href="https://fund.godotengine.org/">Donate now</a>
