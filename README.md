# Wiggle 2 — Blender 5.1 Compatible Fork

This is an unofficial, community-maintained fork of [Wiggle 2](https://github.com/shteeve3d/blender-wiggle-2) by **Steve Miller (shteeve3d)**, updated to work with **Blender 5.1**.

> **I do not own this addon.** All original credits belong to Steve Miller. This fork is provided strictly for personal, non-commercial use. No commercial use of this fork is permitted in any form.

---

## What's Changed from the Original

| Fix | Description |
|-----|-------------|
| Package structure | Renamed `wiggle_2.py` → `__init__.py` and added `blender_manifest.toml` required by Blender 4.2+ extension system |
| Handler signatures | Added `depsgraph=None` to all persistent handlers (`wiggle_pre`, `wiggle_post`, `wiggle_render_*`, `wiggle_load`) |
| `nla.bake` version check | Fixed logic so Blender 5.x correctly uses the `channel_types` argument |
| RNA property access | Replaced `b[prop]` dict syntax with `getattr`/`setattr` — required by Blender 4.x+ |
| Recursion fix | Added guard in `update_prop` to prevent RNA update callbacks from triggering each other infinitely |
| Parent hierarchy | `get_parent()` now verifies the parent bone is registered in `wiggle.list` before reading its matrix |
| Bone sort order | Bones are now sorted by depth (`bone_depth`) so parent bones are always evaluated before children |
| Constraint whitelist | Only orientation-driving constraints (IK, COPY_ROTATION, etc.) use the `matrix_basis` path — `LIMIT_ROTATION` and similar no longer break parent transform |
| Collision `collision_col` | Replaced `PointerProperty(type=Collection)` with `BoolProperty` — Blender 5.x forbids assigning embedded IDs to pointer properties |
| Scene scale | Gravity and wind forces are now multiplied by `scene.unit_settings.scale_length` so physics behave correctly regardless of rig size |

---

## Installation

1. Download the latest zip from [Releases](../../releases)
2. In Blender: **Edit → Preferences → Add-ons → Install from Disk**
3. Select the zip file and enable the addon

---

## Original Addon

- **Author:** Steve Miller
- **Repository:** https://github.com/shteeve3d/blender-wiggle-2
- **License:** GPL-3.0

Please support the original creator.

---

## Disclaimer

This fork is not affiliated with or endorsed by the original author. It is shared purely to help the community use the addon on newer versions of Blender. No ownership is claimed over the original work.
